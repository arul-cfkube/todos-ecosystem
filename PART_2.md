## Build and Deploy Spring Cloud   

This Part focuses on building out Spring Cloud to support the Todo(s) EcoSystem we deployed in Part 1.  Once completed the Base Set will integrate with [Spring Cloud Config Server](https://github.com/spring-cloud/spring-cloud-config) and [Service Registry](https://spring.io/blog/2015/01/20/microservice-registration-and-discovery-with-spring-cloud-and-netflix-s-eureka).

### Spring Cloud Set

1. [Config Server](https://github.com/corbtastik/config-server) - Spring Cloud Config Server
2. [Cloud Index](https://github.com/corbtastik/cloud-index) - Spring Cloud Service Discovery

The objective is to build and deploy the [Spring Cloud Set](#spring-cloud-set) on PAS and confirm the [Base Set](https://github.com/corbtastik/todos-ecosystem/blob/master/PART_1.md#base-set) integrates with Config and Service Discovery.  We'll be using the [Todo(s) CICD](https://github.com/corbtastik/todos-cicd) project to run bash scripts to handle each stage.

### PrePrep

:heavy_exclamation_mark: If you've not completed [PrePrep](https://github.com/corbtastik/todos-ecosystem/blob/master/PREPREP.md) now would be a good time to do that :smile:

### Clone Spring Cloud Set  

```bash
> cd $TODOS_HOME
> git clone https://github.com/corbtastik/config-server.git
> git clone https://github.com/corbtastik/cloud-index.git
```

### Deploy  

Once [PAS Properties](https://github.com/corbtastik/todos-ecosystem/blob/master/PREPREP.md#pas-properties) are set it's time to point-and-click and coolout while we burst into the cloud. :sunglasses:

```bash
> cd $TODOS_HOME/todos-cicd/part_2
> ./deploy.sh
```

### Verify Part 2

#### Verify Deployment  

Do a quick sanity check on the deployment.

```bash
> cf apps
Getting apps in org bubbles / space dev as ...
OK

name            requested state   instances   memory   disk   urls
cloud-index     started           1/1         1G       1G     cloud-index.cfapps.io
config-server   started           1/1         1G       1G     config-srv.cfapps.io
```

#### Verify Endpoints  

Call endpoints on the Cloud Index and Config Server.

##### Call ``/ops/info`` endpoint on Spring Boot Microservices.

```bash
> http config-srv.cfapps.io/ops/info
HTTP/1.1 200 OK
Content-Type: application/vnd.spring-boot.actuator.v2+json;charset=UTF-8
X-Vcap-Request-Id: 5ef5b69c-2fc9-442b-77e1-6043abcb7174

{
    "build": {
        "artifact": "config-server",
        "group": "io.corbs",
        "name": "config-server",
        "time": "2018-06-25T15:49:59.559Z",
        "version": "1.0.0.SNAP"
    }
}
```

##### 
#### Verify UI

Have a little fun with [Todo(s) UI](https://github.com/corbtastik/todos-ui.git). :relaxed: Try opening it from the gateway ``http://todos-gateway.cfapps.io`` which will put it in-front of the ``/api``.

<p align="center">
    <img src="https://github.com/corbtastik/todos-images/raw/master/todos-ui/todos-ui-online-cloudy.png" width="640">
</p>

