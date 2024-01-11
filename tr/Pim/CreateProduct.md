# Yeni Ürün Yaratma ve Güncelleme API Dökümantasyonu (Tekil Ürün)

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
  - **Type**: Ürünün tipi. Tekil ürün için 4 olmalıdır.

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
            "Model": "CV00004X9ZCH",
            "Option": "CV00004X9ZCH",
            "Sku": "CV00004X9ZCH",
            "Barcode": "99194253408215",
            "Type": 4
        },
        "Name": [
            {
                "Value": "iPhone 15 128 GB",
                "EntityListId": 4,
                "Culture": "std"
            },
            {
                "Value": "iPhone 15 128 GB",
                "EntityListId": 4,
                "Culture": "en"
            },
            {
                "Value": "iPhone 15 128 GB",
                "EntityListId": 4,
                "Culture": "tr"
            }
        ],
        "Description": [
            {
                "Value": "<table><tbody><tr><td class=\"no-border\"><table><tbody><tr><td><div class=\"tealium\"><div id=\"ccs-inline-content\" class=\"cnet-integration\"></div></div></td></tr></tbody></table><table><tbody><tr><td><div id=\"productTechSpecContainer\"><table class=\"data-list tech-spec hidden\"><caption></caption><tbody><tr><th>Marka</th><td><a href=\"/apple\" title=\"Apple\">Apple</a></td></tr></tbody></table><table class=\"data-list tech-spec\"><caption></caption><tbody><tr><th>Yüz Tanıma</th><td><span>Var</span></td></tr><tr><th>Ekran Boyutu</th><td><span>6,1 inç</span></td></tr><tr><th>Ekran Boyut Aralığı</th><td><span>6 inç ve Üzeri</span></td></tr><tr><th>Pil Gücü</th><td><span>3877 mAh</span></td></tr><tr><th>Ön (Selfie) Kamera Aralığı</th><td><span>8 - 13,9 MP</span></td></tr><tr><th>Ön (Selfie) Kamera</th><td><span>12 MP</span></td></tr><tr><th>RAM  Kapasitesi</th><td><span>6 GB RAM</span></td></tr><tr><th>Pil Gücü Aralığı</th><td><span>3500 - 3999 mAh</span></td></tr><tr><th>Kamera Çözünürlüğü Aralığı</th><td><span>20 MP ve Üzeri</span></td></tr><tr><th>Dahili Hafıza</th><td><span>128 GB</span></td></tr><tr><th>Kablosuz Şarj</th><td><span>Var</span></td></tr><tr><th>Garanti Tipi</th><td><span>Apple Türkiye Garantili</span></td></tr><tr><th>Kamera Çözünürlüğü</th><td><span>48 MP + 12 MP</span></td></tr></tbody></table><table class=\"data-list tech-spec\"><caption>Diğer</caption><tbody><tr><th>Garanti Süresi (Ay)</th><td><span>24</span></td></tr><tr><th>Yurt Dışı Satış</th><td><span>Yok</span></td></tr><tr><th>Stok Kodu</th><td><span>CV00004X9ZCH</span></td></tr></tbody></table></div></td></tr></tbody></table></td></tr></tbody></table>",
                "EntityListId": 4,
                "Culture": "std"
            }
        ],
        "Prices": [
            {
                "IsTransferable": false,
                "EntityListId": 7,
                "CurrencyId": 1,
                "ListPrice": 500,
                "SalePrice": 600,
                "OperationType": "upsert"
            }
        ],        
        "Assets": [
            {
                "EntityListId": 8,
                "Name": "http://domain.com/full_path_url_ornegi.jpg",
                "AssetType":3,
                "Order": 0
            },
            {
                "EntityListId": 8,
                "Name": "relative_path_url_ornegi.jpg",
                "AssetType":1,
                "Order": 1
            },
            {
                "EntityListId": 8,
                "Name": "relative_path_url_ornegi.mpeg",
                "AssetType":3,
                "Order": 1
            }
        ],
        "Attributes": [
            {
                "EntityListId": 49,
                "Value": "Siyah",
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
                "Value": "Apple",
                "Key": 270,
                "OperationType": "upsert",
                "Culture": "std"
            }
        ]
    }
]'
