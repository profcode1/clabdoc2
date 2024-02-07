# SetOrderClientStatus

Bu dokümantasyon siparişlere client status eklemek için kullanılacak `setOrderClientStatus` metodunu açıklar.

## API Tanımı

Siparişleri çekerken kullanılacak olan filtre alanının güncellendiği servistir. Gönderilen key bu servis ile set edilir. Siparişler bu bilgiye göre filtrelenerek çekilir. Bu API ile işaretleme yapılan siparişler bir sonraki sipariş çekme isteğinde response’da dönmeyecektir.

## API Endpoint

PUT `https://api.oms.prod.hebiar.com/Orders/SetOrderClientStatus`

## API Yetkilendirmesi

Bu API'yi kullanabilmek için geçerli bir yetkilendirme belirteci (token) gereklidir. Yetkilendirme belirteci, 'Authorization' başlığı ile isteğe eklenmelidir.

## API İsteği

Aşağıdaki `curl` komutu ile API'ye istek yapabilirsiniz:

```bash
curl --location 'https://api.oms.prod.hebiar.com/Orders/SetOrderClientStatus' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer [YourAccessToken]' \
--data '[
    {
        "SourceOrderNumber": "BBptd1705406102",
        "Status": "Created",
        "Message": null
    }
]'
```

### Parametreler

- `SourceOrderNumber`: Güncellenecek siparişin kaynak sipariş numarası
- `Status`: Güncellenecek durum (örn: "Created")
- `Message`: İsteğe bağlı ek bilgi

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
