# İptal İsteği Onaylama Durumu Bildirim Web Hook Örneği

Bu dökümantasyon, İptal isteğinin satıcı tarafından onaylandığı senaryo için Web Hook örneğini açıklar. Bu Web Hook, İptal İsteği durumu ilgili bilgileri almanıza olanak tanır.

## Web Hook Endpoint

Web Hook, aşağıdaki endpoint'i kullanır:

```plaintext
POST https://api.oms.prod.hebiar.com/SampleWebHooks/PackageWebHook_Successsample
```

## İstek Başlıkları

- `accept`: İstekte kabul edilebilir medya türünü belirtir (örn. \*/\*).
- `Content-Type`: İstekte gönderilen içeriğin medya türünü belirtir (örn. application/json).

## İstek Verileri

Aşağıdaki örnek, Web Hook'a gönderilecek istek verilerini gösterir:

```json
{
  "hookName": "CancelOrderItemLineConfirmedEvent",
  "packageId": "BB_pid1692966394724",
  "packageType": "ShipToCustomer",
  "items": [
    {
      "orderItemLineId": "item1692966394138-2",
      "packageItemStatusId": 1302,
      "packageItemStatusName": "Cancelled",      
    }
  ],
  "packageStatusId": 1302,
  "packageStatusName": "Cancelled"  
}
```

- `hookName`: Web Hook olay adı.
- `packageId`: Paket kimliği.
- `packageType`: Paket türü. (ShipToCustomer=0,Return=1)
- `items`: Paket içindeki ürünlerin durum bilgileri.
- `packageStatusId`: Paket durum kimliği.
- `packageStatusName`: Paket durum adı.

## İstek Örneği

Aşağıdaki örnek, Web Hook'a istek yapmanın bir örneğini gösterir:

```bash
curl --location 'https://api.oms.prod.hebiar.com/SampleWebHooks/PackageWebHook_Successsample' 
--header 'accept: */*' 
--header 'Content-Type: application/json' 
--data '{
  "hookName": "CancelOrderItemLineConfirmedEvent",
  "packageId": "BB_pid1692966394724",
  "packageType": "ShipToCustomer",
  "items": [
    {
      "orderItemLineId": "item1692966394138-2",
      "packageItemStatusId": 1302,
      "packageItemStatusName": "Cancelled",      
    }
  ],
  "packageStatusId": 1302,
  "packageStatusName": "Cancelled"  
}'
```

## Dönüş

Web Hook isteğine verilen dönüş HTTP değeri aşağıdaki gibidir:

```plaintext
200 OK
```
