# Conversations

Ahora mismo la aplicacion sigue este proceso para obtener las convesraciones 

llama get conversations INBOX
cuando obtiene el resultado llama a get conversations SENT


## Get Conversations INBOX

Get conversations of the user, INBOX only has conversations created by other user or with awnser from other user

### HTTP Request

`GET https://yonodesperdicio.org/api/mailboxes/inbox/conversations`

#### Headers

Parameter | Description
--------- |  -----------
Authorization | Authorization token 

<!-- #### URL Parameters

Parameter | Description
--------- | -----------
user_id | Id of the ad to retrieve -->


```javascript
var data = null;

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "https://yonodesperdicio.org/api/mailboxes/inbox/conversations");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "auth_token");



xhr.send(data);
```

#### Json response

list of conversations with this params :

Parameter | Description
--------- |  -----------
id | Authorization token 
subject | Conversation subject
created_at | date of creation
updated_at | date of last message
thread_id | ?

*Proposed*

Parameter | Description
--------- |  -----------
user_id | id of the other user or id of all users in conversation
last_msg | text of the last message in conversation



Devuelve json con id y subject de la conversacion

```json
{
    "conversations": [
        {
            "id": 151,
            "subject": "manzanas",
            "created_at": "2017-03-23T09:46:39.000Z",
            "updated_at": "2018-10-06T12:12:52.000Z",
            "thread_id": 0
        },
        {
            "id": 25,
            "subject": "Pipas",
            "created_at": "2016-02-08T16:53:52.000Z",
            "updated_at": "2016-02-12T21:23:01.000Z",
            "thread_id": 0
        }
    ]
}
```


## Get Conversations SENT

Get conversations of the user, SENT only has conversations created by the user 


### HTTP Request

`GET https://yonodesperdicio.org/api/mailboxes/sent/conversations`

#### Headers

Parameter | Description
--------- |  -----------
Authorization | Authorization token 

<!-- #### URL Parameters

Parameter | Description
--------- | -----------
user_id | Id of the ad to retrieve -->


```javascript
var data = null;

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "https://yonodesperdicio.org/api/mailboxes/inbox/conversations");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "auth_token");



xhr.send(data);
```

Devuelve json con id y subject de la conversacion

```json
{
    "conversations": [
        {
            "id": 151,
            "subject": "manzanas",
            "created_at": "2017-03-23T09:46:39.000Z",
            "updated_at": "2018-10-06T12:12:52.000Z",
            "thread_id": 0
        },
        {
            "id": 25,
            "subject": "Pipas",
            "created_at": "2016-02-08T16:53:52.000Z",
            "updated_at": "2016-02-12T21:23:01.000Z",
            "thread_id": 0
        }
    ]
}
```



# Messages 


## Get Messages from conversation INBOX

`GET https://yonodesperdicio.org/api/mailboxes/inbox/conversations/**conversation_id**/messages`

```
```

```json
{
    "messages": [
        {
            "id": 467,
            "body": "hola quiero tus manzanas",
            "subject": "manzanas",
            "sender_id": 247,
            "sender_type": "User",
            "conversation_id": 151,
            "draft": false,
            "updated_at": "2017-03-23T09:46:39.000Z",
            "created_at": "2017-03-23T09:46:39.000Z",
            "notified_object_id": null,
            "notified_object_type": null,
            "notification_code": null,
            "attachment": {
                "url": null
            },
            "global": false,
            "expires": null
        },
        ...
        {
            "id": 1001,
            "body": "prueba",
            "subject": "manzanas",
            "sender_id": 247,
            "sender_type": "User",
            "conversation_id": 151,
            "draft": false,
            "updated_at": "2018-10-06T12:12:50.000Z",
            "created_at": "2018-10-06T12:12:50.000Z",
            "notified_object_id": null,
            "notified_object_type": null,
            "notification_code": null,
            "attachment": {
                "url": null
            },
            "global": false,
            "expires": null
        }
    ],
    "meta": {
        "pagination": {
            "per_page": 0,
            "total_pages": 1,
            "total_objects": 13
        }
    }
}
```


## Get Messages from conversation SENT
 
 `GET https://yonodesperdicio.org/api/mailboxes/sent/conversations/**conversation.id**/messages`

la respuesta es igual que en INBOX 

Notese que si el usuario manda un mensaje y no obtiene respuesta no hay manera de saber cual es el usuaria al que se le ha enviado el mensaje 


```json
{
    "messages": [
        {
            "id": 510,
            "body": "hola",
            "subject": "prueba",
            "sender_id": 41,
            "sender_type": "User",
            "conversation_id": 135,
            "draft": false,
            "updated_at": "2018-11-09T20:11:37.000Z",
            "created_at": "2018-11-09T20:11:37.000Z",
            "notified_object_id": null,
            "notified_object_type": null,
            "notification_code": null,
            "attachment": {
                "url": null
            },
            "global": false,
            "expires": null
        }
    ],
    "meta": {
        "pagination": {
            "per_page": 0,
            "total_pages": 1,
            "total_objects": 1
        }
    }
}
```

## New Message

https://yonodesperdicio.org/api/new_message/**user_id**


```javascript
var data = JSON.stringify({
  "message": {
    "subject": "Apples",
    "body": "Hi, I really like apples"
  }
});

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://yonodesperdicio.org/api/new_message/user_id");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "auth_token");

xhr.send(data);
```

```json
{
    "id": *message_id*,
    "body": "Hi, I really like apples",
    "subject": "Apples",
    "sender_id": *your_user_id*,
    "sender_type": "User",
    "conversation_id": *conversation_id*,
    "draft": false,
    "updated_at": "2018-10-19T15:58:50.000Z",
    "created_at": "2018-10-19T15:58:50.000Z",
    "notified_object_id": null,
    "notified_object_type": null,
    "notification_code": null,
    "attachment": {
        "url": null
    },
    "global": false,
    "expires": null
}
```