## API Dokümantasyonu

### Endpoint

`POST {path_the_comlab_oms_api}/OrderPackage/shipment-packages/{packageId}/multi-split`

### Amaç

Bu API çağrısı, belirli bir paketin içinde bulunan ürün kalemlerini farklı paketlere böler.

### İstek Parametreleri

| Parametre      | Açıklama                            | Tür     | Gerekli |
|----------------|-------------------------------------|---------|---------|
| packageId      | Paket kimlik numarası              | Dize    | Evet    |
| SplitGroups    | Bölünmek istenen gruplar            | Dizi    | Evet    |
| OrderLineIds   | Bölünmek istenen sipariş kalemi kimlik numaraları | Dizi | Evet    |

### Örnek İstek

```json
{
    "SplitGroups":[
        {
            "OrderLineIds":[328935,328934]
        },
        {
            "OrderLineIds":[328936]
        }
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

- `SplitGroups`: Bölünmek istenen gruplar, her bir grup ayrı bir paket oluşturulmasını sağlar.
- Her bir grup içindeki sipariş kalemleri, ilgili pakete dahil edilir.

