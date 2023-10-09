# Yeni Ürün Yaratma ve Güncelleme API Dökümantasyonu (Varyantlı Ürün)

Bu API, yeni ürünlerin yaratılması veya mevcut ürünlerin güncellenmesi için kullanılır.

## API Endpoint

API, aşağıdaki endpoint üzerinden çağrılabilir:

`POST https://apiurl/pim/SaveProductsManually?companyId=8`

## İstek Başlıkları (Request Headers)

- **Authorization**: Kullanıcı kimlik doğrulaması için kullanılan JWT (JSON Web Token) kimlik belgesi.
- **Content-Type**: İstek gövdesinin JSON formatında olduğunu belirten başlık.

## İstek Gövdesi (Request Body)

API isteği, aşağıdaki JSON verilerini içeren bir dizi ürün bilgisi içerir:

### Ürün Bilgileri

- **Main**: Temel ürün bilgilerini içeren nesne.
  - **Model**: Ürünün model numarası.
  - **Option**: Ürünün seçeneği.
  - **Sku**: Ürünün stok birimi (SKU).
  - **Type**: Ürünün tipi. varyantlar  için 3 olmalıdır. model=1,option=2

### Ürün Adları

- Ürünün farklı kültürler için farklı adlarını içeren bir dizi nesne.
  - **Value**: Ürünün adı.
  - **EntityListId**: Dil kodunu içeren kimlik.
  - **Culture**: Dil kodu (örneğin: "std" standart, "en" İngilizce, "tr" Türkçe).

### Ürün Açıklaması

- Ürünün açıklamasını içeren bir dizi nesne.
  - **Value**: Ürünün açıklaması.
  - **EntityListId**: Dil kodunu içeren kimlik.
  - **Culture**: Dil kodu (örneğin: "std" standart, "en" İngilizce, "tr" Türkçe).

### Ürün Fiyatları

- Ürünün fiyat bilgilerini içeren bir dizi nesne.
  - **IsTransferable**: Fiyatın transfer edilebilir olup olmadığını belirten bayrak.
  - **EntityListId**: Fiyat bilgisini tanımlayan kimlik.
  - **CurrencyId**: Para birimi kimliği.
  - **ListPrice**: Ürünün liste fiyatı.
  - **SalePrice**: Ürünün satış fiyatı.
  - **CampaignPrice**: Ürünün kampanya fiyatı (varsa).
  - **OperationType**: Fiyat işlem türü (örneğin: "upsert").

### Ürün Fotoğraf ve Video (Assets)

- Ürünün medya varlıklarını içeren bir dizi nesne. (örneğin, ürün görselleri)
  - **EntityListId**: Varlığı tanımlayan kimlik.
  - **Name**: Varlığın URL'si veya adı.
  - **Order**: Varlığın sıralama düzeni.
  - **AssetType**: Varlığın tipi video=3,fotoğraf=1.

### Ürün Özellikleri

- Ürünün özelliklerini içeren bir dizi nesne.
  - **EntityListId**: Özelliği tanımlayan kimlik.
  - **Value**: Özelliğin değeri.
  - **Key**: Özelliğin anahtarı.
  - **OperationType**: Özellik işlem türü (örneğin: "upsert").
  - **Culture**: Dil kodu (örneğin: "std" standart, "en" İngilizce, "tr" Türkçe).

## Örnek Kullanım

Aşağıda API'yi kullanarak yeni bir ürün eklemek için bir örnek CURL isteği bulunmaktadır.

```bash
curl --location 'https://apiurl/pim/SaveProductsManually?companyId=8' \
--header 'Authorization: Bearer [YourJWTToken]' \
--header 'Content-Type: application/json' \
--data '[
    {
        "Main": {
            "Model": "TestAyakkabi3",
            "Type": 1
        },
        "ProductLists": [
            {
                "OperationType": "upsert",
                "EntityListId": 10
            }
        ]
    },
    {
        "Main": {
            "Option": "TestAyakkabi3KIRMIZI",
            "Model": "TestAyakkabi3",
            "Type": 2
        },
        "Attributes": [
            {
                "EntityListId": 49,
                "Value": "Turkuaz",
                "Key": 260,
                "OperationType": "upsert",
                "Culture": "std"
            },
            {
                "EntityListId": 49,
                "Value": "Unisex",
                "Key": 267,
                "OperationType": "upsert",
                "Culture": "std"
            },
            {
                "EntityListId": 49,
                "Value": "Adidas",
                "Key": 270,
                "OperationType": "upsert",
                "Culture": "std"
            }
        ],
        "Prices": [
            {
                "IsTransferable": true,
                "EntityListId": 7,
                "CurrencyId": 1,
                "ListPrice": 100,
                "SalePrice": 100
            }
        ],
        "ProductLists": [
            {
                "OperationType": "upsert",
                "EntityListId": 10
            }
        ],
        "Name": [
            {
                "Value": "Test Ayakkabi 1 KIRMIZI",
                "EntityListId": 4,
                "Culture": "std"
            }
        ],
        "Description": [
            {
                "Value": "<h1>Çok güzel kırmızı ayakkabı</h1><b>Alt Başlık Deneme</b> <p class=\"table-text\">Burada ürünle ilgili kısa bilgi verilecektir. </p><table><tbody><tr class=\"table-baslik\"> <td>Ürün Özellikleri</td><td>Açıklama</td><tr> <td>Dahili Hafıza</td><td>128 GB</td></tr><tr> <td>Ekran Boyutu</td><td>32\"</td></tr><tr class=\"table-baslik\"> <td>Fiziksel Özellikler</td><td>Açıklama</td><tr> <td>Bölme Sayısı</td><td>3 Bölme</td></tr></tbody></table>",
                "EntityListId": 4,
                "Culture": "std"
            }
        ],
        "Title": [
            {
                "Value": "Test Ayakkabi 1 KIRMIZI",
                "EntityListId": 4,
                "Culture": "std"
            }
        ],
        "SeoDescription": [
            {
                "Value": "Test Ayakkabi 1 KIRMIZI",
                "EntityListId": 4,
                "Culture": "std"
            }
        ]
    },
    {
        "Main": {
            "Type": 3,
            "Option": "TestAyakkabi3KIRMIZI",
            "Model": "TestAyakkabi3",
            "Sku": "TestAyakkabi3KIRMIZI37",
            "Barcode": "TestAyakkabi3KIRMIZI37"
        },
        "Attributes": [
            {
                "EntityListId": 49,
                "Value": "37",
                "Key": 269,
                "OperationType": "upsert",
                "Culture": "std"
            }
        ],
        "ProductLists": [
            {
                "OperationType": "upsert",
                "EntityListId": 10
            }
        ]
    },
    {
        "Main": {
            "Type": 3,
            "Option": "TestAyakkabi3KIRMIZI",
            "Model": "TestAyakkabi3",
            "Sku": "TestAyakkabi3KIRMIZI38",
            "Barcode": "TestAyakkabi3KIRMIZI38"
        },
        "Attributes": [
            {
                "EntityListId": 49,
                "Value": "38",
                "Key": 269,
                "OperationType": "upsert",
                "Culture": "std"
            }
        ],
        "ProductLists": [
            {
                "OperationType": "upsert",
                "EntityListId": 10
            }
        ]
    },
    {
        "Main": {
            "Type": 3,
            "Option": "TestAyakkabi3KIRMIZI",
            "Model": "TestAyakkabi3",
            "Sku": "TestAyakkabi3KIRMIZI39",
            "Barcode": "TestAyakkabi3KIRMIZI39"
        },
        "Attributes": [
            {
                "EntityListId": 49,
                "Value": "39",
                "Key": 269,
                "OperationType": "upsert",
                "Culture": "std"
            }
        ],
        "ProductLists": [
            {
                "OperationType": "upsert",
                "EntityListId": 10
            }
        ]
    }
]'
