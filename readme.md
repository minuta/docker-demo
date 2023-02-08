# A Demo Web App - devoloping with Docker

### about
a simple web-app, showing a user profile, that can be edited and persisted in a database.
The app is used to demonstrate docker on using with multi-containers.

### tech stack
- NodeJS
- Docker
- MongoDB
- Mongo Express

### run

#### 1. via Docker Compose

run containers and start app:

    # docker compose -f docker-compose.yaml up -d
    # node server.js

stop containers:

    # docker compose down

#### 2. manually (without Docker Compose)


### links:
- Mongo Express : http://localhost:8080/
- Web App : http://localhost:3000/