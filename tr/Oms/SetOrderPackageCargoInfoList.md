# SetOrderPackageCargoInfoList

## API Tanımı

Sipariş paketlerine kargo bilgilerini set etme servisi MCC’nin paketlere kargo bilgilerinin set ederken kullandığı servistir. Statüyü set edilebilmesi için paketin Picked veya Invoiced olması gerekir.


## API Endpoint

PUT `{path_the_comlab_oms_api}/OrderPackage/SetOrderPackageInvoiceInfoList`

## API Yetkilendirmesi

Bu API'yi kullanabilmek için geçerli bir yetkilendirme belirteci (token) gereklidir. Yetkilendirme belirteci, 'Authorization' başlığı ile isteğe eklenmelidir.

## API İsteği

Aşağıdaki `curl` komutu ile API'ye istek yapabilirsiniz:

```bash
curl --location '{path_the_comlab_oms_api}/OrderPackage/SetOrderPackageCargoInfoList' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfX3ZlbmRvYXJfXyI6IjIiLCJfX3RlbmFudF9fIjoiQTEwMSIsImlzUHJvZHVjdENyZWF0b3IiOiJ0cnVlIiwiaHR0cDovL3NjaGVtYXMueG1sc29hcC5vcmcvd3MvMjAwNS8wNS9pZGVudGl0eS9jbGFpbXMvbmFtZSI6Inlhc2luLnRla2VyQGNvbW1lcmNlbGFiLmNvbS50ciIsImh0dHA6Ly9zY2hlbWFzLnhtbHNvYXAub3JnL3dzLzIwMDUvMDUvaWRlbnRpdHkvY2xhaW1zL21vYmlsZXBob25lIjoiIiwiaHR0cDovL3NjaGVtYXMueG1sc29hcC5vcmcvd3MvMjAwNS8wNS9pZGVudGl0eS9jbGFpbXMvbmFtZWlkZW50aWZpZXIiOiI2ODA3YWU3MC0xZDdmLTQxNTMtODhjNS1hMmFlOTQ2ZDM3NDUiLCJqdGkiOiI0MWM0YjVhYi0zNDgwLTQxZDctODYwMS0yYzUzOGRkOWI2NTkiLCJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9naXZlbm5hbWUiOiJ5YXNpbi50ZWtlckBjb21tZXJjZWxhYi5jb20udHIiLCJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9zdXJuYW1lIjoic3RyaW5nIiwiaHR0cDovL3NjaGVtYXMueG1sc29hcC5vcmcvd3MvMjAwNS8wNS9pZGVudGl0eS9jbGFpbXMvZW1haWxhZGRyZXNzIjoieWFzaW4udGVrZXJAY29tbWVyY2VsYWIuY29tLnRyIiwiX190ZW5hbnRJZF9fIjoiOCIsImh0dHA6Ly9zY2hlbWFzLm1pY3Jvc29mdC5jb20vd3MvMjAwOC8wNi9pZGVudGl0eS9jbGFpbXMvcm9sZSI6IlRlbmFudEFkbWluIiwiZXhwIjoxNzEwNzkxNjY4LCJpc3MiOiJ3d3cuY29tbWVyY2VsYWIuY29tLnRyIiwiYXVkIjoid3d3LmNvbW1lcmNlbGFiLmNvbS50ciJ9.IaLPUeTCdt48pRHFlSmRyau0WY6ARI-0-t7g4k6Crr8' \
--data '[
    {
        "SourcePackageId": "BB_pid1707829159836",
        "CargoCompany":"ARS",
        "CargoKey": "CRGKEY",
        "CargoBarcode": "324513451234",
        "TrackingNumber": "TRACKINGNUMBER",
        "TrackingUrl": "https://trackinglink.com/BB_pid1705672220960",
        "isChangeStatus":true
    }
]'
```


### Parametreler

- `SourcePackageId`: Kargo bilgilerinin atanacağı paketin kaynak paket numarası (Zorunlu)
- `CargoCompany`: Kargo firması
- `CargoKey`: Kargo anahtarı
- `CargoBarcode`: Kargo barkodu
- `TrackingNumber`: Takip numarası
- `TrackingUrl`: Takip bağlantısı
- `isChangeStatus`: Statü Değişikliği Yapılsın mı? (Zorunlu)


## API Yanıtı

Aşağıda API'nin örnek bir yanıtı yer almaktadır:

```json
{
    "isSuccess": false,
    "statusCode": 0,
    "errorMesssage": "BB_pid1707829159836 paketinin statüsü uygun değil!"
}
```

### Yanıt Alanları ve Açıklamaları

- `isSuccess`: İşlem başarılı mı?
- `statusCode`: Durum kodu
- `errorMessage`: Hata mesajı
