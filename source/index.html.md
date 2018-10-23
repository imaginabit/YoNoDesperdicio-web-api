---
title: API Reference Yo No Desperdicio

language_tabs: # must be one of https://git.io/vQNgJ
   - shell
   - javascript
   - java

toc_footers:
  - <a href='http://yonodesperdicio.com/'>web yo no desperdicio</a>
  - <a href='https://play.google.com/store/apps/details?id=com.imaginabit.yonodesperdicion'>Aplicacion android</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - ads
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
        "id": ###,
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


# Contador total KG

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


# Categories

GET https://yonodesperdicio.org/api/categories

```shell
curl -X GET \
  https://yonodesperdicio.org/api/categories 
```

