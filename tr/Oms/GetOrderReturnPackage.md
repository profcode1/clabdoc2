# Sipariş Paketlerini Çekme

Bu API, iade paketlerini çekmek için kullanılır.

## API İsteği

Aşağıdaki `curl` komutu ile API'ye istek yapabilirsiniz:

```bash
curl --location 'https://api.oms.prod.hebiar.com/orders/GetOrderPackages?page=0&size=15&orderByField=orderDate&orderByDirection=DESC&StartDate=1704099392000&EndDate=null&OrderNumber=&Status=&CustomerCode=null&CustomerId=null&CustomerFirstName=null&CustomerLastName=null&CustomerPhone=&CustomerEmail=&IsGuest=null' \
--header 'authorization: Bearer token'
```

# Sipariş İade Paketleri API Çağrısı Parametreleri

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


## Anahtar Bilgiler

- **isSuccess**: İstek başarılı mı değil mi?
- **statusCode**: API'nin döndüğü HTTP durum kodu.
- **errorMessage**: Hata durumunda hata mesajı.
- **errorSource**: Hata kaynağı.
- **correlationId**: İstekle ilgili ilişkilendirme kimliği.
- **errors**: Hata nesnelerinin listesi.

## data Alanı Detayları

Data alanı içinde bulunan örnek bir sipariş iade paketi detayları:

- **shipmentAddress**: Gönderim adresi bilgileri.
- **lines**: Sipariş ürünleri detayları.
- **parcels**: Kargo bilgileri.
- **invoiceAddress**: Fatura adresi bilgileri.
- **packageHistories**: Paket geçmişi bilgileri.
- **payment**: Ödeme detayları.

## Notlar
İade nedeni, iade tarihi, iade durumu gibi önemli bilgiler reason, returnDate, isConfirm gibi alanlarda bulunmaktadır.

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

- `isSuccess`: İşlem başarılı mı?
- `statusCode`: Durum kodu
- `errorMesssage`: Hata mesajı
- `errorSource`: Hata kaynağı
- `correlationId`: İlişkilendirme kimliği
- `errors`: Hatalar
- `data`: İşlem verileri
  - `shipmentAddress`: Teslimat adresi bilgileri
  - `lines`: Siparişteki ürünler
  - `payment`: Ödeme detayları
  - `packageHistories`: Paket geçmişi
    - `sourcePackageId`: MC tarafındaki paket numarası
    - `orderNumber`: Sipariş numarası
    - `taxNumber`: Vergi numarası
    - `customerCode`: Müşteri kodu
    - `customerId`: Müşteri ID'si
    - `customerFirstName`: Müşterinin adı
    - `customerLastName`: Müşterinin soyadı
    - `customerEmail`: Müşterinin e-posta adresi
    - `cargoTrackingNumber`: Kargo takip numarası
    - `cargoTrackingLink`: Kargo takip linki
    - `cargoCode`: Kargo kodu
    - `orderDate`: Sipariş tarihi
    - `dueDate`: Teslim tarihi
    - `status`: Sipariş durumu
    - `totalListPrice`: Toplam liste fiyatı
    - `totalProductPrice`: Toplam ürün fiyatı
    - `lastModifiedDate`: Son değiştirilme tarihi
    - `vendorCode`: Satıcı kodu
    - `vendorCompanyName`: Satıcı şirket adı
    - `cargoName`: Kargo şirketi adı
    - `channelCode`: Kanal kodu
    - `channelName`: Kanal adı
  - `resultCount`: Sonuç sayısı
  - `totalResultCount`: Toplam sonuç sayısı
  - `pageSize`: Sayfa boyutu
  - `totalPages`: Toplam sayfa sayısı
  - `currentPage`: Mevcut sayfa