---
title: Build a Blog for FREE in 2026
date: 2026-08-13
draft: false
showAuthor: false
showReadingTime: false
showWordCount: false
toc: true
tags:
  - hugo
image: featured.webp

---
{{< youtube id="McWyLdE2cKU" label="title: Build a Blog for FREE in 2026" >}}

## Overview
Learn how to build and deploy a completely free blog using Hugo, GitHub, GitHub Actions, and GitHub Pages.

In this step-by-step tutorial, I'll show you the complete workflow — from creating a fast static website with the Hugo Static Site Generator to pushing the project to a GitHub repository and automatically deploying it with GitHub Actions.

Finally, we'll host the website using GitHub Pages — with zero hosting costs.

This setup is perfect for developers, personal blogs, portfolios, documentation websites, and anyone who wants a fast and lightweight website without paying for hosting.

## Sources
Hugo Installation: [gohugo.io](https://gohugo.io/installation/)  
Hugo Themes: [gohugo.io](https://themes.gohugo.io/)  
PaperMod Installation Guide: [adityatelange.github.io](https://adityatelange.github.io/hugo-PaperMod/posts/papermod/papermod-installation/)  

## Python Script
Take a look and adapt as needed.

````python
from pathlib import Path
import re
import shutil
import unicodedata
import filecmp
import traceback

try:
    from PIL import Image, ImageOps
except ImportError as exc:
    raise SystemExit(
        "Pillow is not installed. Please run this once:\n"
        "  py -m pip install Pillow"
    ) from exc

OBSIDIAN_NOTES = Path(r"C:\opencloud\Personal\vault\website")
OBSIDIAN_ATTACHMENTS = Path(r"C:\opencloud\Personal\vault\attachements")
HUGO_POSTS = Path(r"C:\opencloud\Personal\hugo\content\post")

WEBP_MAX_WIDTH = 2400
WEBP_QUALITY = 82
WEBP_METHOD = 6

THUMBNAIL_RE = re.compile(r"^\s*THUMBNAIL:\s*!\[\[(.+?)\]\]\s*$", re.MULTILINE)
IMAGE_RE = re.compile(r"!\[\[(.+?)\]\]")
DRAFT_RE = re.compile(r"^\s*draft:\s*true\s*$", re.MULTILINE | re.IGNORECASE)

YOUTUBE_RE = re.compile(
    r'\{\{<\s*(?:youtubeLite|youtube)\s+id="(?P<id>[^"]+)"\s+label="(?P<label>[^"]*)"\s*>\}\}',
    re.IGNORECASE
)

URL_RE = re.compile(r"https?://")

FRONT_MATTER_YAML_RE = re.compile(r"^---\n(?P<body>.*?)\n---\n?", re.DOTALL)
FRONT_MATTER_TOML_RE = re.compile(r"^\+\+\+\n(?P<body>.*?)\n\+\+\+\n?", re.DOTALL)

def log(message: str):
    print(message)

def slugify(text: str) -> str:
    text = unicodedata.normalize("NFKD", text)
    text = text.encode("ascii", "ignore").decode("ascii")
    text = text.lower()
    text = re.sub(r"[^a-z0-9]+", "-", text)
    return text.strip("-")

def is_template_note(note_path: Path) -> bool:
    return note_path.stem.lower().startswith("00_")

def is_draft(content: str) -> bool:
    return DRAFT_RE.search(content) is not None

def extract_youtube_id(raw: str) -> str:
    raw = raw.strip()

    if re.fullmatch(r"[A-Za-z0-9_-]{11}", raw):
        return raw

    m = re.search(
        r"\[([A-Za-z0-9_-]{11})\]\((?:https?://)?(?:www\.)?(?:youtu\.be/|youtube\.com/watch\?v=)[^)]+\)",
        raw,
        re.IGNORECASE,
    )
    if m:
        return m.group(1)

    m = re.search(r"(?:v=|youtu\.be/)([A-Za-z0-9_-]{11})", raw, re.IGNORECASE)
    if m:
        return m.group(1)

    m = re.search(r"[A-Za-z0-9_-]{11}", raw)
    if m:
        return m.group(0)

    raise ValueError(f"No valid YouTube ID found: {raw!r}")

def fix_youtube_shortcodes(content: str) -> str:
    def repl(match):
        raw_id = match.group("id")
        label = match.group("label").replace('"', "'")
        video_id = extract_youtube_id(raw_id)
        return f'{{{{< youtube id="{video_id}" label="{label}" >}}}}'

    return YOUTUBE_RE.sub(repl, content)

def set_front_matter_image(content: str, image_value: str = "featured.webp") -> str:

    yaml_match = FRONT_MATTER_YAML_RE.match(content)
    if yaml_match:
        body = yaml_match.group("body")

        if re.search(r"(?m)^\s*image\s*:", body):
            body = re.sub(
                r"(?m)^\s*image\s*:\s*.*$",
                f"image: {image_value}",
                body,
                count=1,
            )
        else:
            body = body.rstrip() + f"\nimage: {image_value}\n"

        remainder = content[yaml_match.end():]
        return f"---\n{body}\n---\n{remainder.lstrip(chr(10))}"

    toml_match = FRONT_MATTER_TOML_RE.match(content)
    if toml_match:
        body = toml_match.group("body")

        if re.search(r"(?m)^\s*image\s*=", body):
            body = re.sub(
                r"(?m)^\s*image\s*=\s*.*$",
                f'image = "{image_value}"',
                body,
                count=1,
            )
        else:
            body = body.rstrip() + f'\nimage = "{image_value}"\n'

        remainder = content[toml_match.end():]
        return f"+++\n{body}\n+++\n{remainder.lstrip(chr(10))}"

    log("  -> WARNING: No front matter found; 'image' could not be set.")
    return content

def preserve_url_line_breaks(content: str) -> str:
    lines = content.splitlines()
    result = []

    for line in lines:
        if URL_RE.search(line) and not line.rstrip().endswith("  "):
            result.append(line.rstrip() + "  ")
        else:
            result.append(line)

    return "\n".join(result) + "\n"

def find_attachment(filename: str) -> Path:
    matches = list(OBSIDIAN_ATTACHMENTS.rglob(filename))
    if not matches:
        raise FileNotFoundError(f"Attachment not found: {filename}")
    return matches[0]

def copy_if_changed(src: Path, dest: Path) -> bool:
    if dest.exists() and filecmp.cmp(src, dest, shallow=False):
        log(f"    Unchanged: {dest.name}")
        return False

    shutil.copy2(src, dest)
    log(f"    Copied: {src.name} -> {dest.name}")
    return True

def convert_to_webp_if_changed(src: Path, dest: Path) -> bool:

    temp_dest = dest.with_name(f".{dest.stem}.tmp.webp")

    try:
        with Image.open(src) as image:
            image = ImageOps.exif_transpose(image)

            if image.width > WEBP_MAX_WIDTH:
                new_height = round(image.height * WEBP_MAX_WIDTH / image.width)
                image = image.resize(
                    (WEBP_MAX_WIDTH, new_height),
                    Image.Resampling.LANCZOS,
                )

            has_transparency = (
                image.mode in {"RGBA", "LA"}
                or (image.mode == "P" and "transparency" in image.info)
            )
            image = image.convert("RGBA" if has_transparency else "RGB")

            image.save(
                temp_dest,
                format="WEBP",
                quality=WEBP_QUALITY,
                method=WEBP_METHOD,
                optimize=True,
            )

        if dest.exists() and filecmp.cmp(temp_dest, dest, shallow=False):
            temp_dest.unlink()
            log(f"    Unchanged: {dest.name}")
            return False

        temp_dest.replace(dest)
        log(
            f"    Converted: {src.name} -> {dest.name} "
            f"(max. {WEBP_MAX_WIDTH}px, quality {WEBP_QUALITY})"
        )
        return True

    finally:
        if temp_dest.exists():
            temp_dest.unlink()

def remove_old_featured_jpg(post_dir: Path):

    old_featured = post_dir / "featured.jpg"
    if (post_dir / "featured.webp").exists() and old_featured.exists():
        old_featured.unlink()
        log("    Removed: featured.jpg")

def write_if_changed(dest: Path, content: str) -> bool:
    if dest.exists() and dest.read_text(encoding="utf-8") == content:
        log(f"    Unchanged: {dest.name}")
        return False

    dest.write_text(content, encoding="utf-8")
    log(f"    Written: {dest.name}")
    return True

def convert_note(note_path: Path) -> bool:
    log(f"\nProcessing: {note_path}")

    content = note_path.read_text(encoding="utf-8")
    content = fix_youtube_shortcodes(content)

    if is_template_note(note_path):
        log("  -> Skipped (template)")
        return False

    if is_draft(content):
        log("  -> Skipped (draft)")
        return False

    slug = slugify(note_path.stem)
    post_dir = HUGO_POSTS / slug
    log(f"  -> Slug: {slug}")
    log(f"  -> Target: {post_dir}")

    post_dir.mkdir(parents=True, exist_ok=True)

    thumb_match = THUMBNAIL_RE.search(content)
    if thumb_match:
        thumb_raw = thumb_match.group(1).strip()
        thumb_name = thumb_raw.split("|")[0].strip()

        log(f"  -> Thumbnail found: {thumb_name}")

        thumb_src = find_attachment(thumb_name)
        convert_to_webp_if_changed(thumb_src, post_dir / "featured.webp")
        remove_old_featured_jpg(post_dir)

        content = THUMBNAIL_RE.sub("", content).strip() + "\n"
        content = set_front_matter_image(content, "featured.webp")
    else:
        log("  -> No thumbnail found")

    def replace_image(match):
        raw = match.group(1).strip()

        parts = raw.split("|")
        image_name = parts[0].strip()
        size = parts[1].strip() if len(parts) > 1 else ""

        log(f"  -> Image found: {image_name}")

        src = find_attachment(image_name)

        safe_name = slugify(src.stem) + src.suffix.lower()
        dest = post_dir / safe_name

        copy_if_changed(src, dest)

        if size:
            width = size.split("x")[0].strip()
            if width.isdigit():
                return (
                    f'<img src="{safe_name}" '
                    f'style="width: {width}px; max-width: 100%; height: auto;" '
                    f'alt="">'
                )

        return (
            f'<img src="{safe_name}" '
            f'style="width: 100%; max-width: 100%; height: auto;" '
            f'alt="">'
        )

    content = IMAGE_RE.sub(replace_image, content)
    content = preserve_url_line_breaks(content)

    write_if_changed(post_dir / "index.md", content)
    log(f"  -> Exported: {note_path.name}")
    return True

def main():
    log(f"Notes folder: {OBSIDIAN_NOTES}")
    log(f"Attachments folder: {OBSIDIAN_ATTACHMENTS}")
    log(f"Hugo posts folder: {HUGO_POSTS}")
    log(
        f"WebP: max. {WEBP_MAX_WIDTH}px width, "
        f"quality {WEBP_QUALITY}, method {WEBP_METHOD}"
    )

    if not OBSIDIAN_NOTES.exists():
        log("ERROR: OBSIDIAN_NOTES does not exist.")
        input("\nPress Enter to exit...")
        return

    notes = list(OBSIDIAN_NOTES.rglob("*.md"))
    log(f"Markdown files found: {len(notes)}")

    if not notes:
        log("ERROR: No .md files found.")
        input("\nPress Enter to exit...")
        return

    processed = 0
    skipped = 0
    errors = 0

    for note in notes:
        try:
            changed = convert_note(note)
            if changed:
                processed += 1
            else:
                skipped += 1
        except Exception as e:
            errors += 1
            log(f"\nERROR in file: {note}")
            log(f"  {e}")
            log("  Traceback:")
            traceback.print_exc()

    log("\nSummary")
    log(f"  Processed: {processed}")
    log(f"  Skipped: {skipped}")
    log(f"  Errors: {errors}")

    input("\nPress Enter to exit...")

if __name__ == "__main__":
    main()
````

## Support me!
You like the content and want to support me? [Buy me some ABS!](https://ko-fi.com/andystechlab)  

**Some of the stuff i use:**
PLA Filament: [Amazon](https://amzn.to/3Vauu4n) *  
ABS Filament: [Amazon](https://amzn.to/4lzb316) *  
Filament Dryer: [Amazon](https://amzn.to/42NVXxg) *  

*This link is an affiliate link, which means I may earn a commission at no extra cost to you.
