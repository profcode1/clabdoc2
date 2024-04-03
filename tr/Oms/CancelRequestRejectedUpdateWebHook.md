# İptal İsteği Red Durumu Bildirim Web Hook Örneği

Bu dökümantasyon, İptal isteğinin satıcı tarafından reddedildiği senaryo için Web Hook örneğini açıklar. Bu Web Hook, İptal İsteği durumu ilgili bilgileri almanıza olanak tanır.

## Web Hook Endpoint

Web Hook, aşağıdaki endpoint'i kullanır:

```plaintext
POST {path_the_comlab_oms_api}/SampleWebHooks/PackageWebHook_Successsample
```

## İstek Başlıkları

- `accept`: İstekte kabul edilebilir medya türünü belirtir (örn. \*/\*).
- `Content-Type`: İstekte gönderilen içeriğin medya türünü belirtir (örn. application/json).

## İstek Verileri

Aşağıdaki örnek, Web Hook'a gönderilecek istek verilerini gösterir:

```json
{
  "hookName": "CancelOrderItemLineRejectedEvent",
  "packageId": "BB_pid1692966394724",
  "packageType": "ShipToCustomer",
  "items": [
    {
      "orderItemLineId": "item1692966394138-2",
      "packageItemStatusId": 1324,
      "packageItemStatusName": "CancelRequestDenied",
      "packageItemStatusReasonId": 168,
      "packageItemStatusReasonName":  "Gönderi Yola Çıktı",
      "packageItemStatusReasonDesc": ""
    }
  ],
  "packageStatusId": 1324,
  "packageStatusName": "CancelRequestDenied",
  "packageStatusReasonId": 168,
  "packageStatusReasonName": "Gönderi Yola Çıktı",
  "packageStatusReasonDesc": "",  
}
```

- `hookName`: Web Hook olay adı.
- `packageId`: Paket kimliği.
- `packageType`: Paket türü. (ShipToCustomer=0,Return=1)
- `items`: Paket içindeki ürünlerin durum bilgileri.
- `packageStatusId`: Paket durum kimliği.
- `packageStatusName`: Paket durum adı.
- `packageStatusReasonId`: Paket durum sebep kimliği. [reasonId bilgisini bu apiden alabilirsiniz](GetReasonsByStatus.md)
- `packageStatusReasonName`: Paket durum sebep adı.
- `packageStatusReasonDesc`: Paket durum sebep açıklaması.

## İstek Örneği

Aşağıdaki örnek, Web Hook'a istek yapmanın bir örneğini gösterir:

```bash
curl --location '{path_the_comlab_oms_api}SampleWebHooks/PackageWebHook_Successsample' 
--header 'accept: */*' 
--header 'Content-Type: application/json' 
--data '{
  "hookName": "CancelOrderItemLineRejectedEvent",
  "packageId": "BB_pid1692966394724",
  "packageType": "ShipToCustomer",
  "items": [
    {
      "orderItemLineId": "item1692966394138-2",
      "packageItemStatusId": 1324,
      "packageItemStatusName": "CancelRequestDenied",
      "packageItemStatusReasonId": 168,
      "packageItemStatusReasonName":  "Gönderi Yola Çıktı",
      "packageItemStatusReasonDesc": ""
    }
  ],
  "packageStatusId": 1324,
  "packageStatusName": "CancelRequestDenied",
  "packageStatusReasonId": 168,
  "packageStatusReasonName": "Gönderi Yola Çıktı",
  "packageStatusReasonDesc": "",  
}'
```

## Dönüş

Web Hook isteğine verilen dönüş HTTP değeri aşağıdaki gibidir:

```plaintext
200 OK
```
