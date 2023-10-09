# Stok Güncelleme API Dökümantasyonu

Bu dökümantasyon, Stok Güncelleme API'sini kullanmak için gereken bilgileri içerir.

## API Tanımı

Stok bilgilerini güncellemek için kullanılan bir API'dir. Bu API, SKU (Stok Tutma Birimi) kimlikleri, güncellenecek stok miktarları ve depo kodlarını kabul eder.

## API Endpoint

PUT `https://api.oms.prod.hebiar.com/Inventory/UpdateInventory`

## API Yetkilendirmesi

Bu API'yi kullanabilmek için geçerli bir yetkilendirme belirteci (token) gereklidir. Yetkilendirme belirteci, 'Authorization' başlığı ile isteğe eklenmelidir.

## API İsteği

Aşağıdaki cURL komutunu ve başlıkları kullanarak API isteği yapabilirsiniz:

```bash
curl --location --request PUT 'https://api.oms.prod.hebiar.com/Inventory/UpdateInventory' 
--header 'Authorization: Bearer token' 
--header 'Content-Type: application/json' 
--data '[
    {
        "Sku": "194880975692",
        "Qty": 50,
        "StorageCode": "L011"
    },
    {
        "Sku": "194880975693",
        "Qty": 60,
        "StorageCode": "L011"
    },
    {
        "Sku": "194880975694",
        "Qty": 50,
        "StorageCode": "L011"
    }
]'
```

## API İsteği Body Parametreleri

API isteği gövdesinde (body) aşağıdaki parametreler kullanılmalıdır:

- `Sku`: SKU (Stok Tutma Birimi) kimliği.
- `Qty`: Güncellenecek stok miktarı.
- `StorageCode`: Depo kodu.

Örnek bir API isteği gövdesi:

```json
[
    {
        "Sku": "194880975692",
        "Qty": 50,
        "StorageCode": "L011"
    },
    {
        "Sku": "194880975693",
        "Qty": 60,
        "StorageCode": "L011"
    },
    {
        "Sku": "194880975694",
        "Qty": 50,
        "StorageCode": "L011"
    }
]