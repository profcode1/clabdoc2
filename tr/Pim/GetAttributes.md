# Ürün Özelliklerini Listeleme API Dökümantasyonu

## API Açıklaması

Bu API, veritabanındaki tüm ürün özelliklerini (attribute) listelemek için kullanılır.

## Endpoint 

```
https://pim_api_url/pim/GetAttributes
```

## Metod 

`GET`

## Authorization

Bu API, Bearer Token ile yetkilendirme kullanır. 

Örnek cURL komutu:
```bash
curl 'https://pim_api_url/pim/GetAttributes' 
  -H 'authorization: Bearer YOUR_ACCESS_TOKEN'
```

*Not: `YOUR_ACCESS_TOKEN` kısmını geçerli bir token ile değiştirmeyi unutmayın.*

## Yanıt Örneği

Aşağıda başarılı bir API çağrısının yanıt örneği verilmiştir.

```json
[
    {
        "AttributeId": 260,
        "AttributeName": "Renk",
        "AttributeDataTypeId": 2,
        "AttributeTypeId": 2,
        "AttributeRelationLevelId": 2,
        "AttributeBindingTypeId": 1,
        "AttributeDataType": "Text",
        "AttributeType": "Display Option",
        "AttributeRelationLevel": "Option",
        "AttributeBindingType": "Auto"
    },
    {
        "AttributeId": 267,
        "AttributeName": "Cinsiyet",
        "AttributeDataTypeId": 2,
        "AttributeTypeId": 2,
        "AttributeRelationLevelId": 2,
        "AttributeBindingTypeId": null,
        "AttributeDataType": "Text",
        "AttributeType": "Display Option",
        "AttributeRelationLevel": "Option",
        "AttributeBindingType": null
    },
    {
        "AttributeId": 269,
        "AttributeName": "Beden",
        "AttributeDataTypeId": 2,
        "AttributeTypeId": 1,
        "AttributeRelationLevelId": 1,
        "AttributeBindingTypeId": null,
        "AttributeDataType": "Text",
        "AttributeType": "Variant",
        "AttributeRelationLevel": "Variant",
        "AttributeBindingType": null
    }
]
```

## Alanlar 

### Çıktı Alanları

- **AttributeId** (integer): Özelliğin tekil tanımlayıcısı.
- **AttributeName** (string): Özelliğin ismi.
- **AttributeDataTypeId** (integer): Özelliğin veri tipinin ID'si.
- **AttributeTypeId** (integer): Özelliğin tipinin ID'si.
- **AttributeRelationLevelId** (integer): Özelliğin ilişki seviyesinin ID'si.
- **AttributeBindingTypeId** (integer/null): Özelliğin bağlama tipinin ID'si. Null olabilir.
- **AttributeDataType** (string): Özelliğin veri tipi.
- **AttributeType** (string): Özelliğin tipi.
- **AttributeRelationLevel** (string): Özelliğin ilişki seviyesi.
- **AttributeBindingType** (string/null): Özelliğin bağlama tipi. Null olabilir.

### Hata Yanıtları

Aşağıda, olası hata durumlarını ve bunların nasıl ele alınması gerektiğini gösteren genel bir rehber bulunmaktadır.

- **401 Unauthorized**: Doğrulanmamış erişim denemesi. Token'in geçerli olduğundan ve doğru olarak gönderildiğinden emin olun.
- **404 Not Found**: API endpoint’inin doğru olduğunu kontrol edin.
- **500 Internal Server Error**: Sunucu tarafındaki genel hata. Bu tür hataları yöneticinizle veya API sağlayıcınızla iletişime geçerek bildirin.

---

Bu dökümantasyon, API'nın genel kullanımını ve akışını özetlemektedir. Kullanan geliştiricilerin, uygulama geliştirmelerini bu bilgiler ışığında sürdürebilmeleri amaçlanmıştır. Daha fazla detay veya özel kullanım durumları için lütfen [API Dokümantasyonu](#) (eğer varsa ilgili linki buraya ekleyin) başvurunuz.
