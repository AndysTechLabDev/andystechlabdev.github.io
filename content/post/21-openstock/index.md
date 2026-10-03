---
title: Deploy a Self-Hosted Stock Dashboard with Docker
date: 2026-10-02
publishDate: 2026-10-02T18:30:00+02:00
draft: false
showAuthor: false
showReadingTime: false
showWordCount: false
toc: true
tags:
  - docker
  - self-hosting
  - homelab
  - Linux
image: featured.webp

---
{{< youtube id="mInqgYY00gY" label="Deploy a Self-Hosted Stock Dashboard with Docker" >}}

## Overview
OpenStock is an open-source stock market dashboard that can be self-hosted on your own server.

It provides features such as stock search, watchlists, charts, company information, financial data, market news and general market overviews. It is not intended to replace a professional trading platform, portfolio accounting tool or brokerage service, but it covers many of the features that are useful for casually monitoring stocks.

The application uses external services for market data. In this setup, a free Finnhub API key is used, while MongoDB stores the application's local data.

OpenStock can be deployed with Docker Compose, but unlike many self-hosted applications it does not rely on a pre-built OpenStock image. The Docker image is built locally from the source code after cloning the GitHub repository.

The basic setup therefore consists of:
- Docker Compose
- Environment variables for application configuration
- OpenStock
- MongoDB
- Finnhub API access

Optional services such as Gemini can also be configured for additional automation features, but they are not required for the core stock dashboard.
___
## Commands
Clone the repo from Github:
```
git clone https://github.com/Open-Dev-Society/OpenStock.git  
```

Build the image and start the containers:
```
docker compose up -d mongodb && docker compose up -d --build
```
___
## docker-compose.yml
```
services:
  openstock:
    build:
      context: .
      extra_hosts:
        - "mongodb:host-gateway"
	container_name: openstock
    ports:
      - "3000:3000"
    env_file:
      - .env
    restart: unless-stopped
    depends_on:
      - mongodb

  mongodb:
    image: mongo:7
    container_name: openstock_mongodb
    restart: unless-stopped
    environment:
      MONGO_INITDB_ROOT_USERNAME: root
      MONGO_INITDB_ROOT_PASSWORD: example
    ports:
      - "27017:27017"
    volumes:
      - ./mongo-data:/data/db
    healthcheck:
      test: ["CMD", "mongosh", "--eval", "db.adminCommand('ping')"]
      interval: 10s
      timeout: 5s
      retries: 5
```
___
## Sources
* [Github OpenStock](https://github.com/Open-Dev-Society/OpenStock)  
* [Finnhub](https://finnhub.io/)  
___
## Support me!
You like the content and want to support me? [Buy me some ABS!](https://ko-fi.com/andystechlab)  
Or buy something with my [affiliate links](https://andystechlab.dev/product-links/) with no exra cost!  

**Some of the stuff i use:**\
PLA Filament: [Amazon](https://amzn.to/3Vauu4n) *  
ABS Filament: [Amazon](https://amzn.to/4lzb316) *  
Filament Dryer: [Amazon](https://amzn.to/42NVXxg) *  

*This link is an affiliate link, which means I may earn a commission at no extra cost to you.
