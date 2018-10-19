# Conversations

## Get Conversations

GET https://yonodesperdicio.org/api/mailboxes/inbox/conversations

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


## Get Messages from conversation

GET https://yonodesperdicio.org/api/mailboxes/inbox/conversations/**conversation_id**/messages

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