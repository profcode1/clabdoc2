## API Dokümantasyonu

### Endpoint

`POST {path_the_comlab_oms_api}/OrderPackage/shipment-packages/{packageId}/split-packages`

### Amaç

Bu API çağrısı, belirli bir paketi, içinde bulunan ürün kalemlerinin belirli miktarlarını alarak yeni paketler oluşturur.

### İstek Parametreleri

| Parametre      | Açıklama                            | Tür     | Gerekli |
|----------------|-------------------------------------|---------|---------|
| packageId      | Paket kimlik numarası              | Dize    | Evet    |
| SplitPackages  | Paketi bölmek için ayrıntılar      | Dizi    | Evet    |
| OrderLineId    | Sipariş kalemi kimlik numarası     | Tamsayı | Evet    |
| Quantities     | Pakete eklenecek ürün miktarı      | Tamsayı | Evet    |

### Örnek İstek

```json
{
  "SplitPackages": [
    {
      "PackageDetails": [
        {
          "OrderLineId": 328938,
          "Quantities": 5
        },
        {
          "OrderLineId": 328939,
          "Quantities": 5
        }
      ]
    }
  ]
}
```

### Örnek Yanıt

Başarılı bir istek durumunda, API aşağıdaki gibi bir yanıt döndürecektir:

```json
{
  "status": "success",
  "message": "Yeni paket oluşturuldu."
}
```

### Hata Durumu

Hata durumunda, API aşağıdaki gibi bir yanıt döndürecektir:

```json
{
  "status": "error",
  "message": "Hata: Ayrıntılar eksik veya geçersiz."
}
```

### Notlar

- `OrderLineId`: Sipariş kalemi kimlik numarası, ilgili ürünü temsil eder.
- `Quantities`: Pakete eklenecek ürün miktarı, ilgili üründen kaç adet ekleneceğini belirtir.
- Birden fazla ürün kalemi eklemek için, her bir kalemin ayrı ayrı belirtilmesi gerekir.


