# ChatWeb Application

## Real-Time Chat Application built with Spring Boot, MongoDB, and WebSocket to enable seamless user communication.
# 📖 About ChatWeb

 ChatWeb is a real-time messaging application designed to support private chats with dynamic chat rooms and user status tracking. It leverages Spring Boot for robust back-end services, MongoDB for scalable data storage, and WebSocket for instant two-way communication. Docker is used to streamline MongoDB setup and management.
# ✨ Features

   Dynamic Chat Rooms: Automatically create unique chat rooms for private messaging.
    Real-Time Messaging: Instant communication powered by WebSocket and STOMP messaging.
    User Status Tracking: Online/offline user status with automatic updates.
    Message Persistence: Scalable NoSQL storage using MongoDB (Dockerized).
    Fallback Support: Seamless WebSocket connections with SockJS fallback.

# 🛠️ Technologies Used

    Language: Java
    Framework: Spring Boot
    Messaging Protocol: WebSocket, STOMP
    Database: MongoDB (via Docker)
    Libraries: Lombok, Jackson
    Dependency: spring-boot-starter-data-mongodb
    Containerization: Docker

# 🚀 Getting Started
### Prerequisites

    Java 11 or higher
    Maven 3.6+
    Docker and Docker Compose

# 🚀 MongoDB Setup

This project uses MongoDB as the database and includes a Docker Compose setup to simplify the process. Follow these steps to configure MongoDB for your environment:

Step 1: Modify docker-compose.yml File

Customize the following values in the docker-compose.yml file as per your requirements:

    MongoDB Service:
        MONGO_INITDB_ROOT_USERNAME: Replace with your desired admin username.
        MONGO_INITDB_ROOT_PASSWORD: Replace with your desired admin password.

    Mongo Express Service:
        ME_CONFIG_MONGODB_ADMINUSERNAME: Ensure it matches the MongoDB admin username.
        ME_CONFIG_MONGODB_ADMINPASSWORD: Ensure it matches the MongoDB admin password.

Here’s an example docker-compose.yml snippet for reference:
```
services:
  mongodb:
    image: mongo
    container_name: mongo_db
    ports:
      - 27017:27017
    volumes:
      - mongo:/data
    environment:
      - MONGO_INITDB_ROOT_USERNAME=<your_username>
      - MONGO_INITDB_ROOT_PASSWORD=<your_password>
  mongo-express:
    image: mongo-express
    container_name: mongo_express
    restart: always
    ports:
      - 8081:8081
    environment:
      - ME_CONFIG_MONGODB_ADMINUSERNAME=<your_username>
      - ME_CONFIG_MONGODB_ADMINPASSWORD=<your_password>
      - ME_CONFIG_MONGODB_SERVER=mongodb
volumes:
  mongo: {}
```

Step 2: Start MongoDB Services

Run the following command to start MongoDB and Mongo Express:
``
docker-compose up -d
``
Step 3: Verify MongoDB Setup

Access MongoDB: Open a terminal and connect to the MongoDB shell:

``docker exec -it mongo_db mongo -u <your_username> -p <your_password> --authenticationDatabase admin``

  Access Mongo Express: Open your browser and navigate to http://localhost:8081. Use the credentials you specified in the docker-compose.yml file to log in.

Step 4: Run the Application

Start the Spring Boot application using:

Upon successful startup, the Frontend will be available on http://localhost:8080.

# Notes for Customization

  Port Configuration: If 27017 or 8088 is unavailable, modify the ports in the docker-compose.yml and application.yml files.
