# Fast Dolphin Project
Fast Dolphin is a comprehensive web application that integrates a backend API, a Telegram bot, and MongoDB as its primary database, all seamlessly orchestrated using Docker.

## Services Overview:
- `API`: The primary backend service that interacts with the MongoDB database and communicates with RabbitMQ to send messages. Built using FastAPI (assuming based on the naming).
- `MongoDB`: The primary datastore for the Fast Dolphin API.
- `Telegram Bot`: A bot that can receive and potentially send messages. It listens to the RabbitMQ notify_admin queue for messages from the API.
- `RabbitMQ`: A message broker used to facilitate communication between the API and the Telegram bot.

## Interaction Flow:
`API` and `MongoDB`: The `API` communicates with `MongoDB` for data storage and retrieval purposes.

`API` and `RabbitMQ`: The `API` sends messages to `RabbitMQ` (specifically to the `notify_admin` queue) which are meant to be received by the `Telegram bot`.

`Telegram Bot` and `RabbitMQ`: The `Telegram bot` listens to the `notify_admin` queue in `RabbitMQ`, processing any messages that the `API` sends to that queue.

### Getting Started:

#### Prerequisites:
- Docker and Docker Compose installed on your machine.

#### Setup:
Clone the repository:

```bash
git clone [your-repo-link]
cd [your-repo-directory]
```

Create a `.env` file in the root of the project.

Build and start the Docker services:

```bash
docker-compose up --build
```

#### Access:
- The `API` should be accessible at http://localhost:8000.
- `MongoDB` is exposed on its default port 27017.
- `RabbitMQ` is exposed on its default port 5672.