# İade Paketi Onay Durumu Bildirim Web Hook Örneği

Bu dökümantasyon, iade isteğinin satıcı tarafından onaylandığı senaryo için Web Hook örneğini açıklar. Bu Web Hook, iadenin durumu ilgili bilgileri almanıza olanak tanır.

## Web Hook Endpoint

Web Hook, aşağıdaki endpoint'i kullanır:

```plaintext
POST {path_the_comlab_oms_api}SampleWebHooks/PackageWebHook_Successsample
```

## İstek Başlıkları

- `accept`: İstekte kabul edilebilir medya türünü belirtir (örn. \*/\*).
- `Content-Type`: İstekte gönderilen içeriğin medya türünü belirtir (örn. application/json).

## İstek Verileri

Aşağıdaki örnek, Web Hook'a gönderilecek istek verilerini gösterir:

```json
{
  "hookName": "ReturnOrderPackageConfirmedEvent",
  "packageId": "BB_pid1692966394724",
  "packageType": "Return",
  "items": [
    {
      "orderItemLineId": "item1692966394138-2",
      "packageItemStatusId": 1318,
      "packageItemStatusName": "Returned",      
    }
  ],
  "packageStatusId": 1318,
  "packageStatusName": "Returned",  
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
curl --location '{path_the_comlab_oms_api}/SampleWebHooks/PackageWebHook_Successsample' 
--header 'accept: */*' 
--header 'Content-Type: application/json' 
--data '{
  "hookName": "ReturnOrderPackageConfirmedEvent",
  "packageId": "BB_pid1692966394724",
  "packageType": "Return",
  "items": [
    {
      "orderItemLineId": "item1692966394138-2",
      "packageItemStatusId": 1318,
      "packageItemStatusName": "Returned",      
    }
  ],
  "packageStatusId": 1318,
  "packageStatusName": "Returned",  
}'
```

## Dönüş

Web Hook isteğine verilen dönüş HTTP değeri aşağıdaki gibidir:

```plaintext
200 OK
```
