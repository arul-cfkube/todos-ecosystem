## Build and Deploy Todo(s) Data  

This Part focuses on adding Todo persistance into the [EcoSystem](/README.md), which amounts to deploying [Todo(s) Data](https://github.com/corbtastik/todos-data) and binding it to a MySQL [Backing Service](https://12factor.net/backing-services).

This Part focuses on building out Spring Cloud to support the Todo(s) EcoSystem we deployed in Part 1.  Once completed the Base Set will integrate with [Spring Cloud Config Server](https://github.com/spring-cloud/spring-cloud-config) and [Service Registry](https://spring.io/blog/2015/01/20/microservice-registration-and-discovery-with-spring-cloud-and-netflix-s-eureka).

### Spring Cloud Set

1. [Config Server](https://github.com/corbtastik/config-server) - Spring Cloud Config Server
2. [Cloud Index](https://github.com/corbtastik/cloud-index) - Spring Cloud Service Discovery

The objective is to build and deploy the [Spring Cloud Set](#spring-cloud-set) on PAS and confirm the [Base Set](/PART_1.md#base-set) integrates with Config and Service Discovery.  We'll be using the [Todo(s) CICD](https://github.com/corbtastik/todos-cicd) project to run bash scripts to handle each stage.

### PrePrep

:heavy_exclamation_mark: If you've not completed [PrePrep](https://github.com/corbtastik/todos-ecosystem/blob/master/PREPREP.md) now would be a good time to do that :smile:

### Clone Spring Cloud Set  

```bash
> cd $TODOS_HOME
> git clone https://github.com/corbtastik/config-server.git
> git clone https://github.com/corbtastik/cloud-index.git
```

### Deploy  