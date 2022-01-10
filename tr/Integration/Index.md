# Entegrasyon Nasıl Yapılır?

![screenshoot](../../m/integrationhowto.png)

> Entegrasyona başlarken size özel test ortamı için `Api Url` , api `Key` , `Secret` ve `supplierid` bilgileri commercelab tarafından temin edilir. Öncelikle test ortamında işlemler tamamlandıktan sonra prod ortamı için sadece bu bilgiler değişecektir.

>Entegrasyonu yaparken tüm endpointlere ulaşabileceğiniz swagger arayüzü sağlanmaktadır.

* Entegrasyon `REST Api` ler düzerinden yütülmektedir.
* Bazı doğrulamasız apiler haricinde tüm apiler `Basic Auth` kullanarak yürütülmektedir.
* Api urlleri  `https://{path_the_comlab_api}/sapigw/suppliers/{supplierid}/` şeklinde başlayarak ilgili fonksiyon eklenerek oluşur. `{supplierid}`,`{path_the_comlab_api}` sizelere iletilecektir.
*


## Örnek bir request
Method:`POST`

Security:`Basic Auth`

URL:`{path_the_comlab_api}/sapigw/suppliers/{supplierid}/products/price-and-inventory`

Request Body:
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

Basic Auth ile RESTSharp ile yapılan örnek bir fonksiyon

C#
```csharp
public static IRestResponse PutJson<T>(string url, T body, string username, string password)
        {
            var client = new RestClient(url);
            var request = new RestRequest(Method.PUT);
            request.AddHeader("content-type", "application/json");

            if (!string.IsNullOrEmpty(username))
            {
                request.AddHeader("Authorization", "Basic " + Convert.ToBase64String(
                System.Text.ASCIIEncoding.ASCII.GetBytes(
                    string.Format("{0}:{1}", username, password))));
            }
            string json = JsonConvert.SerializeObject(body, new JsonSerializerSettings { NullValueHandling = NullValueHandling.Ignore });
            request.AddParameter("application/json", json, ParameterType.RequestBody);
            return client.Execute(request);
        }
```        

## Entegrasyonlardaki istek limitleri
>Saatlik ve günlük istek limitleri

|İstek|Limit|
|-|-|
|QueCreateProductRequestDay|100	                 |
|QueCreateProductRequestHours|50	|
|QueUpdateCustomerLineRequestDay|2000	|
|QueUpdateCustomerLineRequestHours|1000	|
|QueUpdateCustomerRequestDay|100	|
|QueUpdateCustomerRequestHours|10	|
|QueUpdateInvoiceLinkRequestDay|10000	|
|QueUpdateInvoiceLinkRequestHours|1000	|
|QueUpdateOrderRequestDay|10000	|
|QueUpdateOrderRequestHours|1000	|
|QueUpdatePackageRequestDay|	10000	|
|QueUpdatePackageRequestHours|	1000	|
|QueUpdatePriceAndInventoryRequestDay	|2000	|
|QueUpdatePriceAndInventoryRequestHours	|800	|
|QueUpdateTrackingLinkRequestDay|	10000	|
|QueUpdateTrackingLinkRequestHours|	1000	|
|QueUpdateTrackingNumberRequestDay|	10000	|
|QueUpdateTrackingNumberRequestHours|	1000|


>Sonraki :  [Ürün Entegrasyonu](Catalog/Product.md)