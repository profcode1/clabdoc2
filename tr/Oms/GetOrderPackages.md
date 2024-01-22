# Sipariş Paketlerini Çekme

Bu API, sipariş paketlerini çekmek için kullanılır.

## API İsteği

Aşağıdaki `curl` komutu ile API'ye istek yapabilirsiniz:

```bash
curl --location 'https://api.oms.prod.hebiar.com/orders/GetOrderPackages?page=0&size=15&orderByField=orderDate&orderByDirection=DESC&StartDate=1704099392000&EndDate=null&OrderNumber=&Status=&CustomerCode=null&CustomerId=null&CustomerFirstName=null&CustomerLastName=null&CustomerPhone=&CustomerEmail=&IsGuest=null' \
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


## API Yanıtı

Aşağıda API'nin örnek bir yanıtı yer almaktadır:

```json
{
  "isSuccess": true,
  "statusCode": "string",
  "errorMesssage": "string",
  "errorSource": "string",
  "correlationId": "string",
  "errors": [
    {
      "code": "string",
      "message": "string"
    }
  ],
  "data": [
    {
      "shipmentAddress": { // Teslimat Adresi ile ilgili bilgiler
        "id": 0,
        "firstName": "string", // İsim
        "lastName": "string", // Soyisim
        ...
        "fullAddress": "string" // Müşterinin tam adresi
      },
      ...
      "payment": { // Ödeme ile ilgili detaylar bu alanda gelecek
        ...
        "iban": "string"
      },
      ...
      "channelName": "string"
    }
  ],
  "resultCount": 0,
  "totalResultCount": 0,
  "pageSize": 0,
  "totalPages": 0,
  "currentPage": 0
}
```

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
