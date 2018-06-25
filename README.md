## Todo(s) Ecosystem of Microservices

Each one of these Microservices can be developed and deployed individually but each one also participates in a larger demo set thats meant to highlight [Spring Boot](https://spring.io/projects/spring-boot) and [Pivotal Application Service](https://pivotal.io/platform/pivotal-application-service) feartures.

### Part(s)

The Ecosystem is divided into smaller parts, each highlighting specific features of [Spring Boot](https://spring.io/projects/spring-boot), [Spring Cloud](https://projects.spring.io/spring-cloud/) and [Pivotal Application Service](https://pivotal.io/platform/pivotal-application-service).  Feel free to clone and play around with [each one](#apps) individually or work through these Part(s) which builds out the EcoSystem on the [Cloud](https://run.pivotal.io/).

1. [Build and Deploy Base Set](PART_1.md) - build and cf push...awe yeah
2. [Build and Deploy Spring Cloud](PART_2.md) - build and cf push Spring Cloud stack
3. [Build and Deploy Todo(s) Data](PART_3.md) - build and cf push Todo(s) Data to enable saving Todo(s)
4. [Build and Deploy Todo(s) Cache](PART_4.md) - build and cf push Todo(s) Cache

### Apps

App | Description | Local Port | PAS enabled
------------ | ------------- | ------------- | -------------  
[todos-ui](https://github.com/corbtastik/todos-ui) | todomvc.com Vue.js frontend Todo(s) UI | 4040 | [yes](https://github.com/corbtastik/todos-ui#run-on-pas)

### JVM Microservices

Microservice | Description | Local Port | PAS enabled
------------ | ------------- | ------------- | -------------  
[todos-gateway](https://github.com/corbtastik/todos-gateway) | Todo(s) API gateway featuring Zuul | 9999 | [yes](https://github.com/corbtastik/todos-gateway#run-on-pas)
[todos-api](https://github.com/corbtastik/todos-api) | Todo(s) REST API in Spring Boot 2.0 | 8080 | [yes](https://github.com/corbtastik/todos-api#run-on-pas)  
[todos-restclient](https://github.com/corbtastik/todos-restclient) | Todo(s) HTTP Client, used to call Todo(s) API(s) | 8006 | NO  
[todos-command](https://github.com/corbtastik/todos-command) | Todo(s) CQRS impl, command pattern, Spring Boot w/ Spring Cloud Streams |  
[todos-query](https://github.com/corbtastik/todos-query) | Todo(s) CQRS impl, query pattern, Spring Boot w/ Feign Client |  
[todos-cache](https://github.com/corbtastik/todos-cache) | Todo(s) cache, Spring Boot w/ Spring Data Redis and Spring Cloud Streams |
[todos-data](https://github.com/corbtastik/todos-data) | Todos(s) Data Microservice, using Spring Boot JPA and Spring Data REST | 8003 | [yes](https://github.com/corbtastik/todos-data#run-on-pas)
[todos-webflux](https://github.com/corbtastik/todos-data) | Todo(s) REST API in Spring Boot 2.0 WebFlux for non-blocking endpoints |
[todos-webclient](https://github.com/corbtastik/todos-webclient) | Todo(s) Reactive HTTP Client, used to call Todo(s) API(s) |  
[todos-source](https://github.com/corbtastik/todos-source) | Todo(s) Event Driven Source Microservice in Spring Cloud Streams |  
[todos-sink](https://github.com/corbtastik/todos-sink) | Todo(s) Event Driven Sink Microservice in Spring Cloud Streams |  
[todos-kotlin](https://github.com/corbtastik/todos-kotlin) | Todo(s) REST API in Spring Boot 2.0 implemented with Kotlin |  

### Non JVM Microservice

Non JVM Microservice | Description | Local Port
------------ | ------------- | -------------
[todos-nodejs](https://github.com/corbtastik/todos-nodejs) | Todo(s) REST API in Node.js w/ Express.js | 

### Spring Cloud Support

Spring Cloud component | Description | Local Port
------------ | ------------- | -------------
[config-server](https://github.com/corbtastik/config-server) | Spring Cloud Config Server, used to host external config for ecosystem | 8888
[cloud-index](https://github.com/corbtastik/cloud-index) | Spring Cloud Netflix Eureka Server, used for Service Discovery | 8761

### Build, Release, Run

CI/CD | Description
------------ | -------------
[todos-cicd](https://github.com/corbtastik/todos-cicd) | Build, Release and Run scripts for local and cloud deployment of the ecosystem

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

Todo(s) Gateway is a Zuul based router used to front requests for Todo(s) Microservices.

### Todo(s) API

Todo(s) REST API in Spring Boot using ``@RestController and @RequestMappings``.

### Todo(s) Rest Client

Todo(s) API Client using RestTemplate and OkHttp.

### Todo(s) Command

Todo(s) Command component of CQRS using Spring Cloud Streams.

### Todo(s) Query

Todo(s) Query component of CQRS using Spring Boot and Feign.

### Todo(s) Cache

Todo(s) Cache Microservice using Spring Data Redis and Spring Data Rest.

### Todo(s) Data

Todo(s) Data Microservice using Spring Data JPA and Spring Data Rest.

### Todo(s) WebFlux

Todo(s) REST API in Spring Boot 2.0 using the Reactive Stack to build a non-blocking API.

### Todo(s) WebClient

Todo(s) API Client using WebClient to make non-blocking API calls.

### Todo(s) Source

Todo(s) Source Microservice using Spring Cloud Streams to source Todo Event(s).

### Todo(s) Sink

Todo(s) Sink Microservice using Spring Cloud Streams to sink Todo Event(s).

### Todo(s) Kotlin

Todo(s) REST API in Spring Boot using Kotlin.

### Config Server

Spring Cloud Config Server for all Todo(s) Microservices.

### Cloud Index

Spring Cloud Netflix Eureka server for all Todo(s) Microservices.

### Todo(s) CI/CD

Build, Release and Run scripts for local and cloud deployments on Pivotal Application Service.
