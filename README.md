## Overview

### This repository contains the Docker configuration files for setting up a Ruby on Rails application with PostgreSQL using Docker Compose. The setup includes creating environment variables for PostgreSQL credentials, Dockerfiles for PostgreSQL and the Rails application, as well as a Docker Compose configuration to orchestrate the services.

## Step 1: Creating Environment Variables for PostgreSQL
### To create environment variables for PostgreSQL in the terminal, use the following command:
```
kubectl create secret generic postgres-credentials \
  --from-literal=POSTGRES_USER=your_username \
  --from-literal=POSTGRES_PASSWORD=your_password \
  --from-literal=POSTGRES_DB=your_database
```
####(Replace your_username, your_password, and your_database with your actual PostgreSQL credentials.)
##Step 2: Dockerfiles
### PostgreSQL Dockerfile
###The Dockerfile for PostgreSQL sets up a PostgreSQL 15 image and sets environment variables for PostgreSQL credentials.

### Ruby on Rails Dockerfile
###The Dockerfile for the Ruby on Rails application sets up a Ruby 2.6 environment, installs dependencies including PostgreSQL client, Node.js, and Yarn, and copies the application files. It then precompiles assets and exposes port 3000 for the Rails server.

###Step 3: Docker Compose Configuration
###The Docker Compose configuration (docker-compose.yml) defines two services: web for the Ruby on Rails application and db for PostgreSQL. It specifies the build context and Dockerfiles for both services, exposes port 3000 for the web service, and sets environment variables for the database URL in the web service.
Building the Images

### To build the Docker images, run the following command:
```
docker-compose build
```
### Running the Docker Compose Configuration

###To start the services defined in the Docker Compose configuration, run the following command:
```
docker-compose up
```
This command will start the web and db services, making the Rails application available at http://localhost:3000.
