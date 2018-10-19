---
title: API Reference Yo No Desperdicio

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  # - ruby
  # - python
  - javascript
  # - java
  # - kotlin

toc_footers:
    - <a href='http://yonodesperdicio.com/'>web yo no desperdicio</a>
  - <a href='https://play.google.com/store/apps/details?id=com.imaginabit.yonodesperdicion'>Aplicacion android</a>
  # - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - conversations
  - offers  
  - errors

search: true
---

# Introduccion

Bienvenido a la API de Yo No Desperdicio.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This API documentation page was created with [Slate](https://github.com/lord/slate).

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl -X POST \
  https://yonodesperdicio.org/api/sessions \
  -H 'content-type: multipart/form-data' \
  -F username='user_name' \
  -F password='secret password'
```

```javascript
var data = new FormData();
data.append("username", "user name");
data.append("password", "secret password");

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://yonodesperdicio.org/api/sessions");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```

> The above command returns JSON structured like this:

```json
{
    "session_user": {
        "id": 100,
        "username": "Username",
        "total_quantity": 0,
        "rating": null,
        "image": "propias/avatar_original.png",
        "zipcode": "35011",
        "city": "las palmas",
        "province": "lpgc",
        "email": "user@example.com",
        "auth_token": "<auth_token>",
        "created_at": "2016-02-08",
        "fcm_registration_token": "<fcm_token>"
    }
}
```

> If you put a wrong password it returns:

```json
{
  "errors":"Invalid username or password"
}
```

> Make sure to replace `auth_token` with your auth token.

<!-- `Authorization: meowmeowmeow` -->

<aside class="notice">
You must replace <code>user name</code> and <code>password</code> with your user/password from the website.
</aside>

You need a auth_token to use the api, get your *auth_token* with your user and password 




# Ads

## Get Ads 

> Make sure to replace `auth_token` with your auth token.

<aside class="notice">
You must replace <code>auth_token</code> with your personal auth token.
</aside>


```shell
curl "https://yonodesperdicio.org/api/ads"
  -H "Authorization: auth_token"
```

> The above command returns JSON structured like this:

```json
{
    "ads": [
        {
            "id": 225,
            "title": "Caja de Hojaldres de León",
            "body": "Trajeron muchas cosas para una merienda y esta caja de hojaldres no hizo falta",
            "status": 1,
            "grams": 230,
            "expiration_date": null,
            "pick_up_date": "2019-04-09",
            "comments_enabled": 1,
            "image": "/system/ads/images/000/000/225/original/IMG_8105.JPG?1539072229",
            "zipcode": "28003",
            "city": "madrid",
            "province": "madrid",
            "food_category": "pan y bollería",
            "created_at": "2018-10-09T08:03:50.000Z",
            "updated_at": "2018-10-09T08:03:50.000Z",
            "user_id": 35,
            "comment_ids": []
        },
        ...
        25 anuncios
        ...
        {
            "id": 187,
            "title": "Angurriñas    ",
            "body": "La fecha max de recogida es hoy viernes 03/08. Estare disponible hasta las 13.30 en Pza. de Castilla",
            "status": 1,
            "grams": 125,
            "expiration_date": null,
            "pick_up_date": "2018-08-03",
            "comments_enabled": null,
            "image": "/system/ads/images/000/000/187/original/angurri%C3%B1as____.jpg?1533253450",
            "zipcode": "28046",
            "city": "Madrid",
            "province": "Madrid",
            "food_category": "pescado y marisco",
            "created_at": "2018-08-02T23:44:13.000Z",
            "updated_at": "2018-08-16T12:42:36.000Z",
            "user_id": 1378,
            "comment_ids": []
        }
    ],
    "users": [
        {
            "id": 35,
            "username": "Beatriz",
            "image": "propias/avatar_original.png",
            "zipcode": "28003",
            "total_quantity": 180,
            "rating": 5,
            "created_at": "2015-11-03"
        },
        {
            "id": 1570,
            "username": "acc",
            "image": "propias/avatar_original.png",
            "zipcode": "28050",
            "total_quantity": 0,
            "rating": null,
            "created_at": "2018-10-04"
        }
    ],
    "meta": {
        "pagination": {
            "per_page": 0,
            "total_pages": 6,
            "total_objects": 146
        }
    }
}
```

This endpoint retrieves all kittens.

### HTTP Request

`GET https//yonodesperdicio.org/api/ads`

### Headers

Parameter | Description
--------- |  -----------
Authroization | must send this 


## Get a Specific Ad

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve



## Create Ad

POST https://yonodesperdicio.org/api/ads

```javascript
var data = JSON.stringify({
  "ad": {
    "title": "Milk",
    "body": "I have 5 milk briks ",
    "grams": "5000",
    "status": "1",
    "food_category": "bebidas",
    "image": ""
  }
});

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "http://beta.yonodesperdicio.org/api/ads");
xhr.setRequestHeader("authorization", "auth_token");
xhr.setRequestHeader("content-type", "application/json");


xhr.send(data);
```


## Edit Ad

PUT https://yonodesperdicio.org/api/ads/**ad_id**

```shell
curl -X PUT \
  http://beta.yonodesperdicio.org/api/ads/74 \
  -H 'authorization: **auth_token**' \
  -H 'content-type: application/json' \ 
  -d '{"ad": {"title":"Edit from api"}}'
```

```javascript
var data = JSON.stringify({
  "ad": {
    "title": "Edit from api"
  }
});

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("PUT", "http://beta.yonodesperdicio.org/api/ads/74");
xhr.setRequestHeader("authorization", "**auth_toket**");
xhr.setRequestHeader("content-type", "application/json");

xhr.send(data);
```



## Contador total KG

https://yonodesperdicio.org/api/total_kg

```javascript
var data = null;

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "https://yonodesperdicio.org/api/total_kg");

xhr.send(data);

```json
{
    "total_kg": 105.61
}
```

## Delete Ad

DELETE http://yonodesperdicio.org/api/ads/**ad_id**


```shell
curl -X DELETE \
  http://yonodesperdicio.org/api/ads/66 \
  -H 'authorization: auth_token' \  
  -H 'content-type: application/json' \
  -d '{"ad": { "title":"probando desde api","body":"un alimento muy rico","grams":"120", "status":"1", "food_category":"bebidas","image": "" }}'
```

```javascript
var data = JSON.stringify({
  "ad": {
    "title": "probando desde api",
    "body": "un alimento muy rico",
    "grams": "120",
    "status": "1",
    "food_category": "bebidas",
    "image": ""
  }
});

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("DELETE", "http://yonodesperdicio.org/api/ads/66");
xhr.setRequestHeader("authorization", "auth_token");
xhr.setRequestHeader("content-type", "application/json");



xhr.send(data);
```

## Categories

GET https://yonodesperdicio.org/api/categories

```shell
curl -X GET \
  http://yonodesperdicio.org/api/categories 
```

