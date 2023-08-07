# Durum Sebepleri API Dökümantasyonu

Bu dökümantasyon, ürün iptal sebepleri ile ilgili API'yi açıklar. Bu API, örneğin ürün iptal sebeplerini almanıza ve diğer işlemlerde kullanmanıza olanak tanır.

## API Endpoint

API, aşağıdaki endpoint'i kullanır:

```plaintext
GET https://api.oms.prod.hebiar.com/Lookup/OrderStatusReasonByTenant/GetStatusReasonByType?statusType=Cancelled
```

## Yetkilendirme

API'ye erişim sağlamak için aşağıdaki yetkilendirme başlığını kullanmanız gerekmektedir:

```
authorization: Bearer ... 
```

## İstek Parametreleri

- `statusType` (zorunlu): İptal durumu tipini belirtir (örn. "Cancelled").

## İstek Örneği

Aşağıdaki örnek, API'ye istek yapmanın bir örneğini gösterir:

```bash
curl --location 'https://api.oms.prod.hebiar.com/Lookup/OrderStatusReasonByTenant/GetStatusReasonByType?statusType=Cancelled' 
--header 'authorization: Bearer ... '
```

## Cevap

API isteğine verilen cevap aşağıdaki gibi olacaktır:

```json
[
    {
        "orderStatusReasonId": 1,
        "orderStatusReason": null,
        "reasonName": "Stok yok",
        "id": 135,
        "createdAt": "2023-05-25T19:56:19.489+03:00"
    },
    {
        "orderStatusReasonId": 2,
        "orderStatusReason": null,
        "reasonName": "Müşteri isteği",
        "id": 136,
        "createdAt": "2023-05-25T19:56:19.489+03:00"
    }
```

Her bir nesne aşağıdaki alanları içerir:

- `orderStatusReasonId`: Ürün iptal sebebi kimliği.
- `orderStatusReason`: İptal sebebi açıklaması.
- `reasonName`: İptal sebebinin adı.
- `id`: Kimlik numarası.

Bu cevap içerisinden alınan `id` değerini diğer API isteklerinde kullanabilirsiniz.

## Daha Fazla Bilgi

Bu API'nin döndürdüğü `id` değerini diğer API isteklerinde kullanabilirsiniz.

## Destek

Herhangi bir sorunuz varsa [destek@hebiar.com](mailto:destek@hebiar.com) adresine e-posta gönderebilirsiniz.
    