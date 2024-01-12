# Sipariş Paketlerini Çekme

Bu API, sipariş paketlerini çekmek için kullanılır.

## API İsteği

Aşağıdaki `curl` komutu ile API'ye istek yapabilirsiniz:

```bash
curl --location 'https://api.oms.prod.hebiar.com/orders/GetOrderPackages?page=0&size=15&orderByField=orderDate&orderByDirection=DESC&StartDate=1704099392000&EndDate=null&OrderNumber=&Status=&CustomerCode=null&CustomerId=null&CustomerFirstName=null&CustomerLastName=null&CustomerPhone=&CustomerEmail=&IsGuest=null' \
--header 'authorization: Bearer token'
```

### Parametreler

- `page`: Sipariş paketlerinin alınacağı sayfa numarası (örn: 0)
- `size`: Bir sayfada görüntülenecek sipariş paketi sayısı (örn: 15)
- `orderByField`: Sıralama yapılacak alan (örn: `orderDate`)
- `orderByDirection`: Sıralama yönü (`ASC` veya `DESC`)
- `StartDate`: Başlangıç tarihi (epoch time formatında)
- `EndDate`: Bitiş tarihi (epoch time formatında, `null` ise sınırsız)
- `OrderNumber`: Sipariş numarası (boş bırakılabilir)
- `Status`: Sipariş durumu (boş bırakılabilir)
- `CustomerCode`: Müşteri kodu (boş bırakılabilir)
- `CustomerId`: Müşteri ID'si (boş bırakılabilir)
- `CustomerFirstName`: Müşterinin adı (boş bırakılabilir)
- `CustomerLastName`: Müşterinin soyadı (boş bırakılabilir)
- `CustomerPhone`: Müşterinin telefon numarası (boş bırakılabilir)
- `CustomerEmail`: Müşterinin e-posta adresi (boş bırakılabilir)
- `IsGuest`: Müşterinin konuk olup olmadığı (boş bırakılabilir)

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
```
