## Build and Deploy Todo(s) Cache  

This Part focuses on adding Todo caching into the [EcoSystem](/README.md), which amounts to deploying the [Todo(s) Cache](https://github.com/corbtastik/todos-cache) Microservice and binding it to a Redis [Backing Service](https://12factor.net/backing-services).

### Todo(s) Cache

1. [Todo(s) Cache](https://github.com/corbtastik/todos-cache) - add caching with redis  

The objective is to build and deploy the [Todo(s) Cache](#todos-cache) on PAS and bind it to a Redis [Backing Service](https://12factor.net/backing-services).  We'll be using the [Todo(s) CICD](https://github.com/corbtastik/todos-cicd) project to run bash scripts to handle each stage.

### PrePrep

:heavy_exclamation_mark: If you've not completed [PrePrep](https://github.com/corbtastik/todos-ecosystem/blob/master/PREPREP.md) now would be a good time to do that :smile:

### Clone Todo(s) Cache  

```bash
> cd $TODOS_HOME
> git clone https://github.com/corbtastik/todos-cache.git
```

### Deploy  

Once [PAS Properties](/PREPREP.md#pas-properties) are set it's time to point-and-click and coolout while we burst into the cloud. :sunglasses:

```bash
> cd $TODOS_HOME/todos-cicd/part_4
> ./deploy.sh
```

### Verify Part 4

#### Verify Deployment  

Do a quick sanity check on the deployment.

```bash
> cf apps
Getting apps in org bubbles / space dev as ...

```