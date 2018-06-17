## Todo(s) Ecosystem of Microservices

Each one of these Microservices can be developed, deployed and tested individually but each one also participates in a larger demo set thats meant to highlight Spring Boot and Cloud Foundry (specifically Pivotal Application Service, which has a Cloud Foundry core) features.

### The Apps, Microservices and Scripts

#### Apps

App | Description
------------ | -------------
todos-ui | todomvc.com Vue.js frontend Todo(s) UI

#### JVM Microservices

Microservice | Description
------------ | -------------
todos-gateway | Todo(s) API gateway featuring Zuul
todos-api | Todo(s) REST API in Spring Boot 2.0
todos-restclient | Todo(s) HTTP Client, used to call Todo(s) API(s)
todos-command | Todo(s) CQRS impl, command pattern, Spring Boot w/ Spring Cloud Streams
todos-query | Todo(s) CQRS impl, query pattern, Spring Boot w/ Feign Client
todos-cache | Todo(s) cache, Spring Boot w/ Spring Data Redis and Spring Cloud Streams
todos-data | Todos(s) Data Microservice, using Spring Boot JPA and Spring Data REST
todos-webflux | Todo(s) REST API in Spring Boot 2.0 WebFlux for non-blocking endpoints
todos-webclient | Todo(s) Reactive HTTP Client, used to call Todo(s) API(s)
todos-source | Todo(s) Event Driven Source Microservice in Spring Cloud Streams
todos-sink | Todo(s) Event Driven Sink Microservice in Spring Cloud Streams
todos-kotlin | Todo(s) REST API in Spring Boot 2.0 implemented with Kotlin

#### Non JVM Microservice

Non JVM Microservice | Description
------------ | -------------
todos-nodejs | Todo(s) REST API in Node.js w/ Express.js

#### Spring Cloud Support

Spring Cloud component | Description
------------ | -------------
config-server | Spring Cloud Config Server, used to host external config for ecosystem
cloud-index | Spring Cloud Netflix Eureka Server, used for Service Discovery

#### Build, Release, Run

CI/CD | Description
------------ | -------------
todos-cicd | Build, Release and Run scripts for local and cloud deployment of the ecosystem

### Spring Cloud Support

Each JVM based Microservice taps into the power of Spring Cloud which you'll need if you're deploying Microservices on a Macro scale.

Each Microservices uses these Spring Cloud Dependencies

* Spring Cloud Config Client for Centralized Config
* Spring Cloud Eureka Client for Service Discovery
* Spring Cloud Sleuth for Tracing

And a few such as the Spring Cloud Streams and Spring Data Microservices use Hystix

* Spring Cloud Hystrix for Circuit Breaking

### Todo(s) UI

The Todo(s) UI in this ecosystem is an exact clone of [todomvc.com's Vue.js implementation](http://todomvc.com/examples/vue/).

<p align="center">
    <img src="https://github.com/corbtastik/todos-images/raw/master/todos-ui/todos-ui-one.png">
</p>

### Todo(s) Gateway

### Todo(s) API

### Todo(s) Rest Client

### Todo(s) Command

### Todo(s) Query

### Todo(s) Cache

### Todo(s) Data

### Todo(s) WebFlux

### Todo(s) WebClient

### Todo(s) Source

### Todo(s) Sink

### Todo(s) Kotlin

### Config Server

### Cloud Index

### Todo(s) CI/CD
