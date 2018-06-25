## Build and Deploy Spring Cloud   

This Part focuses on building out Spring Cloud to support the Todo(s) EcoSystem we deployed in Part 1.  Once completed the Base Set will integrate with [Spring Cloud Config Server](https://github.com/spring-cloud/spring-cloud-config) and [Service Registry](https://spring.io/blog/2015/01/20/microservice-registration-and-discovery-with-spring-cloud-and-netflix-s-eureka).

### Spring Cloud Set

1. [Config Server](https://github.com/corbtastik/config-server) - Spring Cloud Config Server
2. [Cloud Index](https://github.com/corbtastik/cloud-index) - Spring Cloud Service Discovery

The objective is to build and deploy the [Spring Cloud Set](#spring-cloud-set) on PAS and confirm the [Base Set](https://github.com/corbtastik/todos-ecosystem/blob/master/PART_1.md#base-set) integrates with Config and Service Discovery.  We'll be using the [Todo(s) CICD](https://github.com/corbtastik/todos-cicd) project to run bash scripts to handle each stage.

### PrePrep

If you've not completed [PrePrep](https://github.com/corbtastik/todos-ecosystem/blob/master/PREPREP.md) now would be a good time to do that :smile:

### Clone Base Set  

```bash
> git clone https://github.com/corbtastik/todos-cicd.git
> git clone https://github.com/corbtastik/todos-gateway.git
> git clone https://github.com/corbtastik/todos-api.git
> git clone https://github.com/corbtastik/todos-ui.git
```

### PAS Properties  

Before running ``todos-cicd/part_1/deploy.sh`` edit ``todos-cicd/deploy.conf`` and add your PAS properties.  ``deploy.conf`` has presets for [Pivotal Web Services](https://run.pivotal.io).

```bash
#!/bin/bash
cf_api="https://api.run.pivotal.io"
cf_domain="cfapps.io"
cf_user=""
cf_pass=""
cf_org=""
cf_space=""
```

### Deploy  

Once [PAS Properties](#pas-properties) are set it's time to point-and-click and coolout while we burst into the cloud. :sunglasses:

```bash
cd todos-cicd/part_1
./deploy.sh
```

### Verify Part 1

#### Verify Deployment  

Do a quick sanity check on the deployment.

```bash
> cf apps
Getting apps in org bubbles / space dev as ...
OK

name            requested state   instances   memory   disk   urls
todos-api       started           1/1         1G       1G     todos-api.cfapps.io
todos-gateway   started           1/1         1G       1G     todos-gateway.cfapps.io
todos-ui        started           1/1         512M     1G     todos-ui.cfapps.io
```

#### Verify Endpoints  

Call ``/ops/info`` endpoint on Spring Boot Microservices.

```bash
> http todos-gateway.cfapps.io/ops/info
HTTP/1.1 200 OK
Content-Type: application/vnd.spring-boot.actuator.v2+json;charset=UTF-8
X-Vcap-Request-Id: 55ea5199-ab82-4e50-7684-324e593c28de

{
    "build": {
        "artifact": "todos-gateway",
        "group": "io.corbs",
        "name": "todos-gateway",
        "time": "2018-06-24T19:38:24.979Z",
        "version": "1.0.0.SNAP"
    }
}
```

#### Verify UI

Have a little fun with [Todo(s) UI](https://github.com/corbtastik/todos-ui.git). :relaxed: Try opening it from the gateway ``http://todos-gateway.cfapps.io`` which will put it in-front of the ``/api``.

<p align="center">
    <img src="https://github.com/corbtastik/todos-images/raw/master/todos-ui/todos-ui-online-cloudy.png" width="640">
</p>

