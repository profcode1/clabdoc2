# Sipariş Paketlerini Çekme

Bu API, sipariş paketlerini çekmek için kullanılır.

## API İsteği

Aşağıdaki `curl` komutu ile API'ye istek yapabilirsiniz:

```bash
curl --location '{path_the_comlab_oms_api}/orders/GetOrderPackages?page=0&size=15&orderByField=orderDate&orderByDirection=DESC&StartDate=1704099392000&EndDate=null&OrderNumber=&Status=&CustomerCode=null&CustomerId=null&CustomerFirstName=null&CustomerLastName=null&CustomerPhone=&CustomerEmail=&IsGuest=null' \
--header 'authorization: Bearer token'
```

### Parametreler

| Parametre          | Değer                       | Değer Açıklaması                                       |
| ------------------ | --------------------------- | -------------------------------------------------------|
| page               | 10                          | İstenen sayfa numarası                                 |
| size               | 15                          | Sayfa başına dönecek maksimum öğe sayısı               |
| orderByField       | orderDate                   | Sıralama için kullanılacak alan adı                    |
| orderByDirection   | DESC                        | Sıralama yönü (ASC veya DESC)                          |
| StartDate          | 1641774294                  | Başlangıç tarihi (Unix timestamp formatında)           |
| EndDate            | 1641774294                  | Bitiş tarihi (Unix timestamp formatında)               |
| OrderNumber        | null                        | Sipariş numarası (null ise filtrelenmez)               |
| Status             | null                        | Sipariş durumu (null ise filtrelenmez)                 |
| CustomerCode       | null                        | Müşteri kodu (null ise filtrelenmez)                   |
| CustomerId         | null                        | Müşteri ID'si (null ise filtrelenmez)                  |
| CustomerFirstName  | null                        | Müşteri adı (null ise filtrelenmez)                    |
| CustomerLastName   | null                        | Müşteri soyadı (null ise filtrelenmez)                 |
| CustomerPhone      | null                        | Müşteri telefon numarası (null ise filtrelenmez)       |
| CustomerEmail      | null                        | Müşteri e-posta adresi (null ise filtrelenmez)         |
| IsGuest            | null                        | Misafir müşteri olup olmadığı (null ise filtrelenmez)  |


### Yanıt Alanları ve Açıklamaları

```json

{
  "isSuccess": true,
  "statusCode": "string",          // Durum kodu
  "errorMesssage": "string",       // Hata mesajı
  "errorSource": "string",         // Hata kaynağı
  "correlationId": "string",       
  "errors": [
    {
      "code": "string",            // Hata kodu
      "message": "string"          // Hata mesajı
    }
  ],
  "data": [
    {
      "shipmentAddress": {
        "id": 0,                    // Adres ID, ilgili sipariş için yaratılmış olan adresin ID'sidir. CL'den gelecektir. 
        "firstName": "string",      // Alıcı adı
        "lastName": "string",       // Alıcı soyadı
        "fullAddress": "string"     // Tam adres
      },
      "lines": [
        {
          "quantity": 0,            // Ürün miktarı
          "productSize": "string",   // Ürün boyutu
          "vendorSku": "string",     // Satıcı SKU, MC bunu kullanmayacaktır. 
          "productName": "string",   // Ürün adı
          "discountDetails": [
            {
              "discountTypeId": "string",   // İndirim türü ID, siparişte indirim varsa uygulanan indirim tipinin ID'sini belirtir. 
              "couponCode": "string",       // Varsa kupon kodu
              "discountId": "string",       // İndirim ID
              "amount": 0,                  // İndirim miktarı
              "realAmount": 0,              // Gerçek indirim miktarı
              "discountName": "string",     // İndirim adı
              "discountCode": "string"      // İndirim kodu
            }
          ],
          "itemLines": [ 
            {
              "id": 0,                     // Ürün satırı ID, satın alınan ürünün id'sidir, CL'den gelecektir. 
              "productName": "string",    // Ürün adı
              "sourceOrderItemLineId": "string",  // 
              "sourceOrderItemId": "string",      // 
              "orderItemId": 0,           // 
              "orderId": 0,               // Sipariş ID
              "sku": "string",            // SKU
              "barcode": "string",        // Barkod
              "vendorId": 0,              // Satıcı ID, MC burayı kullanmayacak
              "lastPackageId": 0,         // 
              "lastPackageItemId": 0,     // 
              "quantity": 0,              // Miktar
              "isReturn": true,           // Pakette iade var mı?
              "returnReason": "string",   // İade nedeni
              "returnReasonDesc": "string",       // İade nedeni açıklaması
              "isCancel": true,           // İptal durumu
              "rejectReason": "string",   // İptal nedeni
              "rejectReasonDesc": "string",       // İptal nedeni açıklaması
              "isAvaibleCancelRequest": true,    // Paket iptal edilebilir mi?
              "isAvaibleReturnRequest": true,    // Paket iade edilebilir mi?
              "saleTotal": 0,             // Toplam satış
              "returnLineAttachments": [
                {
                  "returnLineAttachmentId": 0,   // İade ek doküman ID
                  "fileName": "string",           // Dosya adı
                  "extension": "string"           // Dosya uzantısı
                }
              ]
            }
          ],
          "productColor": "string",   // Ürün rengi
          "id": 0,                     // ID, Ürün ID'sidir. CL'den gelecek. 
          "sku": "string",             // SKU
          "barcode": "string",         // Barkod
          "productPrice": 0,           // Ürün fiyatı
          "listPrice": 0,              // Liste fiyatı
          "productImageUrl": "string", // Ürün resmi URL'si
          "dueDate": "string",         // Bitiş tarihi
          "currency": "string"         // Para birimi
        }
      ],
      "parcels": [
        {
          "orderPackage": 0,          // Sipariş paketi ID, CL'den gelecek.
          "carrierCompany": 0,        // Taşıyıcı şirket ID
          "parcelOrderNo": 0,         // Paket sipariş numarası
          "parcelBarcode": "string",  // Paket barkodu
          "cargoKey": "string",       // Kargo anahtarı
          "cargoBarcode": "string",   // Kargo barkodu
          "trackingCode": "string",   // Takip kodu
          "trackingURL": "string"     // Takip URL'si
        }
      ],
      "invoiceAddress": {
        "id": 0,                     // Fatura adresi ID
        "firstName": "string",       // Fatura adı
        "lastName": "string",        // Fatura soyadı
        "fullAddress": "string",     // Tam adres
        "taxOffice": "string",       // Vergi dairesi
        "taxNumber": "string"        // Vergi numarası
      },
      "packageHistories": [
        {
          "createdDate": "string",   // Oluşturulma tarihi
          "status": "string"         // Durum
        }
      ],
      "payment": {
        "iban": "string"             // IBAN
      },
      "sourcePackageId": "string",   // Kaynak paket ID
      "orderNumber": "string",       // Sipariş numarası
      "taxNumber": "string",         // Vergi numarası
      "customerCode": "string",      // Müşteri kodu
      "customerId": 0,               // Müşteri ID
      "customerFirstName": "string", // Müşteri adı
      "customerLastName": "string",  // Müşteri soyadı
      "customerEmail": "string",     // Müşteri e-posta
      "cargoTrackingNumber": "string",   // Kargo takip numarası
      "cargoTrackingLink": "string",     // Kargo takip linki
      "cargoCode": "string",             // Kargo kodu
      "orderDate": "string",             // Sipariş tarihi
      "dueDate": "string",               // Teslim tarihi
      "status": "string",                // Sipariş durumu
      "totalListPrice": 0,               // Toplam liste fiyatı
      "totalProductPrice": 0,            // Toplam ürün fiyatı
      "lastModifiedDate": "string",      // Son güncelleme tarihi
      "vendorCode": "string",            // Satıcı kodu
      "vendorCompanyName": "string",    // Satıcı şirket adı
      "cargoName": "string",             // Kargo şirketi adı
      "channelCode": "string",           // Kanal kodu
      "channelName": "string"            // Kanal adı
    }
  ],
  "resultCount": 0,                    // Sonuç sayısı
  "totalResultCount": 0,               // Toplam sonuç sayısı
  "pageSize": 0,                       // Sayfa boyutu
  "totalPages": 0,                      // Toplam sayfa sayısı
  "currentPage": 0                     // Mevcut sayfa
}
```

## Örnek API Yanıtı

Aşağıda API'nin örnek bir yanıtı yer almaktadır:

```json
{
    "resultCount": 1,
    "totalResultCount": 1,
    "pageSize": 5,
    "totalPages": 1,
    "currentPage": 0,
    "isSuccess": true,
    "statusCode": "200",
    "data": [
        {
            "shipmentAddress": {
                "id": 894336,
                "firstName": "ALİ",
                "lastName": "HAZAR",
                "company": null,
                "address1": "Zaviye, ***** / ***",
                "address2": "-",
                "city": "Malatya",
                "cityCode": null,
                "district": "Yeşilyurt",
                "districtId": null,
                "postalCode": "11111",
                "countryCode": "TR",
                "neighborhoodId": null,
                "neighborhood": "Zaviye",
                "phone": "905312250102",
                "fullName": "ALİ HAZAR",
                "fullAddress": "Zaviye, ***** / ***",
            },
            "lines": [
                {
                    "quantity": 1,
                    "productSize": null,
                    "vendorSku": null,
                    "productName": "Beestar Çizim Seti 4'lü",
                    "discountDetails": [],
                    "itemLines": [
                        {
                            "id": 851696,
                            "productName": "Beestar Çizim Seti 4'lü",
                            "sourceOrderItemLineId": "3124010971725196-26014919-1",
                            "sourceOrderItemId": "3124010971725196-26014919",
                            "orderItemId": 785144,
                            "orderId": 402396,
                            "sku": "26014919",
                            "barcode": "8690345727803",
                            "vendorId": null,
                            "lastPackageId": 448139,
                            "lastPackageItemId": 848412,
                            "quantity": 1,
                            "isReturn": null,
                            "returnReason": "Vazgeçtim",
                            "returnReasonDesc": "-",
                            "isCancel": true,
                            "rejectReason": null,
                            "rejectReasonDesc": null,
                            "isAvaibleCancelRequest": false,
                            "isAvaibleReturnRequest": false,
                            "saleTotal": 5.62,
                            "returnLineAttachments": null
                        }
                    ],
                    "productColor": null,
                    "id": 848412,
                    "sku": "26014919",
                    "barcode": "8690345727803",
                    "productPrice": 7.5,
                    "listPrice": 7.5,
                    "productImageUrl": "8/26014919DEFAULT/26014919DEFAULT_857.jpg",
                    "dueDate": "2024-01-12T13:41:26.585+03:00",
                    "currency": "TRY"
                }
            ],
            "parcels": [],
            "invoiceAddress": {
                "id": 894335,
                "firstName": "ALİ",
                "lastName": "HAZAR",
                "company": null,
                "address1": "Zaviye, ***** / ***",
                "address2": "-",
                "city": "Malatya",
                "cityId": null,
                "district": "Yeşilyurt",
                "districtId": null,
                "postalCode": "11111",
                "countryCode": "TR",
                "neighborhoodId": null,
                "neighborhood": "Zaviye",
                "phone": "905312250102",
                "fullName": "ALİ HAZAR",
                "fullAddress": "Zaviye, ***** / ***",
                "taxOffice": null,
                "taxNumber": null
            },
            "packageHistories": [
                {
                    "createdDate": "2023-01-01T03:00:00+03:00",
                    "status": "Cancelled"
                }
            ],
            "payment": {
                "captureTransactionResult": null,
                "captureTransactionId": null,
                "authorizationTransactionResult": null,
                "authorizationTransactionCode": null,
                "authorizationTransactionId": null,
                "cardExpirationYear": null,
                "subscriptionTransactionId": null,
                "cardExpirationMonth": null,
                "maskedCreditCardNumber": null,
                "cardNumber": null,
                "cardName": null,
                "cardType": null,
                "cardFamily": null,
                "cardIssuer": null,
                "bankName": null,
                "fraudScore": null,
                "posName": null,
                "allowStoringCreditCardNumber": null,
                "cardCvv2": null,
                "paidDateUtc": null,
                "installmentCount": null,
                "paymentStatus": null,
                "total": null,
                "paymentMethod": null,
                "paymentType": null,
                "paymentAgent": null,
                "transferBankName": null,
                "iban": null
            },
            "sourcePackageId": "5303724133",
            "orderNumber": "3124010971725196",
            "taxNumber": null,
            "customerCode": "b2F5CeP0eE4oBePRkWQrlcqf",
            "customerFirstName": "ALİ",
            "customerEmail": "ali.hazar@outlook.com.tr",
            "customerId": 402380,
            "customerLastName": "HAZAR",
            "id": 448139,
            "cargoTrackingNumber": "242452881425",
            "cargoTrackingLink": "https://sube.sendeo.com.tr/takip?ccode=345326&musref=5303724133&hash=C7159DD7EF287A1D3CF193F3005F4898",
            "cargoCode": "SND",
            "cargoKey": "5303724133",
            "cargoBarcode": null,
            "cargoAggrementTypeCode": null,
            "orderDate": "2024-01-09T10:41:26.585+03:00",
            "dueDate": "2024-01-12T13:41:26.585+03:00",
            "status": "Cancelled",
            "totalListPrice": 7.5,
            "totalProductPrice": 7.5,
            "lastModifiedDate": "2024-01-09T10:43:13.262892+03:00",
            "vendorCode": null,
            "vendorCompanyName": null,
            "cargoName": "Sendeo Kargo",
            "channelCode": "WEB",
            "channelName": "A101 WebShop"
        }
    ]
}
```
