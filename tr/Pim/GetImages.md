# PIM'deki Ürün Görsellerini Çekme

PIM'deki ürün görsellerinin çekilmesi için aşadaki curl kullanılabilir. 

## API Yetkilendirmesi

Bu API'yi kullanabilmek için geçerli bir yetkilendirme belirteci (token) gereklidir. Yetkilendirme belirteci, 'Authorization' başlığı ile isteğe eklenmelidir.

## API İsteği

Aşağıdaki `curl` komutu ile API'ye istek yapabilirsiniz:

```json
curl --location 'https://stgapi.mcc.awstest.hebiar.com/pim/vendor/products?isPre=false' \
--data '{
    "FilteredColumns": [],
    "Page": 1,
    "PageSize": 1000,
    "SelectedColumns": [
        "assetid"
    ],
    "SortedColumn": null
}'
```

### İstek Parametreleri

| Parametre         | Açıklama                                   | Tür     | Gerekli   |
|-------------------|--------------------------------------------|---------|-----------|
| FilteredColumns  | Filtrelenmiş sütunlar                      | Dizi    | Opsiyonel |
| Page             | Sayfa numarası                             | Tamsayı | Gerekli   |
| PageSize         | Sayfa başına maksimum öğe sayısı           | Tamsayı | Gerekli   |
| SelectedColumns  | Seçilen sütunlar                           | Dizi    | Gerekli   |
| SortedColumn     | Sıralanmış sütun                            | Dizi    | Opsiyonel |


## API Yanıtı

Aşağıda API'nin örnek bir yanıtı yer almaktadır:

```json
{
    "status": "success",
    "data": {
        "assets": [
            {
                "assetid": "ÖRNEK_ASSET_ID_1"
            },
            {
                "assetid": "ÖRNEK_ASSET_ID_2"
            },
            ...
        ]
    }
}

```

### Yanıt Alanları ve Açıklamaları

- `status`: İstek durumu (`success` veya `error`).
- `data`: İstek sonucu veri.
- `assets`: Varlık listesi.
- `assetid`: Varlığın kimlik numarası.


