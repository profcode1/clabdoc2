# Ürün Entegrasyonu

![screenshoot](../../../m/productIntegration.png)

> Ürün entegrasyonu için gerekli ve zorunlu alanlar

|Alan|Zorunlumu?|Açıklama|Değer|Örnek|
|:-|:-:|-|-|-|
| Type|Hayır||variant,single,bundle|variant|
| Model|Evet| Model bir ürünün varyantsız tanımıdır. Bir ürünü renk bazında eşleştirmek için Model kodları aynı olmalıdır. Bir model kodunun altında aynı renkten birden fazla olamaz.|Serbest|GOMLEK10|
| OptionCode|Evet|Bir Fotoğrafa ve renge sahip olan listelenebilir ürünü temsil eder. Bir OptionCode altında eğer varyant var ise aynı varyant özelliğine sahip olan 2 Sku olamaz.|Serbest|GOMLEK10KRMZ|
| Sku|Evet|Sku satılabilir, sepete eklenebilir ürünü temsil eder ve tekildir. Aynı Sku dan birden fazla olamaz. |Serbest|GOMLEK10KRMZM|
| Barcode|Evet|Ürünün varsayılan barkodudur ve tekildir.|Serbest|978020137962

Ürün hiyerarşik yapısı
* Model
    * Option
        * Sku - `Barcode`

Yukarıdaki örnek üzerinden gidecek olursak.

* GOMLEK10 `Gömlek 10 modeli`
    * GOMLEK10KRMZ `Gömlek 10 modelinin Kırmızı Renkli ürünü`
        * GOMLEK10KRMZM `Gömlek 10 modeli Kırmızı Renkli ve medium bedenlisi`


# Api

Method:`POST`

Security:`Basic Auth`

URL:`{path_the_comlab_api}/sapigw/suppliers/{supplierid}/v2/products`

Request Body:
```json
{
    "items": [{
            "barcode": "324324324324",
            "title": "Regular Fit Normal Kesim  Gömlek",
            "productMainId": "EDFCVG",
            "brandId": 22,
            "brandName": "Abc",
            "categoryId": 597,
            "quantity": 0.0,
            "stockCode": "EDFCVGKRMZXL",
            "dimensionalWeight": 0,
            "description": "%100 Pamuk, Mavi",
            "currencyType": "TRY",
            "listPrice": 399.0,
            "salePrice": 199.9,
            "vatRate": 8.0,
            "cargoCompanyId": 12,
            "shipmentAddressId": 0,
            "returningAddressId": 0,
            "images": [{
                    "url": "https://path_to_photo_1.jpg",
                    "UpdatedOn": "2021-03-10T17:24:58"
                }, {
                    "url": "https://path_to_photo_2.jpg",
                    "UpdatedOn": "2021-03-10T17:24:57"
                }
            ],
            "attributes": [
                {                   
                    "attributeName": "Model Kodu",
                    "attributeValue": "EDF"
                },
                {                   
                    "attributeName": "Renk",
                    "attributeValue": "Kırmızı"
                },{
                   
                    "attributeName": "Beden",
                    "attributeValue": "XL"
                },{
                   
                    "attributeName": "Cinsiyet",
                    "attributeValue": "Erkek"
                }, {
                   
                    "attributeName": "Kategori",
                    "attributeValue": "Gömlek"
                }
            ]
        }, 
        {
            "barcode": "324324324324",
            "title": "Regular Fit Normal Kesim  Gömlek",
            "productMainId": "EDFCVG",
            "brandId": 22,
            "brandName": "Abc",
            "categoryId": 597,
            "quantity": 0.0,
            "stockCode": "EDFCVGKRMZM",
            "dimensionalWeight": 0,
            "description": "%100 Pamuk, Mavi",
            "currencyType": "TRY",
            "listPrice": 399.0,
            "salePrice": 199.9,
            "vatRate": 8.0,
            "cargoCompanyId": 12,
            "shipmentAddressId": 0,
            "returningAddressId": 0,
            "images": [{
                    "url": "https://path_to_photo_1.jpg",
                    "UpdatedOn": "2021-03-10T17:24:58"
                }, {
                    "url": "https://path_to_photo_2.jpg",
                    "UpdatedOn": "2021-03-10T17:24:57"
                }
            ],
            "attributes": [
                {                   
                    "attributeName": "Model Kodu",
                    "attributeValue": "EDF"
                },
                {
                   
                    "attributeName": "Renk",
                    "attributeValue": "Kırmızı"
                },{
                   
                    "attributeName": "Beden",
                    "attributeValue": "M"
                },{
                   
                    "attributeName": "Cinsiyet",
                    "attributeValue": "Erkek"
                }, {
                   
                    "attributeName": "Kategori",
                    "attributeValue": "Gömlek"
                }
            ]
        }
    ]
}

```
POSTMAN / Curl
```sh
curl --location -g --request POST '{path_the_comlab_api}/sapigw/suppliers/{supplierid}/v2/products' \
--header 'Authorization: Basic xxx=' \
--header 'Content-Type: application/json' \
--data-raw '{
    "items": [{
            "barcode": "324324324324",
            "title": "Regular Fit Normal Kesim  Gömlek",
            "productMainId": "EDFCVG",
            "brandId": 22,
            "brandName": "Abc",
            "categoryId": 597,
            "quantity": 0.0,
            "stockCode": "EDFCVGKRMZXL",
            "dimensionalWeight": 0,
            "description": "%100 Pamuk, Mavi",
            "currencyType": "TRY",
            "listPrice": 399.0,
            "salePrice": 199.9,
            "vatRate": 8.0,
            "cargoCompanyId": 12,
            "shipmentAddressId": 0,
            "returningAddressId": 0,
            "images": [{
                    "url": "https://path_to_photo_1.jpg",
                    "UpdatedOn": "2021-03-10T17:24:58"
                }, {
                    "url": "https://path_to_photo_2.jpg",
                    "UpdatedOn": "2021-03-10T17:24:57"
                }
            ],
            "attributes": [
                {                   
                    "attributeName": "Model Kodu",
                    "attributeValue": "EDF"
                },
                {                   
                    "attributeName": "Renk",
                    "attributeValue": "Kırmızı"
                },{
                   
                    "attributeName": "Beden",
                    "attributeValue": "XL"
                },{
                   
                    "attributeName": "Cinsiyet",
                    "attributeValue": "Erkek"
                }, {
                   
                    "attributeName": "Kategori",
                    "attributeValue": "Gömlek"
                }
            ]
        }, 
        {
            "barcode": "324324324325",
            "title": "Regular Fit Normal Kesim  Gömlek",
            "productMainId": "EDFCVG",
            "brandId": 22,
            "brandName": "Abc",
            "categoryId": 597,
            "quantity": 0.0,
            "stockCode": "EDFCVGKRMZM",
            "dimensionalWeight": 0,
            "description": "%100 Pamuk, Mavi",
            "currencyType": "TRY",
            "listPrice": 399.0,
            "salePrice": 199.9,
            "vatRate": 8.0,
            "cargoCompanyId": 12,
            "shipmentAddressId": 0,
            "returningAddressId": 0,
            "images": [{
                    "url": "https://path_to_photo_1.jpg",
                    "UpdatedOn": "2021-03-10T17:24:58"
                }, {
                    "url": "https://path_to_photo_2.jpg",
                    "UpdatedOn": "2021-03-10T17:24:57"
                }
            ],
            "attributes": [
                {                   
                    "attributeName": "Model Kodu",
                    "attributeValue": "EDF"
                },
                {
                   
                    "attributeName": "Renk",
                    "attributeValue": "Kırmızı"
                },{
                   
                    "attributeName": "Beden",
                    "attributeValue": "M"
                },{
                   
                    "attributeName": "Cinsiyet",
                    "attributeValue": "Erkek"
                }, {
                   
                    "attributeName": "Kategori",
                    "attributeValue": "Gömlek"
                }
            ]
        }
    ]
}'
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
    "BatchRequestId": "0116ebe904054da7a3f19bf16101fc45",
    "Items": [
        {
            "Value": "324324324324",
            "Status": "SUCCESS",
            "FailureReasons": [
                null
            ]
        },
        {
            "Value": "324324324325",
            "Status": "SUCCESS",
            "FailureReasons": [
                null
            ]
        }
    ],
    "Status": "COMPLETED",
    "CreationDate": 1641445355247,
    "LastModification": 1641445389313,
    "SourceType": "API",
    "ItemCount": 450
}
```


>Sonraki :  [Fiyat Stok Entegrasyonu](PriceStock.md)