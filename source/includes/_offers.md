# Offers 

<aside class="notice">
Edit me, please
</aside>
*Lo he copiado tal cual del mensaje de telegram de Mijaíl*

##View all offers

http://beta.yonodesperdicio.org/api/offers


##View the offer with id=1

http://beta.yonodesperdicio.org/api/offers/1

##Create an offer

POST to /api/offers with the offer data and the Authorization header with the token that returned the login

Example:

```shell
curl -H "Content-Type: application/json" /
    -H "Authorization: TB1T2pDQuGYExhJQ5vYB" /
    -X POST /
    -d '{"offer":{"title": "Title of offer", "address": "The offer address", "store": "The offer store", "until": "2018-10-21", "description": "The offer description"}}' /
    -X POST http://localhost:3000/api/offers
```


>Returns the saved offer, with the id assigned in the database:

```json
{
  "id": 4,
  "title": "Title of offer",
  "address": "The offer address",
  "store": "The offer store",
  "until": "2018-10-21T00:00:00.000Z",
  "status": "available",
  "image": {
    "medium": "http://localhost:3000/assets/propias/offer_medium.png",
    "large": "http://localhost:3000/assets/propias/offer_large.png",
    "original": "http://localhost:3000/propias/offer_original.png"
  }
}
```