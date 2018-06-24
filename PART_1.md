## Build, Deploy Base Set  

This lesson focuses on building and running the base set of Todo(s) apps, which consists of

### Base Set  

1. [Todo(s) Gateway](https://github.com/corbtastik/todos-gateway) - Spring Cloud Zuul
2. [Todo(s) API](https://github.com/corbtastik/todos-api) - Spring Boot API
3. [Todo(s) UI](https://github.com/corbtastik/todos-ui) - todomvc.com Vue.js UI

The objective is to build and deploy the [Base Set of Todo(s) Apps](#base-set) on PAS.  We'll be using the [Todo(s) CICD](https://github.com/corbtastik/todos-cicd) project to run bash scripts to handle each stage.

### Pre-Prep

Create a top-level directory to house all apps.  [Todo(s) CICD](https://github.com/corbtastik/todos-ui) requires all Todo(s) projects to exist on the same-level.

### Create project directory

```bash
> mkdir todos-apps
> cd todos-apps
```

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

