<img src="https://raw.githubusercontent.com/cmsax/linka/main/public/logo192.png" width="150">

# Linka!

A smooth bookmarks management web app, shipped with special optimization for quick-search & quick-open, which will boost your productivity.

Currently it supports `linkding`, we are planning to make `Linka` a more flexible app to support other popular backends.

## Features

- full text search
- multi keywords, substract keywords support
- instantly open search results
- search on type
- dark/light mode
- hotkeys

## Demo

![demo](./screenshot/demo.gif)

[Linka! demo web app](https://linka.unoiou.com)

- `demo linkding base url`: https://link.unoiou.com
- `demo token`(restricted): `a6816f654f87197545cd66bfd2f8e294c40f1ee4`

## How-To use

- type any keywords, seperated by space, results will be **intersection**
- use keywords start with `!` to **exclude**
- type `Enter` to open search results in new tabs

### Hotkeys

- `cmd+l` or `ctrl+l` to focus on the search box

## Development Guid

### Prerequisite

Install `nodejs` and `yarn`.

### Start a local development app

Run `yarn install` & `yarn start` to start up.

### Build for production

#### Option 1: Deploy With Static HTTP Server (e.g. Nginx)

Run `yarn build` then publish the `./build` directory to a static http server like nginx, following is a demo nginx config part:

```config
# linka
server {
    listen 443 ssl http2;
    server_name linka.unoiou.com;
    index index.html;
    location / {
        root /home/ubuntu/static_sites/linka/build;
        try_files $uri $uri/ /index.html;
    }
}
```

#### Option 2: Deploy with Docker

Use pre build image:

```bash
docker pull cmsax/linka:latest
docker run --name my-own-linka -p 80:80 -d cmsax/linka:latest
```

Build on your own:

```bash
docker build -t my/linka:latest .
docker run --name my-own-linka -p 80:80 -d my/linka:latest
```

## `Linkding` Backend Prerequisite

- Enable `CORS` in backend by adding following headers to response:
  - `Access-Control-Allow-Origin: *`
  - `Access-Control-Allow-Methods: GET,POST,OPTIONS,PUT,DELETE`
  - `Access-Control-Allow-Headers: *`
  - `Access-Control-Max-Age: 1000000`
