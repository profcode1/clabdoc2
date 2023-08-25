# Doğrulama İçin Token Alma API Dökümantasyonu

Bu dökümantasyon, doğrulama için token alma isteği API'sini açıklar. Bu API, kullanıcı kimlik doğrulamasını gerçekleştirerek bir erişim token'ı almanıza olanak tanır.

## API Endpoint

API, aşağıdaki endpoint'i kullanır:

```plaintext
POST https://api.oms.prod.hebiar.com/Auth/login
```

## İstek Başlıkları

- `Content-Type`: İstekte gönderilen içeriğin medya türünü belirtir (örn. application/json).

## İstek Verileri

Aşağıdaki örnek, API'ye gönderilecek istek verilerini gösterir:

```json
{
    "UserName": "sampleusername",
    "Password":"samplepassword"
}
```

- `UserName`: Kullanıcı adı.
- `Password`: Parola.


## İstek Örneği

Aşağıdaki örnek, API'ye istek yapmanın bir örneğini gösterir:

```bash
curl --location 'https://api.oms.prod.hebiar.com/Auth/login' 
--header 'Content-Type: application/json' 
--data-raw '{
    "UserName": "sampleusername",
    "Password":"samplepassword"
}'
```

## Dönüş

API isteğine verilen dönüş aşağıdaki gibidir:

```json
{
    "token": "alınan-token-degeri",
    "expire": "2023-09-24T14:10:46Z",
    "isSuccess": true,
    "statusCode": null
}
```

- `token`: Erişim token'ı.
- `expire`: Token'ın son kullanma tarihi.
- `isSuccess`: İstek başarılı ise true, aksi halde false.
- `statusCode`: İstek durum kodu.


