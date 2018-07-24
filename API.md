# Todo(s) API

This API contract is left to the implementer and represents the HTTP interface of a CRUD based Todo API.  Many of the apps in Todo(s) EcoSystem implements this interface.

* [Todo(s) API](https://github.com/corbtastik/todos-api)
* [Todo(s) WebFlux](https://github.com/corbtastik/todos-webflux)
* [Todo(s) RestTemplate Client](https://github.com/corbtastik/todos-restclient)
* [Todo(s) WebClient](https://github.com/corbtastik/todos-webclient)
* [Todo(s) Data](https://github.com/corbtastik/todos-data)
* [Todo(s) Cache](https://github.com/corbtastik/todos-cache)

Note - this API does not specify a context-root.  It's possible to hang this API off any root path, for example ``todos/``.

## Create

### Request  

```bash
POST /
{
    "title" : "make bacon pancakes"
}
```

### Exceptions

* If the API has a limit (such as you can only create 25 Todo(s) or something) and the limit is reached then return ``400 Bad Request``.

### Response

```bash
HTTP 200 ok | 204 created
{
    "completed": false,
    "id": 1,
    "title": "make bacon pancakes"
}
```

## Retrieve All

### Request  

```bash
GET /
```

### Response

```bash
HTTP 200 ok
[
    {
        "completed": false,
        "id": 1,
        "title": "make bacon pancakes"
    },
    {
        "completed": false,
        "id": 2,
        "title": "eat bacon pancakes"
    }  
]
```

## Retrieve One

### Request

```bash
GET /2
```

### Exceptions

* If the id of the Todo is invalid return ``404 Not Found``

### Response  

```bash
HTTP 200 ok
{
    "completed": false,
    "id": 2,
    "title": "eat bacon pancakes"
}
```

## Update  

* Use ``PATCH`` for updating Todo properties
* Provide partial JSON to update fields (i.e. ``{"completed":true}``)
* Return an updated view of Todo

### Request  

```bash
PATCH /2
{
    "completed" : true
}
```

### Exceptions

* If the id of the Todo is invalid return ``404 Not Found``
* If the Todo JSON is malformed return ``400 Bad Request``

### Response  

```bash
HTTP ok 200
{
    "completed": true,
    "id": 2,
    "title": "eat bacon pancakes"
}
```

## Delete One

### Request 

```bash
DELETE /2
```

### Response

```bash
HTTP 200 ok
```