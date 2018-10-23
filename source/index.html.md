---
title: API Reference Yo No Desperdicio

language_tabs: # must be one of https://git.io/vQNgJ
   - shell
#   - javascript
#   - java

toc_footers:
  - <a href='http://yonodesperdicio.com/'>web yo no desperdicio</a>
  - <a href='https://play.google.com/store/apps/details?id=com.imaginabit.yonodesperdicion'>Aplicacion android</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - user
  - conversations
  - offers  
  - errors


search: true
---

# Introduccion

API Reference Yo No Desperdicio.

WIP!

<!-- We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right. -->

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
            "image": "/url/images/example.jpg",
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
    ],
    "users": [
        {
            "id": 35,
            "username": "#######",
            "image": "propias/avatar_original.png",
            "zipcode": "#####",
            "total_quantity": 180,
            "rating": 5,
            "created_at": "2015-11-03"
        },
        ...
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


### HTTP Request

`GET https//yonodesperdicio.org/api/ads`

<!-- ### Headers

Parameter | Description
--------- |  -----------
Authroization | must send this  -->


## Get a Specific Ad

<!-- ```ruby
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

-->

> The above command returns JSON structured like this:

```json
{
    "ad": {
        "id": *id_ad*,
        "title": "Cápsulas de café para Nespresso",
        "body": "Cápsulas de café Expresso tenia unas cuantas de sobra",
        "status": 1,
        "grams": 2000,
        "expiration_date": null,
        "pick_up_date": "2016-09-17",
        "comments_enabled": null,
        "image": "/img/url/image.jpg",
        "zipcode": "28005",
        "city": "Madrid",
        "province": "Madrid",
        "food_category": "carne y aves",
        "created_at": "2016-09-07T11:14:09.000Z",
        "updated_at": "2016-09-10T07:37:27.000Z",
        "user_id": **user_id**,
        "comment_ids": []
    },
    "users": [
        {
            "id": **user_id**,
            "username": "dnl",
            "image": "/img/url/aoeu.jpg",
            "zipcode": "28005",
            "total_quantity": 150,
            "rating": 5,
            "created_at": "2015-09-18"
        }
    ],
    "comments": []
}
```

This endpoint retrieves a specific ad info.

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`GET https://yonodesperdicio.org/api/ads/**id_ad**`


### URL Parameters

Parameter | Description
--------- | -----------
id_ad | Id of the ad to retrieve




## Create Ad

`POST https://yonodesperdicio.org/api/ads`

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

xhr.open("POST", "https://yonodesperdicio.org/api/ads");
xhr.setRequestHeader("authorization", "auth_token");
xhr.setRequestHeader("content-type", "application/json");


xhr.send(data);
```


## Edit Ad

`PUT https://yonodesperdicio.org/api/ads/**ad_id**`


```shell
curl -X PUT \
  https://yonodesperdicio.org/api/ads/74 \
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

xhr.open("PUT", "https://yonodesperdicio.org/api/ads/74");
xhr.setRequestHeader("authorization", "**auth_toket**");
xhr.setRequestHeader("content-type", "application/json");

xhr.send(data);
```



## Contador total KG

`GET https://yonodesperdicio.org/api/total_kg`

```shell
curl -X GET \
  https://yonodesperdicio.org/api/total_kg
```

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
```

>The above command returns JSON structured like this:
```json
{
    "total_kg": 105.61
}
```

## Delete Ad

DELETE https://yonodesperdicio.org/api/ads/**ad_id**


```shell
curl -X DELETE \
  https://yonodesperdicio.org/api/ads/66 \
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

xhr.open("DELETE", "https://yonodesperdicio.org/api/ads/66");
xhr.setRequestHeader("authorization", "auth_token");
xhr.setRequestHeader("content-type", "application/json");



xhr.send(data);
```

## Categories

GET https://yonodesperdicio.org/api/categories

```shell
curl -X GET \
  https://yonodesperdicio.org/api/categories 
```

