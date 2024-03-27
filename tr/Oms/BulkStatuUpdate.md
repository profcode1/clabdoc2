# Toplu Statü Güncelleme

Bu API, sipariş paketleri statülerinin toplu olarak güncellenmesinde kullanlır. 

## API Endpoint

`POST https://api.oms.awstest.hebiar.com/OrderPackage/SetOrderPackageStatusInfoList`

## API Yetkilendirmesi

Bu API'yi kullanabilmek için geçerli bir yetkilendirme belirteci (token) gereklidir. Yetkilendirme belirteci, 'Authorization' başlığı ile isteğe eklenmelidir.

## API İsteği

Aşağıdaki `curl` komutu ile API'ye istek yapabilirsiniz:

```bash
curl --location 'https://api.oms.awstest.hebiar.com/OrderPackage/SetOrderPackageStatusInfoList' \
--header 'Content-Type: application/json' \
--header 'authorization: Bearer token' \
--data-raw '[
    {
        "SourcePackageId": "BB_pid1707338188636",
        "Status": "Shipped"
    },
    {
        "SourcePackageId": "BB_pid1707338183915",
        "Status": "Delivered"
    }
]'

### Parametreler

- `SourcePackageId`: Kargo bilgilerinin atanacağı paketin kaynak paket numarası (Zorunlu)
- `Status`: Güncellenecek statü


## Örnek API Yanıtı

Aşağıda API'nin örnek bir yanıtı yer almaktadır:

```json
{
  "success": true,
  "message": "Paketlerin durumu başarıyla güncellendi.",
  "updatedPackages": [
    {
      "SourcePackageId": "BB_pid1707338188636",
      "Status": "Shipped"
    },
    {
      "SourcePackageId": "BB_pid1707338183915",
      "Status": "Delivered"
    }
  ]
}

