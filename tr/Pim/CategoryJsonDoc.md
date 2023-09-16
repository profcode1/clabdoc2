# Kategori modelinin detayları

Bu dökümantasyon, api yada hook ile alınan kategori modelinin alanlarını açıklar.


```json
{
    "AllowCustomersToSelectPageSize": 48,//kullanıabilir defaullta hangi PageSize seçerli.
    "CategoryFullPath": "Elektronik >> Televizyon ",//ismen full path gösterim için kullanıabilir.
    "CategoryId": "C0101", //kategtori id olarak kullanılmalı
    "CategoryImageUrl": null,//kategori için seçilecek bir fotoğraf urli    
    "CreatedOn": "2023-06-01T12:13:15.073Z",//kullanılabilir kategori yaratma tarihi    
    "DefaultSort": -1,//kategoride defaultta hangi sıralama seçeneği seçili
    "DefaultSortTypeId": 1,
    "Deleted": false,//kategorinin silinmesi durumunda 301 lemek gerek 
    "Description": "Televizyon  Description",//kategorinin açıklaması
    "DisplayOrder": 971,//kategorinin sırası
    "Faqs": [ //seo için kullanılabilir faq , detaylarla ilgili seo firması ile ilerlenmeli
        {
            "Answer": "Televizyon  çok iyidir.", //kategori ile ilgili google için sorusuna cevap  detaylarla ilgili seo firması ile ilerlenmeli            
            "OrderNo": 1,//sırası detaylarla ilgili seo firması ile ilerlenmeli
            "Question": "Televizyon  iyimidir?"//kategori ile ilgili google için sorusu  detaylarla ilgili seo firması ile ilerlenmeli
        }
    ],
    "Faseds": [//seo için kullanılabilir fased li linklerin eklenebilmesi için, detaylarla ilgili seo firması ile ilerlenmeli
        {
            "ALink": false,//fased linki bir yerde varsa ona link verilmelimi?  detaylarla ilgili seo firması ile ilerlenmeli
            "CanonicalUrl": "televizyon-C971?renk=kirmizi",//ilgili fasedli urlin canonicalurli            detaylarla ilgili seo firması ile ilerlenmeli              
            "Description": "Kırmızı Televizyon  Description",//ilgili fasedli urlin açıklaması     detaylarla ilgili seo firması ile ilerlenmeli
            "MetaDescription": "Kırmızı Televizyon  MetaDescription",//ilgili fasedli seo desci detaylarla ilgili seo firması ile ilerlenmeli
            "MetaTitle": "Kırmızı Televizyon  MetaTitle",//ilgili fasedli urlin seo titlesi detaylarla ilgili seo firması ile ilerlenmeli
            "Name": "Kırmızı Televizyon ",//ilgili fasedli urlin adı      detaylarla ilgili seo firması ile ilerlenmeli
            "NoFollow": false,//ilgili fasedli urlin linkine nofollow eklenip eklenmemesi ile ilgili detaylarla ilgili seo firması ile ilerlenmeli
            "NoIndex": false,//ilgili fasedli urlin indexlenmesi ile ilgili      detaylarla ilgili seo firması ile ilerlenmeli
            "Sitemap": false,//ilgili fasedli urlin sitemape eklenip eklenmemesi ile ilgili      detaylarla ilgili seo firması ile ilerlenmeli
            "Url": "televizyon-C971?renk=kirmizi"//ilgili fasedli urlin urli     detaylarla ilgili seo firması ile ilerlenmeli
        }
    ],    
    "FilterableAttributeIds": [//bu kategoride hangi attributeler filtrelenebilir?
                270,
                260,
                461
            ],    
    "GenericAttributes": [//istenirse kullanıabilir tamamen serbest bir alan. mesela bir kategorinin en üstüne bir html eklenmek isteniyorsa.
                {
                    "AttributeKey": "ust_foto_1",
                    "AttributeValue": "http://foto1...",
                    "CategoryId": 1022,
                    "ExternalStoreId": "5e66aebbc742917014d6a2dc",
                    "StoreId": 1,
                    "StoreName": "store01"
                }
            ],
    "Icon": null,//istenirse kullanılabilir menülerde icon koyulmak istenebiliyor  iconurl gelecek
    "Id": 971,//kullanılmasına gerek yok bizim iç idmiz.
    "IncludeInTopMenu": false,//istenirse kullanılabilir üst menüye koyup koymamakla ilgili
    "IsBreadcrumb": false,//birden fazla kategori seçildiğinde sadece breadcrumb kategorşisinin hangisi oılduğuna karar verebilmek için kullanıabilir.
    "MetaDescription": "Televizyon  MetaDescription",//seo için MetaDescription
    "MetaKeywords": "Televizyon  MetaKeywords", //seo için MetaKeywords
    "MetaTitle": "Televizyon  MetaTitle", //seo için meta title
    "Name": "Televizyon ",//kategori adı
    "NodeTypeId": 1, //kategorinin markamı yoksa normal kategorimi olduğu 1=kategori 4 marka
    "NoIndex": false,//istenirse kullanılabilir seoda noindex
    "PageSize": 48, //istenirse kullanılabilir kategoride paging yapılacaksa kaçar kaçar geleceği    
    "ParentCategoryId": "C01",//parent kategtori id olarak kullanılmalı    
    "PriceRanges": "0-199;200-299;300-499;500-;", //istenirse kullanılabilir kategori filtredeki fiyat aralıkları
    "Published": true,//istenirse kullanılabilir, kategori genel olarak yayındamı değilmi? 
    "SearchBoxDisplayOrder": 0,//istenirse kullanılabilir, autocomplete aramada kaçıncı sırada gelecek?
    "ShowOnHomePage": false,//istenirse kullanılabilir anasayfada gösterilmek istenip istenmediği
    "ShowOnSearchBox": false,//istenirse kullanılabilir autocompletede gösterilmek istenip istenmediği
    "ToMenuVisibleProductCount": null,//istenirse kullanılabilir bir menüde minimum kaç adet ürün varsa o kategori menüye konulmalı?
    "UpdatedOn": "2023-09-16T14:50:08.113Z", //kullanılabilir kategori güncelleme tarihi
    "Url": "televizyon-C0101"//url olarak kullanılmalı
}
```
