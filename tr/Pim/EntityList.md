# API Dökümantasyonu - Entity List

Bu dökümantasyon, Entity List API'sini tanımlar. Bu API, varlıkların listesini almak için kullanılır.

## API Endpoint Bilgisi

API'nin temel URL'i: `https://pim_url/PIM/Entity/List`

## Kullanılacak HTTP Metodu

API, `GET` HTTP metodu kullanılarak çağrılmalıdır.

## Örnek bir cURL Komutu

Aşağıda, API'yi çağırmak için kullanabileceğiniz örnek bir cURL komutu bulunmaktadır:

```plaintext
curl 'https://pim_url/PIM/Entity/List' 
  -H 'authorization: Bearer token'
```

## Örnek Bir API Yanıtı

API isteği sonucunda alınabilecek örnek bir JSON formatındaki yanıt aşağıda verilmiştir:

```json
{
    "IsSuccess": true,
    "ErrorType": null,
    "ErrorMessage": null,
    "ErrorSource": "Commercelab",
    "Data": [
        {
            "Id": 4,
            "Name": "Default Content",
            "EntityTypeId": 8
        },
        {
            "Id": 5,
            "Name": "France Content",
            "EntityTypeId": 8
        },
        {
            "Id": 7,
            "Name": "Default Price List",
            "EntityTypeId": 4
        },		
        {
            "Id": 17,
            "Name": "France Price List",
            "EntityTypeId": 4
        },
        {
            "Id": 8,
            "Name": "Default Asset List",
            "EntityTypeId": 7
        },
        {
            "Id": 18,
            "Name": "Mobile Asset List",
            "EntityTypeId": 7
        },
        {
            "Id": 10,
            "Name": "Default Product List",
            "EntityTypeId": 5
        },
        {
            "Id": 13,
            "Name": "Default Warehouse Group",
            "EntityTypeId": 6
        },
        {
            "Id": 21,
            "Name": "Market Place Warehouse Group",
            "EntityTypeId": 6
        }
    ]
}
```

EntityTypeId aşağıdakiler sabittir. çıktıdan sadece fiyat listelerini alacağınız zaman sadece tipi 4 olanları almalısınız.
```
3	CategoryTree   
4	PriceList 
5	ProductList
6	WarehouseGroup
7	Asset
8	Content
11	IntegrationAttribute
13	Attribute
````


## Yanıttaki Alanların Açıklamaları

- `IsSuccess`: API isteğinin başarılı olup olmadığını belirten bir değerdir (true/false).
- `ErrorType`: Hata türünü içerir (varsa).
- `ErrorMessage`: Hata mesajını içerir (varsa).
- `ErrorSource`: Hatanın kaynağını içerir (varsa).
