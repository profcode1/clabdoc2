# SetPackageClientStatus

Bu API, sipariş paketinin istemci tarafından belirlenen durumunu güncellemek için kullanılır.

## API Tanımı

MCC’nin paketleri çekerken kullanacağı filtre alanının set edildiği servis denilebilir. Gönderilen key bu alana set edilir. GetOrderPackages ile filtreye eklenerek istenilen paketler filtreli bir şekilde çekilir.

## API Endpoint

PUT `{path_the_comlab_oms_api}/OrderPackage/SetPackageClientStatus`

## API Yetkilendirmesi

Bu API'yi kullanabilmek için geçerli bir yetkilendirme belirteci (token) gereklidir. Yetkilendirme belirteci, 'Authorization' başlığı ile isteğe eklenmelidir.

## API İsteği

Aşağıdaki `curl` komutu ile API'ye istek yapabilirsiniz:

```bash
curl --location '{path_the_comlab_oms_api}/OrderPackage/SetPackageClientStatus' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer [YourAccessToken]' \
--data '[
    {
        "SourcePackageId": "BB_pid1705406102308",
        "Status": "Created",
        "Message": null
    }
]'
```

### Parametreler

- `SourcePackageId`: Güncellenecek sipariş paketinin kaynak paket numarası (Zorunlu)
- `Status`: Güncellenecek durum (örn: "Created") (Zorunlu)
- `Message`: İsteğe bağlı ek bilgi (Zorunlu Değil)

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
