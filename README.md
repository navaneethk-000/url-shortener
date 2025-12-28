# URL Shortener with Analytics

A simple URL shortener that lets you shorten links, track clicks, see where visitors came from, and generate QR codes.

## Features

- Shorten URLs
- Custom aliases (e.g., http://sho.rt/my-link)
- Click tracking
- Referrer stats (e.g., http://sho.rt/32da?ref=google.com)
- QR code generation
- user authentication

## Tech Stack

- **Backend:** Golang (Gin Framework), GORM, PostgreSQL
- **Frontend:** Nuxt 3, Tailwind CSS
- **Infrastructure:** Docker, Docker Compose, Nginx (Reverse Proxy)

The source code for the frontend and backend lives in separate submodules.

[Frontend-repo](https://github.com/navaneethk-000/url-shortener-frontend)

[Backend-repo](https://github.com/navaneethk-000/url-shortener-backend)
