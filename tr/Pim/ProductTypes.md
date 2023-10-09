# PIM Ürün Tipleri API Dökümantasyonu

Bu dökümantasyon, PIM (Product Information Management) sistemi tarafından sunulan "Ürün Tipleri" API'sini tanımlar. Bu API, ürün tipleri hakkında bilgi almak için kullanılır.

## API Endpoint Bilgisi

API'nin temel URL'i: `https://pim_url/PIM/LookUp/ProductTypes`

## Kullanılacak HTTP Metodu

API, `GET` HTTP metodu kullanılarak çağrılmalıdır.

## Örnek bir cURL Komutu

Aşağıda, API'yi çağırmak için kullanabileceğiniz örnek bir cURL komutu bulunmaktadır:

```
curl 'https://pim_url/PIM/LookUp/ProductTypes' 
  -H 'authorization: Bearer token'
```

## Örnek bir API Yanıtı

API isteği sonucunda alınabilecek örnek bir JSON formatındaki yanıt aşağıda verilmiştir:

```json
{    
    "Data": [
        {
            "Id": 1,
            "Name": "Model",
            "Salable": false,
            "Listable": false
        },
        {
            "Id": 2,
            "Name": "Option",
            "Salable": false,
            "Listable": true
        },
        {
            "Id": 3,
            "Name": "Sku/Variant",
            "Salable": true,
            "Listable": false
        },
        {
            "Id": 4,
            "Name": "Single",
            "Salable": true,
            "Listable": true
        },
        {
            "Id": 5,
            "Name": "Bundle",
            "Salable": true,
            "Listable": true
        },
        {
            "Id": 6,
            "Name": "Combine",
            "Salable": false,
            "Listable": true
        }
    ]
}
```

## Yanıttaki Alanların Açıklamaları

- `Data`: API yanıtının ana veri nesnesidir ve ürün tiplerini içerir.
- `Id`: Ürün tipinin benzersiz kimliğini temsil eder.
- `Name`: Ürün tipinin adını içerir.
- `Salable`: Ürün tipinin satılabilir olup olmadığını belirten bir değerdir (true/false).
- `Listable`: Ürün tipinin listelenebilir olup olmadığını belirten bir değerdir (true/false).
```
