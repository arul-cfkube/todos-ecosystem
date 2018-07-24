# Todo(s) API

This API contract is left to the implementer and represents the HTTP interface of a CRUD based Todo API.  Many of the apps in Todo(s) EcoSystem implements this interface.

* Todo(s) API
* Todo(s) WebFlux
* Todo(s) RestTemplate Client
* Todo(s) WebClient
* Todo(s) Data
* Todo(s) Cache

## Create

### Request  

```bash
POST /
{
    "title" : "make bacon pancakes"
}
```

### Response

```json
{
    "completed": false,
    "id": 1,
    "title": "make bacon pancakes"
}
```

Retrieve

Update

Delete

