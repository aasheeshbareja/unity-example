
# LOGISTIC RESTful API
## Featuring Docker, Node, Express, MongoDB, Mongoose

## About

- [Docker](https://www.docker.com/) as the container service to isolate the environment.
- [Node.js](https://nodejs.org/en/) (Long-Term-Support Version) as the run-time environment to run JavaScript.
- [Express.js](https://expressjs.com/) as the server framework / controller layer
- [MongoDB](https://www.mongodb.com/) as the database layer
- [Mongoose](https://mongoosejs.com/) as the "ODM" / model layer

## How to Install & Run

1.  Clone the repo
2.  Set Google Distance API key in config/production.json file line no.2
3.  Run `./start.sh`
    after installing them start three containers:
    - the MongoDB database container
    - the Node.js app container
4.  After starting container, test cases will run automatically

## Manually Starting the docker and test Cases

1. You can run `docker-compose up` from terminal
2. Server is accessible at `http://localhost:8080`
3. Run manual test case suite
   1. For Running Unit Test Cases:
   sudo docker exec logistic_app_1 npm test test/unitTests

   2. For Running Integration Test Cases:
   sudo docker exec logistic_app_1 npm test test/integrationTests

## How to Run Tests (Explicity from cli)

 You should be able to run `npm install` followed by `npm test test` to run everything (assuming you have the LTS version of Node installed on your machine).

## App Structure

**./**
-	bin/www contains entry point for application that starts the server
-	`config` contains configuration for development & production environment and pm2 configuration for running the app.
-	`controllers` contains functions which will be called for handling routes.
-	`helper` contains classes used across the application
- `models` contains mongoose schemas.
- `routes` define the routes for different api endpoints.
-	`schemas` contains validation schemas for creating or updating an Order.
-	`test` contains unit & Integration Test Cases in unitTests.js and integrationTests.js respectively.
-	`util` contains utility classes.
-	`app.js` is what builds and configures the express app
- `package.json` defines the dependencies need to be installed for running the application
-	`package-lock.json` to lock down the dependencies at specific version so that there is no issue on different machines
-	`start.sh` is startup script for running the application
-	`.eslintrc` file for code lint.




## API Reference Documentation ##

## GET `/orders?page=:page&limit=:limit` listing orders ##

Response :
     [
         {
                 "id" : "5bee80b9bde99e30fbaa7b67",
                 "distance" : "9999",
                 "status" : "TAKEN",
         },
         {
                 "id" : "5bee80b9bde99e30fbaa7b69",
                 "distance" : "200",
                 "status" : "UNASSIGNED",
         },
     ]

## POST `/orders` Create a new order ##

Request:
 `{
     "origin" :["28.704060", "77.102493"],
     "destination" :["28.535517", "77.391029"]
 }`
Response:
 `{
     "id": "5bee80b9bde99e30fbaa7b6b",
     "distance": 9160,
     "status": "UNASSIGNED"
 }`

## PATCH `/orders/:id` Update order status using its order id ##

Request:
 {
     "status" : "TAKEN"
 }
Response:
 {
     "status": "SUCCESS"
 }



## Google API configuration ##

- add google distance Api key in configuration file located in config/production.json


## Swagger API documentation ##

Swagger documentation can be found at /swagger.json

## Linting ##

Linting configuration available at /.eslintrc.
