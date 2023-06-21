# Onaylanan Satıcı Ürünlerini Listeleme

# Api

Method:`GET`

Security:`Basic Auth` 

URL:`{path_the_comlab_pim_api}/pim/GetConfirmedVendorProduct`

|Parametre|Tip|Açıklama|
|-|-|-|
|merchantSku|`string` |Satıcı Ürün Kodunu belirtir.|
|vendorCode|`string`|Satıcı VKN belirtir.| 
|title|`string`| Ürün Başlık alanıdır. | 
|barcode| `string`|Ürün barkod numarasını belirtir.| 
|olcuBirimi|`string`| Ölçü Birimini belirtir. | 
|vatRate|`string`|KDV oranını belirtir. | 
|sctRate|`string`|ÖTV oranını belirtir. | 
|listPrice|`string`| Satın Alma Fiyatını belirtir. | 
|salePrice|`string`|Satış Fiyatını belirtir.| 
 

> Request üzerinde iki filtre bulunmaktadır: "SAP barkodu var mı?" ve "Ürün onaylandı mı?" İhtyaca göre bu filtreler değiştirilir ve ihtiyaca uygun response alınır.
> Selected Columns alanında ürünlerle ilgili gelmesi istenen parametreler yer almaktadır. Bu alanlar ihtiyaca göre doldurularak istenilen verilerin gelmesi sağlanır.


Request Body:
```json
[{
    "FilteredColumns": [
        {
            "column": "hasExternalBarcode",
            "value": false
        },
        {
            "column": "isApproved",
            "value": true
        }
    ],
    "SelectedColumns": [
        "supplierId",
        "vendorCode",
        "merchantSku",
        "title",
        "olcubirimi",
        "vatRate",
        "sctRate",
        "listPrice",
        "salePrice"
    ],
    "Page": 1,
    "PageSize": 5
}
]

```
POSTMAN / Curl
```sh
curl --location 'https://stgapi.a101.prod.hebiar.com/pim/vendor/products?isPre=true&includeParents=false' \
--header 'Authorization: Base64str' \
--header 'Content-Type: application/json' \
--data '{
    "FilteredColumns": [
        {
            "column": "hasExternalBarcode",
            "value": false
        },
        {
            "column": "isApproved",
            "value": true
        }
    ],
    "SelectedColumns": [
        "supplierId",
        "vendorCode",
        "merchantSku",
        "title",
        "olcubirimi",
        "vatRate",
        "sctRate",
        "listPrice",
        "salePrice"
    ],
    "Page": 1,
    "PageSize": 5
}'
]'
```
> Filtreleme sonucunda gelen ürün sayısı ve ürünlere ait özellikler gelir. Örnekteki response'da 1 ürün gelmiş ve 1 sayfa listelenmektedir.
> Ürün üzeirnde tutan bilgilerin yanı sıra, ürüne ait ID, Barkod, SKU, Option, Model kodları ve Type gelir. 

Response:
```json
[{
    "TotalPage": 1
    "TotalProduct": 1,
    "Products": [
        {
            "Columns": [
                {
                    "Column": "sctRate",
                    "Value": "8"
                },
                {
                    "Column": "vatRate",
                    "Value": "18"
                },
                {
                    "Column": "title",
                    "Value": "Regular Fit Normal Kesim  Gömlek"
                },
                {
                    "Column": "olcubirimi",
                    "Value": "KOL"
                },
                {
                    "Column": "merchantSku",
                    "Value": "s2"
                },
                {
                    "Column": "supplierId",
                    "Value": "47"
                },
                {
                    "Column": "vendorCode",
                    "Value": "TI"
                },
                {
                    "Column": "listPrice",
                    "Value": "0"
                },
                {
                    "Column": "salePrice",
                    "Value": "1"
                }
            ],
            "Id": 150,
            "Barcode": " GOMLEK10KRMZM",
            "Sku": " GOMLEK10KRMZM",
            "Option": "GOMLEK10",
            "Model": "GOMLEK",
            "Type": 3
   
}

]

```
