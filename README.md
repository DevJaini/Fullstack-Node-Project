# Fullstack Node Project

A full-stack web application built with **Node.js**, **Express**, **Sequelize**, and **EJS** server-rendered views, organized in a layered architecture with validation, centralized error handling, and logging.

## Tech Stack

- Node.js, Express.js
- Sequelize ORM with MySQL `mysql2`
- EJS for server-side rendered views
- Joi with `express-joi-validation` for request validation
- Helmet, CORS, body-parser, cookie-parser
- dotenv for environment-specific configuration
- Winston for logging

## Project Structure

```
├── server.js            # App entry point (Express setup, middleware, DB sync)
├── public/              # Static assets
└── app/
    ├── controllers/     # Handle requests and responses
    ├── services/        # Business logic and integrations
    ├── models/          # Sequelize models and connection setup
    ├── routes/          # Route definitions (route.js)
    ├── validations/     # Joi request validation schemas
    ├── middlerwares/    # Response formatting and error handling
    ├── loggers/         # Winston logger configuration
    ├── utils/           # Shared utilities
    └── views/           # EJS templates
```

### How a request flows

`Route` → `Validation` → `Controller` → `Service` → `Model (Sequelize)` → Database

Responses pass through the response middleware, and Joi validation errors and other errors are handled by dedicated error-handling middleware.

## Getting Started

### Prerequisites

- Node.js v[18+]
- MySQL running locally or remotely
- npm or yarn

### Installation

```bash
git clone https://github.com/DevJaini/Fullstack-Node-Project.git
cd Fullstack-Node-Project
npm install
```

### Environment Variables

The app loads `.env.<NODE_ENV>` when `NODE_ENV` is set (for example `.env.development`), and `.env` otherwise.

```env
PORT=3001

DB_HOST=localhost
DB_USER=your_user
DB_PASSWORD=your_password
DB_NAME=your_database

JWT_SECRET=your_secret
```

Adjust these names to match what your database config and services read. Do not commit real credentials.

### Database

Create an empty MySQL database. On startup the app runs `sequelize.sync()`, which creates any missing tables from the models in `app/models/`.

### Run the App

```bash
npm start
# or, during development
npm run dev
```

The server listens on `PORT`, defaulting to `3001`.

## Features

- Server-rendered pages with EJS
- Request validation with custom Joi error messages
- Centralized response and error handling middleware
- Secure HTTP headers with Helmet, CORS enabled
- JSON and form body parsing (up to 50 MB) and cookie support
- Static file serving from `public/`
- Logging with Winston

## Contributing

1. Fork the repo
2. Create a branch: `git checkout -b feature/your-feature`
3. Commit your changes
4. Open a pull request

## Author

**Jaini Shah** — [GitHub](https://github.com/DevJaini)
