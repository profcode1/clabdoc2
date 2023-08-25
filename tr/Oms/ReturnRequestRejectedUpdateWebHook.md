# İade Paketi Red Durumu Bildirim Web Hook Örneği

Bu dökümantasyon, iade isteğinin satıcı tarafından reddedildiği senaryo için Web Hook örneğini açıklar. Bu Web Hook, iadenin durumu ilgili bilgileri almanıza olanak tanır.

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
  "hookName": "ReturnOrderPackageRejectedEvent",
  "packageId": "BB_pid1692966394724",
  "packageType": "Return",
  "items": [
    {
      "orderItemLineId": "item1692966394138-2",
      "packageItemStatusId": 1305,
      "packageItemStatusName": "ReturnedRequestDenied",
      "packageItemStatusReasonId": 167,
      "packageItemStatusReasonName":  "Eksik Ürün",
      "packageItemStatusReasonDesc": "Kutunun içinden belirtilen ürün çıkmadı"
    }
  ],
  "packageStatusId": 1305,
  "packageStatusName": "ReturnedRequestDenied",
  "packageStatusReasonId": 167,
  "packageStatusReasonName": "Eksik Ürün",
  "packageStatusReasonDesc": "Kutunun içinden belirtilen ürün çıkmadı",  
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
- `cargoCompanyName`: Kargo firması adı.
- `cargoKey`: Kargo anahtarı.
- `cargoTrackingUrl`: Kargo takip URL'i.
- `estimatedDate`: Tahmini tarih.

## İstek Örneği

Aşağıdaki örnek, Web Hook'a istek yapmanın bir örneğini gösterir:

```bash
curl --location 'https://api.oms.prod.hebiar.com/SampleWebHooks/PackageWebHook_Successsample' 
--header 'accept: */*' 
--header 'Content-Type: application/json' 
--data '{
  "hookName": "ReturnOrderPackageRejectedEvent",
  "packageId": "BB_pid1692966394724",
  "packageType": "Return",
  "items": [
    {
      "orderItemLineId": "item1692966394138-2",
      "packageItemStatusId": 1305,
      "packageItemStatusName": "ReturnedRequestDenied",
      "packageItemStatusReasonId": 167,
      "packageItemStatusReasonName":  "Eksik Ürün",
      "packageItemStatusReasonDesc": "Kutunun içinden belirtilen ürün çıkmadı"
    }
  ],
  "packageStatusId": 1305,
  "packageStatusName": "ReturnedRequestDenied",
  "packageStatusReasonId": 167,
  "packageStatusReasonName": "Eksik Ürün",
  "packageStatusReasonDesc": "Kutunun içinden belirtilen ürün çıkmadı",  
}'
```

## Dönüş

Web Hook isteğine verilen dönüş HTTP değeri aşağıdaki gibidir:

```plaintext
200 OK
```
