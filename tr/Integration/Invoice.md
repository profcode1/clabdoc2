# Fatura Entegrasyonu

> İrsaliyesi kesilmiş paket listesini çekmek için bu servis kullanılır. Bu servisi kullanarak irsaliyeleri ERP sisteminize aktarabilir ve muhasebeleştirebilirsiniz.


# Api

Method:`GET`

URL:`{{path_the_comlab_api}}/sapigw/suppliers/{{supplierid}}/edocuments?size=200`

> Tüm parametreler son güncelleme tarihine göre sıralanır. Müşterileri düzenli çekmek için startDate , endDate kullanarak servisi kullanabilirsiniz.

## Parametreler

|Parametre|Tip|Açıklama|Değer|
|-|-|-|-|
|startDate|`long`|Belirli bir tarihten sonraki müşterileri getirir. Timestamp (milliseconds) ve GMT +3 olarak gönderilmelidir.||
|endDate|`long`|Belirtilen tarihe kadar olan müşterileri getirir. Timestamp (milliseconds) ve GMT +3 olarak gönderilmelidir.| 
|page|`int`|Sadece belirtilen sayfadaki bilgileri döndürür	| 
|size|`int`|Bir sayfada listelenecek maksimum adeti belirtir.|max 200| 
|orderNumber|`string`|Sadece belirli bir sipariş numarası verilerek o siparişin bilgilerini getirir	| 
|status|`string`|Siparişlerin statülerine göre bilgileri getirir.|Created, Cancelled, Delivered, Invoiced, Picked, Returned, Shipped,UnDelivered, UnDeliveredAndReturned, ReturnPending
| 
|orderByDirection|`string`|Eskiden yeniye doğru sıralar.	| ASC|
|orderByDirection|`string`|Yeniden eskiye doğru sıralar.		| DESC|
|clientStatus|`string`|sizin vereceğiniz statu ile filtrelenebilir	| |
|company|`string`|birden fazla firma varsa firmaya göre filtre	| |
|prefix|`string`|sipariş prefixine göre filtre	| |
|OrderTypeCode|`string`|sipariş tipine göre	| ISO (instrore order...) |

> ## `Önemli Note:  MAX 15 gün aralık ile data gelir. Eğer aralık 15 günü geçerse başlangıç tarihinden itibaren +15 gün ile çalışır.`


POSTMAN / Curl
```sh
curl --location -g --request POST 'https://{path_the_comlab_api}/sapigw/suppliers/{{supplierid}}/edocuments?size=200' \
--header 'Authorization: Basic xxx=' \
--header 'Content-Type: application/json' \
'
```
> Result
```json
{
    "Page": 0,
    "Size": 200,
    "TotalPages": 1,
    "TotalElements": 5,
    "Content": [
        {
            "ModelType": 0,
            "CustomerCode": "ERPCUSTCODE",
            "Description": "WEB1234",//sipariş numarası
            "CompanyCode": "1",
            "PosterminalID": 1,
            "IsOrderBase": true,
            "OfficeCode": "ABC",
            "StoreCode": "ABC",
            "WareHouseCode": "ABC",
            "SourceLocation": "ABC",
            "DefaultPreviousProcess": 2,
            "DeliveryCompanyCode": "MNG",
            "ShipmentMethodCode": "2",
            "IsSalesViaInternet": true,
            "EMailAddress": "abc@abc.com",
            "SendInvoiceByEMail": true,
            "Lines": [
                {
                    "OrderLineID": "b5fad013-51f8-47f2-b51a-ae1200aaa66a",
                    "Qty1": 1
                }
            ],
            "SalesViaInternetInfo": {
                "SalesURL": "www.abc.com.tr",
                "PaymentTypeCode": 2,
                "PaymentTypeDescription": "KREDIKARTI/BANKAKARTI",
                "PaymentDate": "2022-01-03T13:21:21.03Z",
                "SendDate": "2022-01-10T17:06:47.0382206+03:00"
            },
            "EDocument": {
                "DocumentId": 59717,
                "EttnNumber": "XXXXXXXX-AAA7-443D-816E-XXXXXXXX",
                "DocumentNumber": "ABC2022000058943",
                "CreateDate": "01/03/2022 17:51:52",
                "Statu": "Completed",
                "ClientStatus": "Complated",
                "ClientStatusDesc": null
            },
            "IsCompleted": true,
            "OrderTypeCode": "WEB"
        }
	]
}
```

> Response için örnek c# sınıfları
```csharp
public partial class EDocumentResult
    {

        public int Page { get; set; }
        public int Size { get; set; }
        public int TotalPages { get; set; }
        public int TotalElements { get; set; }
        public IEnumerable<ERPInvoiceModel> Content { get; set; }

        public partial class EDocument
        {
            public long DocumentId { get; set; }
            public string EttnNumber { get; set; }
            public string DocumentNumber { get; set; }
            public string CreateDate { get; set; }
            public string Statu { get; set; }
            [System.Text.Json.Serialization.JsonIgnore]
            public string OrderLineId { get; set; }
            [System.Text.Json.Serialization.JsonIgnore]
            public string ECargoCompanyId { get; set; }
            [System.Text.Json.Serialization.JsonIgnore]
            public string ErpOrderLineId { get; set; }
            [System.Text.Json.Serialization.JsonIgnore]
            public string OrderId { get; set; }
            [System.Text.Json.Serialization.JsonIgnore]
            public long Qty { get; set; }
            [MaxLength(20)]
            public string ClientStatus { get; set; }            
            [MaxLength(250)]
            public string ClientStatusDesc { get; set; }                        
        }

        public partial class ERPInvoiceLine
        {
            public string OrderLineID { get; set; }
            public int Qty1 { get; set; }
        }

        public partial class SalesViaInternetInfo
        {
            public string SalesURL { get; set; }
            public int PaymentTypeCode { get; set; }
            public string PaymentTypeDescription { get; set; }
            public DateTime PaymentDate { get; set; }
            public DateTime SendDate { get; set; }
        }

        public partial class ERPInvoiceModel
        {
          
            public string CustomerCode { get; set; }
            public string Description { get; set; }
            public string CompanyCode { get; set; }
            public int PosterminalID { get; set; }
            public bool IsOrderBase { get; set; }
            public string OfficeCode { get; set; }
            public string StoreCode { get; set; }
            public string WareHouseCode { get; set; }
            public string SourceLocation { get; set; }
            public int DefaultPreviousProcess { get; set; }
            public string DeliveryCompanyCode { get; set; }
            public string ShipmentMethodCode { get; set; }
            public bool IsSalesViaInternet { get; set; }
            public string EMailAddress { get; set; }
            public bool SendInvoiceByEMail { get; set; } = true;
            public List<ERPInvoiceLine> Lines { get; set; }
            [JsonProperty(NullValueHandling = NullValueHandling.Ignore)]
            public SalesViaInternetInfo SalesViaInternetInfo { get; set; }
            public EDocument EDocument { get; set; }
            public bool IsCompleted { get; set; }
            public string OrderTypeCode { get; set; }
        }

        
    }
```

# Api ile çekilen faturaların çekildiği bilgisini commercelab e iletme

> Bu api commercelab den tüm irsaliyeleri aldımmı sorusunun cevabının verilebilmesi tam bir uyumluluk olması için kullanılır. Kaçırılan bir fatura olmaması adına bu entegrasyonun yapılması tavsiye edilir.



Method:`POST`

URL:`{{path_the_comlab_api}}/sapigw/suppliers/{{supplierid}}/edocuments/updateClientStatus`


POSTMAN / Curl
```sh
curl --location -g --request POST '{{path_the_comlab_api}}/sapigw/suppliers/{{supplierid}}/edocuments/updateClientStatus' \
--header 'Authorization: Basic xxx' \
--header 'Content-Type: application/json' \
--data-raw '[
    {
        "DocumentNumber": "ABC124",
        "ClientStatus": "Completed"
    },
    {
        "DocumentNumber": "ABC123",
        "ClientStatus": "Completed"
    }
]'
```
