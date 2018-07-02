## Build and Deploy Todo(s) CQrS  

This Part focuses on building and deploying a [CQrS](https://martinfowler.com/bliki/CQRS.html) system within the Todo(s) Eco.  Once deployed it's possible to route Creating, Updating and Deleting Todo(s) to the Command Microservice and Reads to the Query one.  [The primary function of CQrS](https://martinfowler.com/bliki/CQRS.html) is to separate read and write logic and that's what this Part will accomplish without a lot of fanfare.

If you've completed all previous [parts](/README.md#parts) then at the end of this lesson you'll have the following picture deployed locally and on [PAS](http://run.pivotal.io/).

### Eco on Local

<p align="center">
  <img src="https://github.com/corbtastik/todos-images/blob/master/todos-ecosystem/TodosCqRS-Local.png" width="480">
</p>

### Eco on PAS

<p align="center">
  <img src="https://github.com/corbtastik/todos-images/blob/master/todos-ecosystem/TodosCqRS-PAS.png" width="480">
</p>

### PrePrep

:heavy_exclamation_mark: If you've not completed [PrePrep](https://github.com/corbtastik/todos-ecosystem/blob/master/PREPREP.md) now would be a good time to do that :smile:

### CqRS Cloud Deployment

#### CqRS Set

1. [Todo(s) Command](https://github.com/corbtastik/todos-command)
1. [Todo(s) Query](https://github.com/corbtastik/todos-query)

#### Backing Services

1. ``todos-db`` - SQL Backing Database (h2 ``default``, mysql ``cloud``)
1. ``todos-cache`` - Redis Backing cache
1. ``todos-messaging`` - RabbitMQ Backing messaging backbone

### Clone Todo(s) Command and Query  

```bash
> cd $TODOS_HOME
> git clone https://github.com/corbtastik/todos-command.git
> git clone https://github.com/corbtastik/todos-query.git
```

### Deploy  

Once [PAS Properties](/PREPREP.md#pas-properties) are set it's time to point-and-click and coolout while we burst into the cloud. :sunglasses:

```bash
> cd $TODOS_HOME/todos-cicd/part_5
> ./deploy.sh
```