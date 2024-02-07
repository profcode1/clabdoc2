# SetOrderPackageInvoiceInfoList

Bu servis, sipariş paketlerine fatura bilgilerini atamak için kullanılır. Paketin statüsü Picked veya Invoiced olmalıdır.

## API Tanımı

MCC’nin paketlere fatura bilgilerini set ederken kullanacağı servistir. Paket statüsünün Picked veya Invoiced olması gereklidir.

## API Endpoint

PUT `https://api.oms.prod.hebiar.com/OrderPackage/SetOrderPackageInvoiceInfoList`

## API Yetkilendirmesi

Bu API'yi kullanabilmek için geçerli bir yetkilendirme belirteci (token) gereklidir. Yetkilendirme belirteci, 'Authorization' başlığı ile isteğe eklenmelidir.

## API İsteği

Aşağıdaki `curl` komutu ile API'ye istek yapabilirsiniz:

```bash
curl --location 'https://api.oms.prod.hebiar.com/OrderPackage/SetOrderPackageInvoiceInfoList' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer [YourAccessToken]' \
--data '[
    {
        "SourcePackageId": "BB_pid1705672220960",
        "InvoiceNumber": "789456",
        "InvoiceLink": "https://invoicelink.com/BB_pid1705672220960"
    }
]'
```

### Parametreler

- `SourcePackageId`: Fatura bilgilerinin atanacağı paketin kaynak paket numarası (Zorunlu)
- `InvoiceNumber`: Fatura numarası (Zorunlu)
- `InvoiceLink`: Fatura bağlantısı (Zorunlu)

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
