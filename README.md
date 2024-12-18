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

---

This system is designed to ensure efficient, scalable, and reliable asynchronous processing of events, leveraging modern technologies and best practices.
