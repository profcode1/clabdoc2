# İptal Edilen Sipariş Kalemini Bildirme API Dökümantasyonu

Bu dökümantasyon, iptal edilen sipariş kalemini bildirme isteği API'sini açıklar. Bu API, iptal edilen sipariş kalemlerini bildirmenize olanak tanır.

## API Endpoint

API, aşağıdaki endpoint'i kullanır:

```plaintext
POST https://api.oms.prod.hebiar.com/Orders/CancelOrderItemLineList
```

## Yetkilendirme

API'ye erişim sağlamak için aşağıdaki yetkilendirme başlığını kullanmanız gerekmektedir:

```
Authorization: Bearer ...loginden-alinan-token...
```

## İstek Başlıkları

- `accept`: İstekte kabul edilebilir medya türünü belirtir (örn. text/plain).
- `Content-Type`: İstekte gönderilen içeriğin medya türünü belirtir (örn. application/json).

## İstek Verileri

Aşağıdaki örnek, API'ye gönderilecek istek verilerini gösterir:

```json
[
  {
    "sourceOrderItemLineId": "item1692969767920-1",
    "quantity": 1,
    "reasonId": 151,
    "reasonDesc": "Vazgeçtim"
  },
  {
    "sourceOrderItemLineId": "item1692969767920-2",
    "quantity": 1,
    "reasonId": 151,
    "reasonDesc": "Vazgeçtim"
  }
]
```

- `sourceOrderItemLineId`: Kaynak sipariş kalemi satırı kimliği.
- `quantity`: İptal edilen ürün miktarı.
- `reasonId`: İptal sebebi kimliği. > [reasonId bilgisini bu apiden alabilirsiniz](GetReasonsByStatus.md)
- `reasonDesc`: İptal sebebi açıklaması.

## İstek Örneği

Aşağıdaki örnek, API'ye istek yapmanın bir örneğini gösterir:

```bash
curl --location 'https://api.oms.prod.hebiar.com/Orders/CancelOrderItemLineList' 
--header 'accept: text/plain' 
--header 'Authorization: Bearer ...loginden-alinan-token...' 
--header 'Content-Type: application/json' 
--data '[
  {
    "sourceOrderItemLineId": "item1692969767920-1",
    "quantity": 1,
    "reasonId": 151,
    "reasonDesc": "Vazgeçtim"
  },
  {
    "sourceOrderItemLineId": "item1692969767920-2",
    "quantity": 1,
    "reasonId": 151,
    "reasonDesc": "Vazgeçtim"
  }
]'
```

## Dönüş

API isteğine verilen dönüş aşağıdaki gibidir:

```json
{
    "isSuccess": true,
    "statusCode": 0
}
```

- `isSuccess`: İstek başarılı ise true, aksi halde false.
- `statusCode`: İstek durum kodu.
