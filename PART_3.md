## Build and Deploy Todo(s) Data  

This Part focuses on adding Todo persistance into the [EcoSystem](/README.md), which amounts to deploying the [Todo(s) Data](https://github.com/corbtastik/todos-data) Microservice and binding it to a MySQL [Backing Service](https://12factor.net/backing-services).

### Todo(s) Data

1. [Todo(s) Data](https://github.com/corbtastik/todos-data) - add todos persistence  

The objective is to build and deploy the [Todo(s) Data](#todos-data) on PAS and bind it to a MySQL [Backing Service](https://12factor.net/backing-services).  We'll be using the [Todo(s) CICD](https://github.com/corbtastik/todos-cicd) project to run bash scripts to handle each stage.

### PrePrep

:heavy_exclamation_mark: If you've not completed [PrePrep](https://github.com/corbtastik/todos-ecosystem/blob/master/PREPREP.md) now would be a good time to do that :smile:

### Clone Todo(s) Data  

```bash
> cd $TODOS_HOME
> git clone https://github.com/corbtastik/todos-data.git
```

### Deploy  

Once [PAS Properties](/PREPREP.md#pas-properties) are set it's time to point-and-click and coolout while we burst into the cloud. :sunglasses:

```bash
> cd $TODOS_HOME/todos-cicd/part_3
> ./deploy.sh
```

### Verify Part 3

#### Verify Deployment  

Do a quick sanity check on the deployment.

```bash
> cf apps
Getting apps in org bubbles / space dev as ...
OK

name            requested state   instances   memory   disk   urls
todos-data      started           1/1         1G       1G     todos-data.cfapps.io
```

#### Verify Endpoints  

Call ``/ops/info`` endpoint on the Todo(s) Data Microservices.

```bash
> http todos-data.cfapps.io/ops/info  
HTTP/1.1 200 OK
Content-Type: application/vnd.spring-boot.actuator.v2+json;charset=UTF-8
X-Vcap-Request-Id: bc7b7d98-df39-4edf-644e-343cd04f7353

{
    "build": {
        "artifact": "todos-data",
        "group": "io.corbs",
        "name": "todos-data",
        "time": "2018-06-25T19:19:39.577Z",
        "version": "1.0.0.SNAP"
    }
}
```

#### Call Eureka endpoint to list App(s)

If you've completed [Part 1](/PART_1.md) & [Part 2](/PART_2.md) then you should see apps for [Todo(s) Gateway](https://github.com/corbtastik/todos-gateway), [Todo(s) API](https://github.com/corbtastik/todos-api), [Config Server](https://github.com/corbtastik/config-server) and now Todo(s) Data.

```bash
> http cloud-index.cfapps.io/eureka/apps | grep "<app>"
      <app>TODOS-GATEWAY</app>
      <app>TODOS-API</app>
      <app>TODOS-DATA</app>
      <app>CONFIG-SERVER</app>
```

#### Create and save a Todo

```bash
> http todos-data.cfapps.io/todoEntities/ title="make bacon pancakes"
HTTP/1.1 201 Created
Content-Type: application/json;charset=UTF-8
Location: http://todos-data.cfapps.io/todoEntities/12
X-Vcap-Request-Id: e425184a-7460-40ae-585e-91b5563355a1

{
    "_links": {
        "self": {
            "href": "http://todos-data.cfapps.io/todoEntities/12"
        },
        "todoEntity": {
            "href": "http://todos-data.cfapps.io/todoEntities/12"
        }
    },
    "completed": false,
    "title": "make bacon pancakes"
}
```  

#### Retreive Todo(s)  

```bash
> http todos-data.cfapps.io/todoEntities/ 
HTTP/1.1 200 OK
Connection: keep-alive
Content-Type: application/hal+json;charset=UTF-8
X-Vcap-Request-Id: cce9ab08-696d-4a72-444f-d5168467d635

{
    "_embedded": {
        "todoEntities": [
            {
                "_links": {
                    "self": {
                        "href": "http://todos-data.cfapps.io/todoEntities/2"
                    },
                    "todoEntity": {
                        "href": "http://todos-data.cfapps.io/todoEntities/2"
                    }
                },
                "completed": false,
                "title": "document cloud profile"
            },
            {
                "_links": {
                    "self": {
                        "href": "http://todos-data.cfapps.io/todoEntities/12"
                    },
                    "todoEntity": {
                        "href": "http://todos-data.cfapps.io/todoEntities/12"
                    }
                },
                "completed": false,
                "title": "make bacon pancakes"
            }
        ]
    },
    "_links": {
        "profile": {
            "href": "http://todos-data.cfapps.io/profile/todoEntities"
        },
        "search": {
            "href": "http://todos-data.cfapps.io/todoEntities/search"
        },
        "self": {
            "href": "http://todos-data.cfapps.io/todoEntities{?page,size,sort}",
            "templated": true
        }
    },
    "page": {
        "number": 0,
        "size": 20,
        "totalElements": 2,
        "totalPages": 1
    }
}
```

#### MySQL Backing Service

When Todo(s) Data boots it connects to the ``todos-db`` backing service which we built in [PrePrep](/PREPREP.md).  Now that we've added a Todo let's look at it inside the database.

The snippets below use [cf-mysql-plugin](https://github.com/andreasf/cf-mysql-plugin) to access the database.

```bash
> cf mysql todos-db
Creating new service key cf-mysql for todos-db...
Your MySQL connection id is 2796738359
Server version: 5.5.56-log MySQL Community Server (GPL)
Copyright (c) 2000, 2018, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| ad_8ba3382327fbabb |
+--------------------+
2 rows in set (4.10 sec)

mysql> use ad_8ba3382327fbabb
Database changed
mysql> show tables;
+------------------------------+
| Tables_in_ad_8ba3382327fbabb |
+------------------------------+
| flyway_schema_history        |
| todos                        |
+------------------------------+
2 rows in set (0.05 sec)

mysql> select * from todos;
+----+------------------------+-----------+
| id | title                  | completed |
+----+------------------------+-----------+
| 12 | make bacon pancakes    |           |
+----+------------------------+-----------+
2 rows in set (0.05 sec)

```

### That's all for Part 3 - Stay Frosty :snowman:
