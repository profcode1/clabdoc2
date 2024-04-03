
# SetErpInfoList

Bu servis, siparişlere ERP'de tutulan bilgileri set etmek için kullanılır. Linelarda ERP'de karşılık gelen ErpOrderItemLineId değerleri set edilir. 

## API İsteği

Aşağıdaki `curl` komutu ile API'ye istek yapabilirsiniz:

```bash
curl --location '{path_the_comlab_oms_api}/Orders/SetErpInfoList' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer [YourAccessToken]' \
--data '[
    {
        "SourceOrderNumber": "BBrae1705403307",
        "ErpOrderNumber": "ERPOMERV2",
        "ErpLines": [
            {
                "SourceOrderItemLineId": "item1705403307451-1",
                "ErpOrderItemLineId": "ERP001"
            },
            {
                "SourceOrderItemLineId": "item1705403307451-2",
                "ErpOrderItemLineId": "ERP002"
            }
        ]
    }
]'
```

### Parametreler

- `SourceOrderNumber`: ERP bilgilerinin set edileceği siparişin kaynak sipariş numarası (Zorunlu)
- `ErpOrderNumber`: ERP sipariş numarası (Zorunlu)
- `ErpLines`: ERP satır bilgileri
  - `SourceOrderItemLineId`: Siparişteki satırın kaynak satır numarası (Zorunlu)
  - `ErpOrderItemLineId`: ERP'deki karşılığı olan satır numarası (Zorunlu)

## API Yanıtı

Aşağıda API'nin örnek bir yanıtı yer almaktadır:

```json
{
  "isSuccess": true,
  "statusCode": "200",
  "errorMessage": null,
  "errorSource": null,
  "correlationId": "string",
  "errors": [
    {
      "code": "string",
      "message": "string"
    }
  ],
  "data": null
}
```

### Yanıt Alanları ve Açıklamaları

- `isSuccess`: İşlem başarılı mı?
- `statusCode`: Durum kodu
- `errorMessage`: Hata mesajı
- `errorSource`: Hata kaynağı
- `correlationId`: İlişkilendirme kimliği
- `errors`: Hatalar
  - `code`: Hata kodu
  - `message`: Hata mesajı
- `data`: İşlem verileri
