# DevOps Microservices Project

A multi-container microservices architecture built with Docker Compose. It consists of two Flask-based services (`user-service` and `data-service`), a PostgreSQL database, and a Redis cache. 

## 🧱 Microservices Overview

### 🔹 user-service
- Registers new users into the database.
- Endpoint:  
POST /register
Body: { "name": "alice", "info": "some info" }


### 🔹 data-service
- Retrieves user info.
- Uses Redis for caching results.
- Endpoint:  
GET /user/<name>

##  PostgreSQL Database

- Initialized using `init.sql`
- Table: `users(name TEXT UNIQUE, info TEXT)`
- Docker image: `postgres:14`

## Redis Cache
Used by data-service to reduce repeated DB queries

Caches user info on first GET

Docker image: redis:alpine

>>>> To Run the Project:
docker-compose up --build

## Example Requests:
Register User:
curl -X POST http://localhost:5001/register \
-H "Content-Type: application/json" \
-d '{"name": "divyanshi", "info": "I am from Jaipur"}'

Get User Info:
curl http://localhost:5000/user/divyanshi

## Stop containers using:
docker-compose down



