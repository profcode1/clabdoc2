# Ürün Entegrasyonu

![screenshoot](../../../m/productIntegration.png)

> Ürün entegrasyonu için gerekli ve zorunlu alanlar

|Alan|Zorunlumu?|Açıklama|Değer|Örnek|
|:-|:-:|-|-|-|
| Type|Hayır||variant,single,bundle|variant|
| Model|Evet| Model bir ürünün varyantsız tanımıdır. Bir ürünü renk bazında eşleştirmek için Model kodları aynı olmalıdır. Bir model kodunun altında aynı renkten birden fazla olamaz.|Serbest|GOMLEK10|
| OptionCode|Evet|Bir Fotoğrafa ve renge sahip olan listelenebilir ürünü temsil eder. Bir OptionCode altında eğer varyant var ise aynı varyant özelliğine sahip olan 2 Sku olamaz.|Serbest|GOMLEK10KRMZ|
| Sku|Evet|Sku satılabilir, sepete eklenebilir ürünü temsil eder ve tekildir. Aynı Sku dan birden fazla olamaz. |Serbest|GOMLEK10KRMZM|
| Barcode|Evet|Ürünün varsayılan barkodudur ve tekildir.|Serbest|978020137962


>Ürün Yapısı

```csharp
public class Product
{        
    public ProductType Type { get; set; }
    public string Barcode { get; set; }
    public string Sku { get; set; }
    public string OptionCode { get; set; }  
    public string Model { get; set; }
    public DateTime CreatedOn { get; set; }
}
```



# Tanımlar
* [Varyant nedir?](/Integration/Catalog/Variant.md)
* [ddd]