# SetOrderPackageCargoInfoList

Sipariş paketlerine kargo bilgilerini set etme servisi MCC’nin paketlere kargo bilgilerinin set ederken kullandığı servistir. Statüyü set edilebilmesi için paketin Picked veya Invoiced olması gerekir.

## API Endpoint

POST `https://api.oms.prod.hebiar.com/OrderPackage/SetOrderPackageCargoInfoList`

## Body

```json
[
    {
        "SourcePackageId": "BB_pid1705672220960", // Zorunlu
        "CargoKey": "CRGKEY",
        "CargoBarcode": "324513451234",
        "TrackingNumber": "TRACKINGNUMBER",
        "TrackingUrl": "https://trackinglink.com/BB_pid1705672220960"
    }
]
```

### Parametreler

- `SourcePackageId`: Kargo bilgilerinin atanacağı paketin kaynak paket numarası (Zorunlu)
- `CargoKey`: Kargo anahtarı
- `CargoBarcode`: Kargo barkodu
- `TrackingNumber`: Takip numarası
- `TrackingUrl`: Takip bağlantısı

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
