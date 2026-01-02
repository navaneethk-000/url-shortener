# URL Shortener with Analytics

A high-performance URL shortener featuring user authentication, geo-location tracking, and advanced analytics. Built with a focus on **Clean Architecture**, **Concurrency**, and **Scalability**.

## Source Repositories

This project is an orchestrator using Git Submodules.

- **Frontend:** [url-shortener-frontend](https://github.com/navaneethk-000/url-shortener-frontend)
- **Backend:** [url-shortener-backend](https://github.com/navaneethk-000/url-shortener-backend)

### Core Functionality

- **URL Shortening:** High-speed mapping via Base62 encoding.
- **Custom Aliases:** User-defined short paths (e.g., `/my-link`).
- **QR Code Engine:** Customizable QR codes (Foreground/Background colors).

### Advanced Analytics

- **Geo-Location Tracking:** Background processing of visitor IP addresses to resolve Country and City.
- **Stepped Performance Graph:** Interactive growth charts using **Chart.js**.
- **Platform Detection:** Real-time logging of Browser, OS, and Referrer data.

### Security & Performance

- **JWT Authentication:** Stateless security with BCrypt password hashing.
- **Worker Pool Pattern:** Asynchronous background worker pool using Go Channels for non-blocking analytics processing.

## Tech Stack

- **Backend:** Golang (Gin Framework), GORM, PostgreSQL.
- **Frontend:** Nuxt 3, Pinia (State Management), Tailwind CSS.
- **DevOps:** Docker, Nginx, Docker Compose (Multi-stage Builds).

## How to Run

### Clone the Project

```bash
git clone --recursive https://github.com/navaneethk-000/url-shortener
cd url-shortener
```

## Configuration

To run this project, you need to set up environment variables.

1. Create a `.env` file in the root directory.
2. Copy the following template into your `.env` file:

```ini
# Database Configuration
DB_USER=user
DB_PASSWORD=password
DB_NAME=name
DB_HOST_PORT=5432

# Backend Configuration
JWT_SECRET=your_random_secret_string
BACKEND_PORT=8080

# IMPORTANT: If testing on a Local Network (LAN),
# replace 'localhost' with your Machine IP (e.g., 192.168.0.152)
BASE_URL=http://localhost:8080
FRONTEND_URL=http://localhost

# Frontend Configuration
FRONTEND_PORT=80
# This must point to the Backend API URL
NUXT_PUBLIC_API_BASE=http://localhost:8080
```

## Build & Run

Run the following command to build images and start the containers.

```bash
docker compose up --build
```

## How to Access the Website

Once the containers are running, you can access the project components as follows:

## USER DASHBOARD (FRONTEND)

• Open your browser and visit:
http://localhost

• If you used your LAN IP in `.env`, use:
http://<YOUR_IP>

## QR CODE TESTING

• Ensure your phone is connected to the SAME Wi-Fi network as your laptop
• Scan the QR code generated in the dashboard
• You will be redirected to the long URL via your local machine's IP

## Testing Geolocation

Since the project runs locally, the backend identifies all requests as `127.0.0.1` (localhost). To test if the Geo-Location tracking works for different countries, you can simulate a request from a specific IP using the `X-Forwarded-For` header.

**Example: Simulate a request from Japan (202.232.2.2)**

```bash
curl -v -H "X-Forwarded-For: 202.232.2.2" http://localhost:8080/shortcode
```
