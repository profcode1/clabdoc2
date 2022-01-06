# Stok ve Fiyat Entegrasyonu

![screenshoot](../../../m/inventory.jpg)

> Ürünleri aktardıktan sonra anlık stok ve fiyat bilgilerini bu servisi kullanarak gönderebilirsiniz.

# Api

Method:`POST`

URL:`{path_the_comlab_api}/sapigw/suppliers/{supplierid}/products/price-and-inventory`
```json
{
   "items":[
      {
         "barcode":"8682344260467",
         "listPrice":599.0,
         "quantity":5,
         "salePrice":419.9
      },
      {
         "barcode":"8682344260474",
         "listPrice":599.0,
         "quantity":0,
         "salePrice":419.9
      }
   ]
}
```

