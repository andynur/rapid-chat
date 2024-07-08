# Rapid Chat

This is a full-stack project built with NestJS, NextJS, MongoDB, Redis Pub-Sub and Nx Workspaces. The application includes user authentication, profile management, and a chat system.

## Table of Contents

- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Setup](#setup)
- [Scripts](#scripts)
- [Migrations](#migrations)
- [Seeding](#seeding)
- [Environment Variables](#environment-variables)
- [Deployment](#deployment)
- [License](#license)

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

## Project Structure

```
rapid-chat/
├── apps/
│   └── api/
│       ├── src/
│       │   ├── app/
│       │   ├── auth/
│       │   ├── chat/
│       │   ├── user/
│       │   └── profile/
│       ├── assets/
│       ├── environments/
│       ├── tsconfig.app.json
│       ├── tsconfig.json
│       ├── jest.config.js
│       └── project.json
├── tools/
│   ├── config/
│   │   └── mongoose.ts
│   ├── database/
│   │   ├── migrations/
│   │   │   ├── 20230706-create-users.ts
│   │   │   ├── 20230707-create-chats.ts
│   │   │   └── 20230708-create-profiles.ts
│   │   ├── seeders/
│   │   │   ├── seed-users.ts
│   │   │   ├── seed-chats.ts
│   │   │   └── seed-profiles.ts
├── nx.json
├── package.json
├── tsconfig.base.json
├── workspace.json
├── nest-cli.json
└── docker-compose.yml
```

## Setup

### Prerequisites

- Node.js v20.x LTS
- Yarn
- Docker
- Docker Compose

### Installing

1. Clone the repository:

    ```bash
    git clone https://github.com/andynur/rapid-chat.git
    cd rapid-chat
    ```

2. Install dependencies:

    ```bash
    yarn install
    ```

3. Set up environment variables. Create a `.env` file in the root directory and add the following:

    ```env
    NODE_ENV=development
    PORT=3000
    MONGO_URI=mongodb://mongo:27017/rapid-chat
    REDIS_URI=redis://redis:6379
    JWT_SECRET=supersecretkey
    ```

## Scripts

### Running the Application

To start the application in development mode:

```bash
yarn start:dev
```

To build the application:

```bash
yarn build
```

To start the application in production mode:

```bash
yarn start:prod
```

### Running Tests

To run unit tests:

```bash
yarn test
```

To run tests in watch mode:

```bash
yarn test:watch
```

To run end-to-end tests:

```bash
yarn test:e2e
```

### Linting

To lint the code:

```bash
yarn lint
```

### Formatting

To format the code:

```bash
yarn format
```

## Migrations

### Running Migrations

To run migrations for creating collections:

```bash
yarn migrate up
```

### Rolling Back Migrations

To rollback migrations for collections:

```bash
yarn migrate down
```

## Seeding

### Running Seeders

To seed the database with initial data:

```bash
yarn seed
```

## Environment Variables

The following environment variables need to be set in a `.env` file in the root directory:

```env
NODE_ENV=development
PORT=3000
MONGO_URI=mongodb://mongo:27017/rapid-chat
REDIS_URI=redis://redis:6379
JWT_SECRET=supersecretkey
```

## Deployment

### Docker

To build and run the application using Docker Compose:

```bash
docker-compose up --build
```

### Railway

To deploy the application to Railway, ensure you have the following configuration in your `nixpacks.toml` file:

```toml
[phases.build]
run = "yarn install && yarn build"

[phases.start]
run = "node dist/apps/api/main.js"

[environment]
NODE_ENV = "production"
PORT = "3000"
MONGO_URI = "mongodb://mongo:27017/rapid-chat"
REDIS_URI = "redis://redis:6379"
JWT_SECRET = "supersecretkey"
```

Then follow the deployment steps provided by Railway.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
