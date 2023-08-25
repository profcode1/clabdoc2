# İade İsteği Yaratma İsteği API Dökümantasyonu

Bu dökümantasyon, iade isteği yaratma isteği API'sini açıklar. Bu API, iade işlemlerini oluşturmanıza olanak tanır.

## API Endpoint

API, aşağıdaki endpoint'i kullanır:

```plaintext
POST https://api.oms.prod.hebiar.com/Return/CreateReturnRequest
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
{
  "ChangeSource":"",
  "carrierCode": "MNG",
  "sourcePackageId": "BB_pid1692964770873",
  "returnPackageItems": [
    {
      "sourceOrderItemId": "item169296477056",
      "quantity": 1,
      "returnPackageItemLines": [
        {
          "sourceOrderItemLineId": "item169296477056-1",
          "reasonId": 151, 
          "reasonDesc": ""
        }
      ]
    }
  ]
}
```

- `ChangeSource`: Değişiklik kaynağı. (optional , boş bırakılabilir)
- `carrierCode`: taşıyıcı kodu. (optional. hiç gönderilmezse sistem uygun taşıyıcıyı seçecektir)
- `sourcePackageId`: Kaynak paket/teslimat kimliği.
- `returnPackageItems`: İade paketi kalemleri.
  - `sourceOrderItemId`: Kaynak sipariş kalemi kimliği.
  - `quantity`: İade edilecek ürün miktarı.
  - `returnPackageItemLines`: İade paketi kalemi satırları. (adet kadar olmalıdır. sourceOrderItemLineId tekil olmalıdır.)
    - `sourceOrderItemLineId`: Kaynak sipariş kalemi satırı kimliği. 
    - `reasonId`: İade sebebi kimliği. [reasonId bilgisini bu apiden alabilirsiniz](GetReasonsByStatus.md)
    - `reasonDesc`: İade sebebi açıklaması.

## İstek Örneği

Aşağıdaki örnek, API'ye istek yapmanın bir örneğini gösterir:

```bash
curl --location 'https://api.oms.prod.hebiar.com/Return/CreateReturnRequest' 
--header 'accept: text/plain' 
--header 'Authorization: Bearer ...loginden-alinan-token...' 
--header 'Content-Type: application/json' 
--data '{
  "ChangeSource":"",
  "carrierCode": "MNG",
  "sourcePackageId": "BB_pid1692964770873",
  "returnPackageItems": [
    {
      "sourceOrderItemId": "item169296477056",
      "quantity": 1,
      "returnPackageItemLines": [
        {
          "sourceOrderItemLineId": "item169296477056-1",
          "reasonId": 151,
          "reasonDesc": ""
        }
      ]
    }
  ]
}'
```

## Dönüş

API isteğine verilen dönüş aşağıdaki gibidir:

```json
{
    "isSuccess": true,
    "statusCode": null,
    "data": {
        "rmaCode": "DEFRMA",
        "carrierCode": "MNG"
    }
}
```

- `isSuccess`: İstek başarılı ise true, aksi halde false.
- `statusCode`: İstek durum kodu.
- `data`: Veri içeriği.
  - `rmaCode`: RMA kodu.
  - `carrierCode`: taşıyıcı(kargo) kodu.



## Hub Arayüz
- İade istekleri ilgili satıcının İade talepleri sayfasına düşmekte ve satıcı bunları onay yada reddederse operatöre webhook ([örneklere buradan ulaşabilirsiniz ](../WhatIsWebHook.md)) ile iletilmektedir.

![screenshoot](../../m/oms-hub-returnrequests.png)
    