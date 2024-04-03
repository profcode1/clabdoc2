# Paket/Teslimat Durum Bildirimleri Web Hook Örneği

Bu dökümantasyon, paket/teslimat durum bildirimleri için Web Hook örneğini açıklar. Bu Web Hook örneği, teslimat durumuyla ilgili bilgileri almanıza olanak tanır. Örneğin Picked , Shipped , Delivered , Cancelled gibi durumları tarafınıza detaylarıyla iletir.

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
  "hookName": "OrderPackageStatusChangedEvent",
  "packageId": "BB_pid1692966394724",
  "packageType": "ShipToCustomer",
  "items": [
    {
      "orderItemLineId": "item1692966394138-2",
      "packageItemStatusId": 1308,
      "packageItemStatusName": "Shipped"     
    }
  ],
  "packageStatusId": 1308,
  "packageStatusName": "Shipped",
  "cargoCompanyName": "MNG",
  "cargoKey": "CargoKey",
  "cargoTrackingUrl": "https://cargotrackingurl.com",
  "estimatedDate": "2023-08-25T12:52:32.533Z"
}
```

- `hookName`: Web Hook olay adı.
- `packageId`: Paket kimliği.
- `packageType`: Paket türü. (ShipToCustomer=0,Return=1)
- `items`: Paket içindeki ürünlerin durum bilgileri.
- `packageStatusId`: Paket durum kimliği.
- `packageStatusName`: Paket durum adı.
- `cargoCompanyName`: Kargo firması adı.
- `cargoKey`: Kargo anahtarı.
- `cargoTrackingUrl`: Kargo takip URL'i.
- `estimatedDate`: Tahmini tarih.

## İstek Örneği

Aşağıdaki örnek, Web Hook'a istek yapmanın bir örneğini gösterir:

```bash
curl --location '{path_the_comlab_oms_api}/SampleWebHooks/PackageWebHook_Successsample' 
--header 'accept: */*' 
--header 'Content-Type: application/json' 
--data '{
  "hookName": "OrderPackageStatusChangedEvent",
  "packageId": "BB_pid1692966394724",
  "packageType": "ShipToCustomer",
  "items": [
    {
      "orderItemLineId": "item1692966394138-2",
      "packageItemStatusId": 1308,
      "packageItemStatusName": "Shipped"     
    }
  ],
  "packageStatusId": 1308,
  "packageStatusName": "Shipped",
  "cargoCompanyName": "MNG",
  "cargoKey": "CargoKey",
  "cargoTrackingUrl": "https://cargotrackingurl.com",
  "estimatedDate": "2023-08-25T12:52:32.533Z"
}'
```

## Dönüş

Web Hook isteğine verilen dönüş HTTP değeri aşağıdaki gibidir:

```plaintext
200 OK
```
