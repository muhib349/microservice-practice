# A hands-on project on microservice Architecture with Java, Spring, and Docker
#### In this project, I've learned microservice best practices with the latest technologies.


## Topics Covered
* Spring Boot
* Spring Cloud (Config, Gateway, Netflix)
* The 12-factor App
* Docker and DockerHub
* Resilience4j
* Zipkin 
* Micrometer
* Prometheus
* Grafana
* Apache Kafka

## [Account Service](https://github.com/muhib349/account-service.git)
* Connected with MySQL server running as a container
* Used FeignClient to invoke other microservices (card service and loan service)
* Connected with config server to get all configurations for all environments
* Implemented Netflix Eureka Client for service registration with the Eureka server
* Distributed tracing and log aggregation
* Monitored microservices metrics & health using Prometheus and Grafana
* Integrated Apache Kafka to save account info

## [Card Service](https://github.com/muhib349/card-service.git)
Kind of the same implementation as the accounts service 
## [Loan Service](https://github.com/muhib349/loan-service.git)
Kind of the same implementation as the accounts service

## [Config Server](https://github.com/muhib349/bank-config-server.git)
* Load all configuration from a GitHub repository
* Served properties based on the environment
* RefreshScope for configuration changes with spring cloud bus(rabbitmq)
* Encrypt or Decrypt properties in config server

## [Eureka Server](https://github.com/muhib349/eureka-server.git)
* Treated as service discovery where other microservices will be registered with it
* Other microservices can locate each by using Eureka Server
* Microservices/clients will send their heartbeats at regular intervals to the central server about their health

## [Gateway Server](https://github.com/muhib349/gateway-server.git)
* Known as API gateway implemented using spring cloud gateway
* Handled custom routing requirements from a central place

## About Kafka Integration
For simplicity, I've used Kafka producer & consumer in `account-service`. Created a rest endpoint to save account info in the database. The Kafka producer writes an event into a topic when a client hit the endpoint, and the Kafka consumer consumes the event and writes data into the database.

## Docker Compose
* Maintained docker-compose file for dev and prod environment
* Run all related services in a sequential manner using a single command
## Some Maven Commands I've Used

| Maven Command                                        | Description                                                         |
|------------------------------------------------------|---------------------------------------------------------------------|
| "mvn clean install -Dmaven.test.skip=true"           | To generate a jar inside target folder without executing any tests. |
| "mvn spring-boot:run"                                | To start a springboot maven project                                 |
| "mvn spring-boot:build-image -Dmaven.test.skip=true" | To generate a docker image using Buildpacks. No need of Dockerfile  |


## Some Docker Commands I've Used

| Docker Command                               | Description                                                       |
|----------------------------------------------|-------------------------------------------------------------------|
| "docker build . -t codelabs/accounts"        | To generate a docker image based on a Dockerfile                  |
| "docker run  -p 8081:8080 codelabs/accounts" | To start a docker container based on a given image                |
| "docker images"                              | To list all the docker images present in the Docker server        |
| "docker image rm image-id"                   | To remove one or more images for a given image ids                |
| "docker ps"                                  | To show all running containers                                    |
| "docker ps -a"                               | To show all containers including running and stopped              |
| "docker container start container-id"        | To start one or more stopped containers                           |
| "docker container stop container-id"         | To stop one or more running containers                            |
| "docker container rm container-id"           | To remove one or more containers based on container ids           |
| "docker compose up"                          | To create and start containers based on given docker compose file |
| "docker compose stop"                        | To stop services                                                  |
