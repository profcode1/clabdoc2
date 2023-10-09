# Ürün Fiyat Güncelleme Api

Bu belge, PIM (Product Information Management) sistemine ürünlerin fiyatlarını güncellemek için kullanılan bir API isteğini açıklamaktadır.

## API İsteği

Aşağıda, bu API isteğini göndermek için kullanılan cURL komutunu bulabilirsiniz:

```shell
curl --location '{{pim_api_url}}/pim/SaveProductsManually?companyId=8' 
--header 'Authorization: Bearer token' 
--header 'Content-Type: application/json' 
--data '[
    {
        "Main": {
            "Option": "TestAyakkabiiso3KIRMIZI",
            "Model": "TestAyakkabiiso3",
            "Type": 2
        },
       
        "Prices": [
            {
                "IsTransferable": false,
                "EntityListId": 7,
                "CurrencyId": 1,
                "ListPrice": 800,
                "SalePrice": 600,
                "OperationType": "upsert"                
            }
        ]
    }
]'
```

## Açıklamalar

- `pim_api_url`: Bu kısmı, API'nin gerçek URL'si ile değiştirmeniz gerekmektedir.
- `Authorization: Bearer token`: API isteğini kimlik doğrulama amacıyla kullanılan bir yetkilendirme belirteci (token) ile gönderir. "token" kısmını gerçek bir yetkilendirme belirteci ile değiştirmeniz gerekmektedir.
- `Content-Type: application/json`: Gönderilen verilerin JSON formatında olduğunu belirten başlık.


## JSON Verileri ve Açıklamaları

İşte API isteğinde kullanılan JSON verileri ve her bir özelliğin detaylı açıklamaları:

- `Main`: Ürünün ana bilgilerini içeren bölüm.

    - `Option`: Ürünün seçeneğini temsil eder, örneğin, "TestAyakkabiiso3KIRMIZI".
    - `Model`: Ürünün modelini temsil eder, örneğin, "TestAyakkabiiso3".
    - `Type`: Ürünün türünü temsil eder, örneğin, "2".

- `Prices`: Ürünün fiyat bilgilerini içeren bölüm.

    - `IsTransferable`: Fiyatların transfer edilebilir olup olmadığını belirtir, bu örnek için "false".
    - `EntityListId`: Fiyatların ait olduğu liste kimliğini temsil eder, bu örnek için "7".
    - `CurrencyId`: Kullanılan para biriminin kimliğini temsil eder, bu örnek için "1".
    - `ListPrice`: Ürünün liste fiyatını temsil eder, bu örnek için "800".
    - `SalePrice`: Ürünün satış fiyatını temsil eder, bu örnek için "600".
    - `OperationType`: Fiyat işlem türünü temsil eder, bu örnek için "upsert".

    