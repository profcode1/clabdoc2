## API Dokümantasyonu

### Endpoint

`POST {path_the_comlab_oms_api}/OrderPackage/shipment-packages/{packageId}/split`

### Amaç

Bu API çağrısı, belirli bir pakette bulunan ürün kalemlerini farklı paketlere böler.

### İstek Parametreleri

| Parametre      | Açıklama                            | Tür     | Gerekli |
|----------------|-------------------------------------|---------|---------|
| packageId      | Paket kimlik numarası              | Dize    | Evet    |
| OrderLineIds   | Bölünmek istenen sipariş kalemi kimlik numaraları | Dizi | Evet    |

### Örnek İstek

```json
{
    "OrderLineIds":[
        328931,
        328930
    ]
}
```

### Örnek Yanıt

Başarılı bir istek durumunda, API aşağıdaki gibi bir yanıt döndürecektir:

```json
{
  "status": "success",
  "message": "Ürünler farklı paketlere bölündü."
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

- `OrderLineIds`: Bölünmek istenen sipariş kalemi kimlik numaraları, ilgili ürünleri temsil eder.
- Her bir sipariş kalemi, ayrı bir pakete bölünür.

