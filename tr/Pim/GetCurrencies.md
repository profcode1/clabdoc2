# A101 API Dökümantasyonu - Para Birimleri

Bu dökümantasyon, A101 API'sinin "Para Birimleri" endpoint'ini tanımlar. Bu API, farklı para birimleri hakkında bilgi almak için kullanılır.

## API Endpoint Bilgisi

API'nin temel URL'i: `https://stgapi.a101.prod.hebiar.com/PIM/GetCurrencies`

## Kullanılacak HTTP Metodu

API, `GET` HTTP metodu kullanılarak çağrılmalıdır.

## Örnek bir cURL Komutu

Aşağıda, API'yi çağırmak için kullanabileceğiniz örnek bir cURL komutu bulunmaktadır:

```plaintext
curl "https://pim_url/PIM/GetCurrencies" 
  -H 'authorization: Bearer token'
```

## Örnek Bir API Yanıtı

API isteği sonucunda alınabilecek örnek bir JSON formatındaki yanıt aşağıda verilmiştir:

```json
[
    {
        "Id": 1,
        "Code": "TRY",
        "Description": "Türk Lirası"
    },
    {
        "Id": 2,
        "Code": "USD",
        "Description": "Amerikan Doları"
    },
    {
        "Id": 3,
        "Code": "EUR",
        "Description": "Euro"
    }
]
```

## Yanıttaki Alanların Açıklamaları

- `Id`: Para biriminin benzersiz kimliğini temsil eder.
- `Code`: Para biriminin kodunu (örneğin, "TRY" for Türk Lirası) içerir.
- `Description`: Para biriminin açıklamasını içerir (örneğin, "Türk Lirası" veya "Amerikan Doları").

## Olası Hata Mesajları ve Açıklamaları

- **401 Unauthorized**: Yetkilendirme hatası. Geçersiz veya eksik bir yetkilendirme belirtilmiş olabilir. Doğru bir erişim belirteci (Bearer token) sağlandığından emin olun.
- **404 Not Found**: Belirtilen endpoint bulunamadı. Lütfen doğru API endpoint'ini kontrol edin.
- **500 Internal Server Error**: Sunucu hatası. Sunucu tarafında bir sorun oluştu. Bu durumu API sağlayıcınıza bildirmeniz gerekebilir.
```

Yukarıdaki dökümantasyon, istediğiniz bilgileri içeren kopyalanabilir bir kod bloğunda sunulmuştur.
