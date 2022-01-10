# Sipariş Entegrasyonu

> Tüm satış kanallarından gelen sipariş paketlerini çekebileceğiniz ve durumlarını güncelleyebileceğiniz servisleri barındıran entegrasyondur.

# Api

Method:`GET`

URL:`{path_the_comlab_api}/sapigw/suppliers/{{supplierid}}/orders?size=200&orderByField=CreatedDate&&orderByDirection=ASC&startDate=1623827403272&endDate=1623913803272`

## Parametreler

|Parametre|Tip|Açıklama|Değer|
|-|-|-|-|
|startDate|`long`|Belirli bir tarihten sonraki siparişleri getirir. Timestamp (milliseconds) ve GMT +3 olarak gönderilmelidir.||
|endDate|`long`|Belirtilen tarihe kadar olan siparişleri getirir. Timestamp (milliseconds) ve GMT +3 olarak gönderilmelidir.| 
|page|`int`|Sadece belirtilen sayfadaki bilgileri döndürür	| 
|size|`int`|Bir sayfada listelenecek maksimum adeti belirtir.|max 200| 
|orderNumber|`string`|Sadece belirli bir sipariş numarası verilerek o siparişin bilgilerini getirir	| 
|status|`string`|Siparişlerin statülerine göre bilgileri getirir.|Created, Cancelled, Delivered, Invoiced, Picked, Returned, Shipped,UnDelivered, UnDeliveredAndReturned, ReturnPending
| 
|orderByField|`string`|Son güncellenme tarihini baz alır.	| PackageLastModifiedDate	|
|orderByDirection|`string`|Eskiden yeniye doğru sıralar.	| ASC|
|orderByDirection|`string`|Yeniden eskiye doğru sıralar.		| DESC|
|shipmentPackageIds|`long`|Paket numarasıyla sorgu atılır.	| |


POSTMAN / Curl
```sh
curl --location -g --request POST 'https://{path_the_comlab_api}/sapigw/suppliers/{{supplierid}}/orders?size=200&orderByField=CreatedDate&&orderByDirection=ASC&startDate=1623827403272&endDate=1623913803272' \
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
            "ShipmentAddress": {
                "Id": 120,
                "AddressId": "1234",
                "FirstName": "ahmet",
                "LastName": "mehmet",
                "Company": "",
                "Address1": "abc sokak no 1",
                "Address2": "",
                "Gsm": "0(505) 1234567",
                "City": "İstanbul",
                "District": "Maltepe",
                "Neighborhood": "Girne Mah",
                "PostalCode": "",
                "CountryCode": "TR",
                "FullName": "ahmet mehmet",
                "FullAddress": "Girne Mah abc sokak no 1",
                "CityCode": 0,
                "DistrictId": 0
            },
            "OrderNumber": "WEB159",
            "GrossAmount": 97.8,
            "TotalDiscount": 43.34,
            "TotalPrice": 89.91,
            "TaxNumber": null,
            "InvoiceAddress": {
                "Id": 120,
                "AddressId": "1234",
                "FirstName": "ahmet",
                "LastName": "mehmet",
                "Company": "",
                "Address1": "abc sokak no 1",
                "Address2": "",
                "Gsm": "0(505) 1234567",
                "City": "İstanbul",
                "District": "Maltepe",
                "Neighborhood": "Girne Mah",
                "PostalCode": "",
                "CountryCode": "TR",
                "FullName": "ahmet mehmet",
                "FullAddress": "Girne Mah abc sokak no 1",
                "CityCode": 0,
                "DistrictId": 0
            },
            "CustomerFirstName": "ahmet",
            "CustomerEmail": "abc@test.com",
            "CustomerId": 0,
            "CustomerCode": "60b7475309e9920001568275",
            "CustomerGsm": "0(505) 1234567",
            "CustomerLastName": "mehmet",
            "Id": 10134,
            "CargoTrackingNumber": null,
            "CargoTrackingLink": null,
            "CargoSenderNumber": "1",
            "CargoProviderName": null,
            "Lines": [
                {
                    "Quantity": 1,                   
                    "MerchantId": 0,
                    "Amount": 59.9,
                    "Discount": 9.54915,
                    "Price": 44.95,
                    "DiscountDetails": [                        
                        {
                            "LineItemPrice": 19.09,
                            "LineItemDiscount": 19.09
                        }
                    ],
                    "PaymentDetails": null,
                    "CurrencyCode": "TRY",
                    "ProductColor": null,
                    "Id": "60c9d65fa269b45f5ccbc8b2",
                    "Sku": "SKU1",
                    "VatBaseAmount": 38,
                    "Barcode": "123456",
                    "OrderLineItemStatusName": "Created",
                    "IsGift": false,
                    "GiftNote": null
                }
            ],
            "OrderDate": 1623851149397,
            "TcIdentityNumber": null,
            "CurrencyCode": "TRY",
            "PackageHistories": [
                {
                    "CreatedDate": 1623851149397,
                    "Status": "Created"
                }
            ],
            "ShipmentPackageStatus": "Created",
            "IntegrationId": "WEB",
            "LastModifiedDate": "2021-06-16T11:10:12.843Z"
        }   
	]
}
```

> Response için örnek c# sınıfları
```csharp
public partial class OrderResult
    {
        public int Page { get; set; }
        public int Size { get; set; }
        public int TotalPages { get; set; }
        public int TotalElements { get; set; }
        public IEnumerable<SwOrder> Content { get; set; }
    }

    public partial class SwOrder
    {
        public SwAddress ShipmentAddress { get; set; }
        public string OrderNumber { get; set; }

        public double GrossAmount { get; set; }
        public double TotalDiscount { get; set; }
        public double TotalPrice { get; set; }
        public object TaxNumber { get; set; }
        public SwAddress InvoiceAddress { get; set; }
        public string CustomerFirstName { get; set; }
        public string CustomerEmail { get; set; }
        public long CustomerId { get; set; }
        public string CustomerCode { get; set; }
        public string CustomerGsm { get; set; }
        public string CustomerLastName { get; set; }
        public long Id { get; set; }
        public string CargoTrackingNumber { get; set; }
        public string CargoTrackingLink { get; set; }
        public string CargoSenderNumber { get; set; }
        public string CargoProviderName { get; set; }
        public List<Line> Lines { get; set; }
        public long OrderDate { get; set; }
        public string TcIdentityNumber { get; set; }
        public string CurrencyCode { get; set; }
        public List<PackageHistory> PackageHistories { get; set; }
        public string ShipmentPackageStatus { get; set; }
        public string IntegrationId { get; set; }
        public DateTime LastModifiedDate { get; set; }
        
        public bool IsGuest { get; set; }
    }

    public partial class SwAddress
    {
        public long Id { get; set; }
        public string AddressId { get; set; }
        public string FirstName { get; set; }
        public string LastName { get; set; }
        public string Company { get; set; }
        public string Address1 { get; set; }
        public string Address2 { get; set; }
        public string Gsm { get; set; }
        public string City { get; set; }
        public string District { get; set; }
        public string Neighborhood { get; set; }
        public string PostalCode { get; set; }
        public string CountryCode { get; set; }
        public string FullName { get; set; }
        public string FullAddress { get; set; }
        public long? CityCode { get; set; }
        public long? DistrictId { get; set; }
        public string TaxAdministration { get; set; }
        public string VatNumber { get; set; }

    }

    public partial class Line
    {
        public int Quantity { get; set; }
        public long SalesCampaignId { get; set; }
        public string ProductSize { get; set; }
        public string MerchantSku { get; set; }
        public string ProductName { get; set; }
        public long ProductCode { get; set; }
        public long MerchantId { get; set; }
        public double Amount { get; set; }
        public double Discount { get; set; }
        public double Price { get; set; }
        public List<DiscountDetail> DiscountDetails { get; set; }
        public List<PaymentDetail> PaymentDetails { get; set; }
        public string CurrencyCode { get; set; }
        public string ProductColor { get; set; }
        public string Id { get; set; }
        public string Sku { get; set; }
        public long VatBaseAmount { get; set; }
        public string Barcode { get; set; }
        public string OrderLineItemStatusName { get; set; }
        public bool IsGift { get; set; }
        public string GiftNote { get; set; }
    }

    public partial class DiscountDetail
    {
        public double LineItemPrice { get; set; }
        public double LineItemDiscount { get; set; }
    }

    public partial class PackageHistory
    {
        public long CreatedDate { get; set; }
        public string Status { get; set; }
    }

    public class PaymentDetail
    {
        public string PaymentId { get; set; }
        public string OrderLineId { get; set; }
        public string PaymentMethodId { get; set; }
        public decimal Total { get; set; }
        public string TransactionId { get; set; }
        public int InstallmentCount { get; set; }
        public string OrderId { get; set; }
        public string CardNumber { get; set; }
        public string CardName { get; set; }
        public string CardType { get; set; }
        public string CardFamily { get; set; }
        public string CardIssuer { get; set; }
        public string BankName { get; set; }
        public string FraudScore { get; set; }
        public string PosName { get; set; }
        public string CardCvv2 { get; set; }
        public string RefundAuthCode { get; set; }
        public string RefundTransactionId { get; set; }

    }
```

|Statü|Açıklama|
|-|-|
|Created|Sipariş gönderime hazır statüsünde olduğu zaman dönmektedir.
|Invoiced|Siparişin faturasını kestiğiniz zaman bize iletebileceğiniz statüdür.|
|Shipped|	Taşıma durumuna geçen siparişler bu statüde belirtilmektedir.|
|Cancelled|İptal edilen siparişlerdir.|
|Delivered|Teslim edilen siparişlerdir.|

>Siparişleri çektikten sonra işlemlerinize göre siparişlerinizi güncellemek için sipariş güncelleme entegrasyonu siparişleri yönetebilirisiniz.

>Sonraki :  [Sipariş Güncelleme Entegrasyonu](OrderUpdate.md)