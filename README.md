# API_GATEWAY

## Overview

API_GATEWAY is a Node.js-based service designed to manage and route API requests to the appropriate backend services. It supports features such as rate limiting, logging, and proxying requests to multiple backend services. The service utilizes Express for server-side operations, `http-proxy-middleware` for request proxying, and `express-rate-limit` for handling request rate limits.

## Features

- **Request Routing**: Routes incoming API requests to the appropriate backend services.
- **Rate Limiting**: Protects backend services from being overwhelmed by limiting the number of requests.
- **Logging**: Provides detailed logs for monitoring and debugging purposes.
- **Proxy Middleware**: Uses `http-proxy-middleware` to forward API requests to backend servers.

## Table of Contents

- [Installation](#installation)
- [Configuration](#configuration)
- [Running the Application](#running-the-application)
- [API Endpoints](#api-endpoints)
- [Project Structure](#project-structure)
- [Contributing](#contributing)

## Installation

To install and set up the project locally, follow these steps:

1. **Clone the repository**:
   ```bash
   git clone https://github.com/yourusername/API_GATEWAY.git
   cd API_GATEWAY
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

## Configuration

Create a `.env` file in the root directory of the project to store environment variables. Here is an example of what the `.env` file might include:

```env
PORT=3000
TARGET_SERVER_URL=http://localhost:8000
RATE_LIMIT_WINDOW_MS=60000
RATE_LIMIT_MAX=100
```

Replace the placeholders with your actual target server URL and desired rate limit settings.

## Running the Application

To start the server, use the following command:

```bash
npm start
```

The server will start on the port specified in the `.env` file (default is 3000). The API Gateway can then be accessed at `http://localhost:3000`.

## API Endpoints

Here is a list of the main API endpoints:

### **Proxy Endpoints**

- **GET `/api/v1/resource`**
  - Proxies the request to the backend server specified in the `TARGET_SERVER_URL`.
  - **Headers**:
    ```json
    {
      "Authorization": "Bearer <JWT_TOKEN>"
    }
    ```

- **POST `/api/v1/resource`**
  - Proxies a POST request to the backend server.
  - **Request Body**:
    ```json
    {
      "key": "value"
    }
    ```

## Project Structure

Here's a high-level overview of the project's structure:

```
API_GATEWAY/
├── src/
│   ├── config/
│   │   └── serverConfig.js           # Server configuration
│   ├── middlewares/
│   │   ├── rate-limiter.js           # Rate limiting middleware
│   │   ├── logger.js                 # Logging middleware
│   │   └── proxy.js                  # Proxy middleware
│   ├── routes/
│   │   ├── index.js                  # Main routing file
│   │   └── v1/                       # Version 1 API routes
│   │       └── index.js
│   ├── utils/
│   │   └── error-handler.js          # Central error handling
│   └── index.js                      # Entry point of the application
├── .gitignore                        # Git ignore file
├── README.md                         # Project documentation
├── package.json                      # Node.js dependencies and scripts
└── package-lock.json                 # Dependency lock file
```

## Contributing

Contributions are welcome! If you have any suggestions or improvements, feel free to open an issue or submit a pull request.

### Steps to Contribute

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes and commit them (`git commit -m 'Add some feature'`).
4. Push to the branch (`git push origin feature-branch`).
5. Open a pull request.
