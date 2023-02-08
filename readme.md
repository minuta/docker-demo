# A Demo Web App - devoloping with Docker

### about
a simple web-app, showing a user profile, that can be edited and persisted in a database.
The app is used to demonstrate docker on using with multi-containers.

### tech stack
- NodeJS
- Docker
- MongoDB
- Mongo Express

---

### run

#### 1. via Docker Compose

run containers and start app:

```sh
docker compose -f docker-compose.yaml up -d
```

```sh
node server.js
```

Cleaning Up
stop containers :

```sh
docker compose stop
```
or stop and remove containers :

```sh
docker compose down
```
remove docker network :

```sh
docker network rm mongo-network
```

#### 2. manually (without Docker Compose)

create a new docker network:
```sh
docker network create mongo-network
```

check the created docker network:
```sh
docker network ls
```

create and run container with MongoDB in the given docker network:
```sh
docker run -d -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password --name mongodb --net mongo-network mongo
```

create and run container with Mongo Express in the given docker network and connect that to the running MongoDB container:
```sh
docker run -d -p 8080:8081 -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin -e ME_CONFIG_MONGODB_ADMINPASSWORD=password --net mongo-network --name mongo-express -e ME_CONFIG_MONGODB_SERVER=mongodb mongo-express
```

The Mongo Express should be available on the http://localhost:8080/

Now run the app : 
```sh
node server.js
```

The app should be available on the http://localhost:3000/

Clean Up:

stop running containers:
```sh
docker stop mongo-express
docker stop mongodb
```

remove stopped containers:
```sh
docker rm mongo-express
docker rm mongodb
```

remove docker network :
```sh
docker network rm mongo-network
```

---

### Links:
- Mongo Express : http://localhost:8080/
- Web App : http://localhost:3000/

Source: based on a tutorial of Nana Janashia.