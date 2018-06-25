## Build and Deploy Todo(s) Data  

This Part focuses on adding Todo persistance into the [EcoSystem](/README.md), which amounts to deploying [Todo(s) Data](https://github.com/corbtastik/todos-data) Microservice and binding it to a MySQL [Backing Service](https://12factor.net/backing-services).

### Todo(s) Data

1. [Todo(s) Data](https://github.com/corbtastik/todos-data) - add todos persistence  

The objective is to build and deploy the [Todo(s) Data](#todos-data) on PAS and binding it to a MySQL [Backing Service](https://12factor.net/backing-services).  We'll be using the [Todo(s) CICD](https://github.com/corbtastik/todos-cicd) project to run bash scripts to handle each stage.

### PrePrep

:heavy_exclamation_mark: If you've not completed [PrePrep](https://github.com/corbtastik/todos-ecosystem/blob/master/PREPREP.md) now would be a good time to do that :smile:

### Clone Todo(s) Data  

```bash
> cd $TODOS_HOME
> git clone https://github.com/corbtastik/todos-data.git
```

### Deploy  