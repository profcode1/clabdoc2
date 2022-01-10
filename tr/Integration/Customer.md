# Müşteri Entegrasyonu

> Tüm kanallardan gelen müşteri bilgilerini çekmek bu servis kullanılır.


# Api

Method:`GET`

URL:`{{path_the_comlab_api}}/sapigw/suppliers/{{supplierid}}/customers?size=200&startDate=1523827403272&endDate=1623913803272`

> Tüm parametreler son güncelleme tarihine göre sıralanır. Müşterileri düzenli çekmek için startDate , endDate kullanarak servisi kullanabilirsiniz.

## Parametreler

|Parametre|Tip|Açıklama|Değer|
|-|-|-|-|
|startDate|`long`|Belirli bir tarihten sonraki müşterileri getirir. Timestamp (milliseconds) ve GMT +3 olarak gönderilmelidir.||
|endDate|`long`|Belirtilen tarihe kadar olan müşterileri getirir. Timestamp (milliseconds) ve GMT +3 olarak gönderilmelidir.| 
|page|`int`|Sadece belirtilen sayfadaki bilgileri döndürür	| 
|size|`int`|Bir sayfada listelenecek maksimum adeti belirtir.|max 200| 
|customerId|`string`|Comlab Müşteri Uniq Numarası|| 
|firstname|`string`|Müşteri Adı|| 
|lastname|`string`|Müşteri Soyadı|| 
|email|`string`|Müşteri Email|| 
|phone|`string`|Müşteri Telefon|format:5999999999| 


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
            "CustomerId": "5e73dd9a63eba06028fa1ffc",
            "CustomerCode": "5e73dd9a63eba06028fa1ffc",
            "Username": null,
            "FirstName": "ahmet",
            "LastName": "mehmet",
            "Company": null,
            "MobilePhone": "",
            "Email": "abc@abc.net",
            "Telephone": null,
            "Fax": null,
            "TaxOffice": null,
            "TaxNumber": null,
            "IdentificationNumber": null,
            "ErpCustomerCode": null,
            "IsNewsletterSubscriber": false,
            "Gender": "",
            "DateOfBirth": "1.01.1900 00:00:00",
            "CustomerNumber": 0,
            "CreatedOn": "2020-03-19T21:01:14.363Z",
            "UpdatedOn": "2021-06-10T09:30:49.513Z",
            "IntegrationId": "WEB",
            "Addresses": [],
            "CustomerPreferenceHistories": [
                {
                    "CustomerId": "5e73dd9a63eba06028fa1ffc",
                    "ContractId": "string",
                    "Type": "ETK",
                    "CreatedDate": "2021-05-19T13:07:43.243Z",
                    "IpAddress": null,
                    "ETKCallPermission": true,
                    "ETKEmailPermission": true,
                    "ETKSmsPermission": true,
                    "KVKKAddressPermission": false,
                    "KVKKCanShareWithForeignCountries": false,
                    "KVKKCanShareWithThirdParty": false
                },
                {
                    "CustomerId": "5e73dd9a63eba06028fa1ffc",
                    "ContractId": "string",
                    "Type": "KVKK",
                    "CreatedDate": "2021-05-19T13:07:43.243Z",
                    "IpAddress": null,
                    "ETKCallPermission": false,
                    "ETKEmailPermission": false,
                    "ETKSmsPermission": false,
                    "KVKKAddressPermission": true,
                    "KVKKCanShareWithForeignCountries": true,
                    "KVKKCanShareWithThirdParty": true
                }
            ]
        },
	]
}
```

> Response için örnek c# sınıfları
```csharp
public class CustomerResult
    {
        public int Page { get; set; }
        public int Size { get; set; }
        public int TotalPages { get; set; }
        public int TotalElements { get; set; }
        public List<CustomerItem> Content { get; set; }

		public class CustomerItem
		{
			public string CustomerId { get; set; }
			public string CustomerCode { get; set; }
			public string Username { get; set; }
			public string FirstName { get; set; }
			public string LastName { get; set; }
			public string Company { get; set; }
			public string MobilePhone { get; set; }
			public string Email { get; set; }
			public string Telephone { get; set; }
			public string Fax { get; set; }
			public string TaxOffice { get; set; }
			public string TaxNumber { get; set; }
			public string IdentificationNumber { get; set; }
			public string ErpCustomerCode { get; set; }
			public bool IsNewsletterSubscriber { get; set; }
			public string Gender { get; set; }
			public string DateOfBirth { get; set; }
			public long CustomerNumber { get; set; }
            public DateTime CreatedOn { get; set; }
            public DateTime UpdatedOn { get; set; }
            public string IntegrationId { get; set; }

            public List<CustomerAddress> Addresses { get; set; }

			public List<PreferenceHistory> CustomerPreferenceHistories { get; set; }

		}
        
		public class CustomerAddress
        {
            public long Id { get; set; }
            public string AddressId { get; set; }
            public string CustomerId { get; set; }
            public string FullName { get; set; }
            public string FirstName { get; set; }
            public string LastName { get; set; }
            public string MobilePhone { get; set; }
            public string Telephone { get; set; }
            public string Country { get; set; }
            public string City { get; set; }
            public string District { get; set; }
            public string Neighborhood { get; set; }
            public string AddressText { get; set; }
            public string PostCode { get; set; }
            public string ErpAddressCode { get; set; }
        }

        
        public class PreferenceHistory
        {
            public string CustomerId { get; set; }
            public string ContractId { get; set; }
            public string Type { get; set; }
            public DateTime CreatedDate { get; set; }
            public string IpAddress { get; set; }
            public bool? ETKCallPermission { get; set; }
            public bool? ETKEmailPermission { get; set; }
            public bool? ETKSmsPermission { get; set; }
            public bool? KVKKAddressPermission { get; set; }
            public bool? KVKKCanShareWithForeignCountries { get; set; }
            public bool? KVKKCanShareWithThirdParty { get; set; }
        }	
	
	}
```

# Müşteri izinlerini güncelleme

>Sonraki :  [Sipariş Güncelleme Entegrasyonu](OrderUpdate.md)