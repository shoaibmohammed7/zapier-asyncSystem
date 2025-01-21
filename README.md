# Zapier Async System

Zapier Async System is a modular, event-driven system designed to handle triggers and actions asynchronously via a backend service, database integration, and GitHub hooks. The system is built to process events efficiently and ensure reliable data persistence.

---

## Architecture

The project follows a well-structured architecture that integrates multiple components for seamless asynchronous event handling. Here's a high-level overview of the system:

### Frontend (zapier.com FE)
- Allows users to create and configure triggers (e.g., "Create a Zap").
- Triggers initiate actions which are sent to the backend.

### Backend (zapier.com + BE)
- **API Endpoint (`api.zapier.com`)**:
  - Receives trigger requests.
  - Handles requests and communicates with the hooks server (`hooks.zapier.com`).

### Hooks Server
- Manages GitHub Webhooks (`hooks.zapier.com/a/b`) to respond to updates/events.
- Creates triggers and processes the payload using the database integration.

### Database (DB)
- Stores:
  - Trigger data (`trigger`).
  - Outbox messages (`triggerOutbox`).
- Supports Kafka for event streaming to the processor.

### Processor
- Consumes messages/events from Kafka.
- Processes the events asynchronously.

---

## Key Features

- **Async Event Handling**: Triggers are processed asynchronously to ensure scalability and reliability.
- **Database Integration**: Efficient storage of trigger data and outbox messages.
- **Kafka Integration**: Enables streaming of event messages to the processor.
- **GitHub Hooks**: Supports webhook integration for triggering actions on GitHub updates.
- **Error Tolerance**: Outbox patterns ensure data reliability even when downstream services fail.



This system is designed to ensure efficient, scalable, and reliable asynchronous processing of events, leveraging modern technologies and best practices.

---

## Run Locally. Setup and Installation

1. Clone the repository:

   ```bash
   git clone <https://github.com/shoaibmohammed7/zapier-asyncSystem>
   cd zapier-asyncsystem

2.Install dependencies for all components:

  ```bash
  cd worker
  npm install

  cd ../processor
  npm install

  cd ../primary-backend
  npm install

  cd ../hooks
  npm install

  cd ../frontend
  npm install
  ```

3. Running all the processors locally

   ```bash
    cd worker
    npm run dev

   cd primary-backend
    npm run dev

    cd  hooks
    npm run dev

    cd processor
    npm run dev

    cd frontend
    npm run dev

          ```
4.Access the application in your browser at http://localhost:3000

---
##Scripts
Worker, Processor, Primary Backend, and Hooks
npm run dev: Builds and starts the service in development mode.

---

##Frontend

npm run dev: Starts the development server.
npm run build: Builds the frontend for production.
npm run start: Starts the production server.
npm run lint: Lints the codebase.



