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

POSTMAN / Curl
```sh
curl --location -g --request POST 'https://{path_the_comlab_api}/sapigw/suppliers/{supplierid}/products/price-and-inventory' \
--header 'Authorization: Basic xxx=' \
--header 'Content-Type: application/json' \
--data-raw '{
    "items": [
        {
            "barcode": "8682344153486",
            "listPrice": 129.0,
            "quantity": 365,
            "salePrice": 129.0
        },
        {
            "barcode": "8682344158740",
            "listPrice": 239.0,
            "quantity": 101,
            "salePrice": 239.0
        }
    ]
}'
```