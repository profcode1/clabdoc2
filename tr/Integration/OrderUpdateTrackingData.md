# Sipariş Güncelleme Entegrasyonu

> Siparişleri çektikten sonra işlemlerinize göre siparişlerinizi güncellemek için sipariş güncelleme entegrasyonu siparişleri yönetebilirisiniz.

# Api

Sipariş Statüsü güncelleme

Method:`PUT`

URL:`https://{path_the_comlab_api}/sapigw/suppliers/{{supplierid}}/shipment-packages/1141`


POSTMAN / Curl
```sh
curl --location -g --request PUT 'https://{path_the_comlab_api}/sapigw/suppliers/{{supplierid}}/shipment-packages/1141' \
--header 'Authorization: Basic xxx=' \
--header 'Content-Type: application/json' \
--data-raw '{
    "Status":"Invoiced",
    "Lines":[],
    "Params":{
        "invoiceNumber":"1-R-1-1236"
    }
}
'
```
> Result
```json
{
    "BatchRequestId": "902b6d5831ab4e5a91ba46afb451f618",
    "IsSuccess": true,
    "Message": null
}
```

Bu istek sonrası size bu işlem adına bir BatchRequestId verilir. Bu işlemin bitip bitmediği veya başarılı olup olmadığı BatchRequest sorgulama apisi ile öğrenilmelidir.

# Api BatchRequest Sonucunu görme

Method:`PUT`

URL:`https://{path_the_comlab_api}/sapigw/suppliers/{{supplierid}}/products/batch-requests/58027b239a0543f9987e2274f8694936`


POSTMAN / Curl
```sh
curl --location -g --request PUT 'https://{path_the_comlab_api}/sapigw/suppliers/{{supplierid}}/products/batch-requests/58027b239a0543f9987e2274f8694936' \
--header 'Authorization: Basic xxx=' \
--header 'Content-Type: application/json' \
'
```
> Result
```json
{
    "BatchRequestId": "58027b239a0543f9987e2274f8694936",
    "Items": [
        {
            "Value": "1141",
            "Status": "SUCCESS",
            "FailureReasons": [
                ""
            ]
        }
    ],
    "Status": "COMPLETED",
    "CreationDate": 1641562367240,
    "LastModification": 1641562367303,
    "SourceType": "API",
    "ItemCount": 1
}
```