## API Dokümantasyonu

### Endpoint

`POST {path_the_comlab_oms_api}/OrderPackage/shipment-packages/{packageId}/quantity-split`

### Amaç

Bu API çağrısı, belirli bir paketin içinde bulunan ürün kalemlerini `Quantities` alanındaki adetlere göre paketlere böler.

### İstek Parametreleri

| Parametre      | Açıklama                            | Tür     | Gerekli |
|----------------|-------------------------------------|---------|---------|
| packageId      | Paket kimlik numarası              | Dize    | Evet    |
| QuantitySplit  | Bölünmek istenen gruplar            | Dizi    | Evet    |
| OrderLineId    | Sipariş kalemi kimlik numarası     | Tamsayı | Evet    |
| Quantities     | Paketlenmek istenen ürün miktarları | Dizi    | Evet    |

### Örnek İstek

```json
{
    "QuantitySplit": [
        {
            "OrderLineId": 328937,
            "Quantities": [ 5, 7, 2, 6] 
        },
        {
            "OrderLineId": 328938,
            "Quantities": [ 5, 7, 2, 6]
        }
    ]
}
```

### Örnek Yanıt

Başarılı bir istek durumunda, API aşağıdaki gibi bir yanıt döndürecektir:

```json
{
  "status": "success",
  "message": "Ürünler istenen adetlere göre paketlere bölündü."
}
```

### Hata Durumu

Hata durumunda, API aşağıdaki gibi bir yanıt döndürecektir:

```json
{
  "status": "error",
  "message": "Hata: Geçersiz istek."
}
```

### Notlar

- `OrderLineId`: Sipariş kalemi kimlik numarası, ilgili ürünü temsil eder.
- `Quantities`: Paketlenmek istenen ürün miktarları, her bir miktarın bir paket oluşturulmasını sağlar.

