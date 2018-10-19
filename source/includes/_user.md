# User

## Get User Info

GET http://beta.yonodesperdicio.org/api/users/**user_id**


> respuesta otro usuario

```json
{
    "user": {
        "id": 1,
        "username": "anatecla",
        "image": "/system/users/images/000/000/001/original/Sula_patas_azules.600x450.jpg?1443019723",
        "zipcode": "28011",
        "total_quantity": 500,
        "rating": 2.5,
        "created_at": "2015-08-07"
    }
}

```

> resupuesta tu propio usuairo

```json
{
    "session_user": {
        "id": 247,
        "username": "eca",
        "total_quantity": 0,
        "rating": null,
        "image": "propias/avatar_original.png",
        "zipcode": "35011",
        "city": "las palmas",
        "province": "lpgc",
        "email": "email@example.com",
        "auth_token": "**auth_token**",
        "created_at": "2016-02-08",
        "fcm_registration_token": "**firebase cloud message token**"
    }
}
```


## User ads ( no auth )

GET https://yonodesperdicio.org/api/ads?user_id=**user_id**

```javascript
var data = new FormData();
data.append("username", "");
data.append("password", "");

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "http://yonodesperdicio.org/api/ads?user_id=1");
xhr.setRequestHeader("authorization", "null");

xhr.send(data);
```

```json

{
    "ads": [
        {
            "id": 146,
            "title": "Conserva de tomate",
            "body": "Varios botes de tomate natural triturado. Conservas manuales.",
            "status": 2,
            "grams": 500,
            "expiration_date": null,
            "pick_up_date": "2017-11-11",
            "comments_enabled": 0,
            "image": "/system/ads/images/000/000/146/original/Tomatoes_plain_and_sliced.jpg?1510251128",
            "zipcode": "28011",
            "city": "Madrid",
            "province": "Madrid",
            "food_category": "conservas",
            "created_at": "2017-11-09T18:09:12.000Z",
            "updated_at": "2017-11-09T18:12:09.000Z",
            "user_id": 1,
            "comment_ids": []
        },
        {
            "id": 2,
            "title": "Avellanas",
            "body": "Me dieron varios kilos de avellanas. Están muy ricas, pero no puedo consumirlas todas que son demasiadas! Si quieres, escríbeme y te las paso.",
            "status": 3,
            "grams": 500,
            "expiration_date": null,
            "pick_up_date": "2015-11-07",
            "comments_enabled": 1,
            "image": "/system/ads/images/000/000/002/original/avellanas.jpg?1445260079",
            "zipcode": "28013",
            "city": "Madrid",
            "province": "Madrid",
            "food_category": "fruta",
            "created_at": "2015-10-19T13:07:59.000Z",
            "updated_at": "2015-11-05T16:18:59.000Z",
            "user_id": 1,
            "comment_ids": [
                10
            ]
        }
    ],
    "users": [
        {
            "id": 1,
            "username": "anatecla",
            "image": "/system/users/images/000/000/001/original/Sula_patas_azules.600x450.jpg?1443019723",
            "zipcode": "28011",
            "total_quantity": 500,
            "rating": 2.5,
            "created_at": "2015-08-07"
        },
        {
            "id": 1,
            "username": "anatecla",
            "image": "/system/users/images/000/000/001/original/Sula_patas_azules.600x450.jpg?1443019723",
            "zipcode": "28011",
            "total_quantity": 500,
            "rating": 2.5,
            "created_at": "2015-08-07"
        }
    ],
    "comments": [
        {
            "id": 10,
            "body": "Me van quedando pocas...",
            "created_at": "2015-10-26T14:59:04.000Z",
            "updated_at": "2015-10-26T14:59:04.000Z",
            "user_id": 1
        }
    ],
    "meta": {
        "pagination": {
            "per_page": 0,
            "total_pages": 1,
            "total_objects": 2
        }
    }
}
```

## Anuncios usuario (autentificado)

GET https://yonodesperdicio.org/api/ads

```
curl -X GET \
  https://yonodesperdicio.org/api/ads \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -F username=**username** \
  -F password=**pass**
```


## Send new firebase token to user

Device send token to save on 

PUT https://yonodesperdicio.org/api/users/218


## Usen new avatar

PUT http://yonodesperdicio.org/api/users/43

## Rate user

POST https://yonodesperdicio.org/api/users/43/rate

???

