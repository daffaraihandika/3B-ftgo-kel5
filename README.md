
# 3B-Kelompok 5

Ini merupakan skenario test yang dilakukan pada aplikasi ftgo pada order service



## Test Scenario

| Test Id | Name              | Method | Endpoint       | Test Data                                                                                                                                                             | Response | Result |
| ------- | ----------------- | ------------- | ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- | ------ |
| TC1     | Membuat Consumer | POST   | ```/consumers```  | ```Create Consumer: {"name": {"firstName": "daffa","lastName": "raihandika"}}``` | ```{"consumerId": 1}``` | PASS |
| TC2     | Mendapatkan Detail Consumer berdasarkan Id | GET   | ```/consumers/{consumerId}```  | consumerId = 1 | ```{"consumerId": 0,"name": {"firstName": "daffa","lastName": "raihandika"}}``` | PASS |
| TC3     | Membuat Restaurant | POST   | ```/restaurants```  | ```Create Restaurant: { "address": { "city": "Bandung", "state": "Jawa Barat", "street1": "Ciwaruga", "zip": "01234" }, "menu": { "menuItems": [ { "id": "1", "name": "Nasi telor kornet", "price": "15000" },{ "id": "2", "name": "Indomie goreng", "price": "7000" } ] }, "name": "Tampomas" }``` | ```{"id": 1}``` | PASS |
| TC4     | Mendapatkan Detail Restaurant berdasarkan Id | GET   | ```/restaurants/{restaurantId}``` | restaurantId = 2 | ```{"id": 1,"name": "Tampomas"}``` | PASS |
| TC5     | Membuat Order | POST   | ```/orders``` | ```Create Order: {"consumerId": 1,"deliveryAddress": {"city": "Bandung","state": "Ciwaruga","street1": "Serra Valley","zip": "4321"},"deliveryTime": "2024-04-05T12:39:32.797Z","lineItems": [{"menuItemId": "2","quantity": 1}],"restaurantId": 1}``` | ```{"orderId": 3}``` | PASS |
| TC6     | Mendapatkan Detail Order berdasarkan Id | GET   | ```/orders/{orderId}``` | orderId = 3 | ```{"orderId": 3,"state": "APPROVED","orderTotal": "7000.00"}``` | PASS |
| TC7     | Melakukan Revise Order berdasarkan Id | POST   | ```/orders/{orderId}/revise``` | orderId = 3, ```Revise Order : {"revisedOrderLineItems": [{"menuItemId": "2","quantity": 3}]}``` | ```{"orderId": 3,"state": "APPROVED","orderTotal": "21000.00"}``` | PASS |
| TC8     | Mendapatkan Detail Order berdasarkan Id (setelah revise) | GET   | ```/orders/{orderId}``` | orderId = 3 | ```{"orderId": 3,"state": "APPROVED","orderTotal": "21000.00"}``` | PASS |
| TC9     | Melakukan Cancel Order berdasarkan Id | POST   | ```/orders/{orderId}/cancel``` | orderId = 3 | ```{"orderId": 3,"state": "APPROVED","orderTotal": "21000.00"}``` | PASS |
| TC10     | Mendapatkan Detail Order berdasarkan Id (setelah cancel) | GET   | ```/orders/{orderId}``` | orderId = 3 | ```{"orderId": 3,"state": "CANCELLED","orderTotal": "21000.00"}``` | PASS |
| TC11     | Melihat Order History berdasarkan Consumer Id | GET   | ```/orders?{consumerId}``` | consumerId = 1 | ```{"orders": [{"orderId": "3","status": "APPROVED","restaurantId": 1,"restaurantName": "Tampomas"},{"orderId": "2","status": "CANCELLED","restaurantId": 1,"restaurantName": "Tampomas"},{"orderId": "1","status": "CANCELLED","restaurantId": 1,"restaurantName": "Tampomas"}],"startKey": null}``` | PASS |

## Screenshots

### TC1
![App Screenshot](https://drive.google.com/file/d/1NdkTTmabi9BGNpFSFjbPRe3-hBQWTsQR/view?usp=sharing)


## Authors

- [@rzanta](https://github.com/rzanta)
- [@egisatriadyw](https://github.com/egisatriadyw)
- [@daffaraihandika](https://github.com/daffaraihandika)
- [@reihanhadifauzan](https://github.com/reihanhadifauzan)
- []()
- [@zis4215](https://github.com/zis4215)