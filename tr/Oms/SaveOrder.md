# Sipariş Kaydetme

# Api

Method:`POST`

Security:`Basic Auth` , `Bearer Token`

URL:`{path_the_comlab_oms_api}/orders/saveorders`

Request Body:
```json
[
  {
    "orderId": "string",
    "orderNumber": "string",
    "channelCode": "string",
    "supplier": "string",
    "orderDate": "2023-07-20T11:08:37.774Z",
    "applicationId": 0,
    "deviceCode": "string",
    "storeId": 0,
    "posId": 0,
    "cashierId": 0,
    "orderSourceTypeCode": "string",
    "erpOrderNumber": "string",
    "isGuest": true,
    "description": "string",
    "packages": [
      {
        "sourcePackageId": "string",
        "lastModifiedDate": "2023-07-20T11:08:37.774Z",
        "lastStatus": "string",
        "packageItems": [
          {
            "sourceOrderItemId": "string",
            "saleTotal": 0,
            "quantity": 0,
            "vendorSku": "string"
          }
        ],
        "shipmentAddress": {
          "sourceAddressId": "string",
          "addressType": "string",
          "firstName": "string",
          "lastName": "string",
          "companyName": "string",
          "phone": "string",
          "addressLine1": "string",
          "addressLine2": "string",
          "zipCode": "string",
          "countryName": "string",
          "cityName": "string",
          "districtName": "string",
          "neighbourhoodName": "string",
          "identityNumber": "string",
          "taxOffice": "string",
          "taxNumber": "string"
        },
        "shipmentAddressId": "string",
        "invoiceAddress": {
          "sourceAddressId": "string",
          "addressType": "string",
          "firstName": "string",
          "lastName": "string",
          "companyName": "string",
          "phone": "string",
          "addressLine1": "string",
          "addressLine2": "string",
          "zipCode": "string",
          "countryName": "string",
          "cityName": "string",
          "districtName": "string",
          "neighbourhoodName": "string",
          "identityNumber": "string",
          "taxOffice": "string",
          "taxNumber": "string"
        },
        "invoiceAddressId": "string",
        "erpOrderNumber": "string",
        "erpOrderCreateDate": "2023-07-20T11:08:37.774Z",
        "vendorCode": "string",
        "cargoIsChangeable": true
      }
    ],
    "customer": {
      "customerId": "string",
      "customerCode": "string",
      "firstName": "string",
      "lastName": "string",
      "phone": "string",
      "mobilePhone": "string",
      "email": "string",
      "identityNumber": "string",
      "taxNumber": "string"
    },
    "items": [
      {
        "sourceOrderItemId": "string",
        "productName": "string",
        "sku": "string",
        "productPhotoPath1": "string",
        "barcode": "string",
        "quantity": 0,
        "productPrice": 0,
        "listPrice": 0,
        "saleTotal": 0,
        "vendorId": 0,
        "salesRepresentativeId": 0,
        "currency": "string",
        "lines": [
          {
            "sourceOrderItemLineId": "string",
            "saleTotal": 0
          }
        ]
      }
    ],
    "payments": [
      {
        "paymentType": "string",
        "paymentStatus": 0,
        "captureTransactionResult": "string",
        "captureTransactionId": "string",
        "authorizationTransactionResult": "string",
        "authorizationTransactionCode": "string",
        "authorizationTransactionId": "string",
        "cardExpirationYear": "string",
        "subscriptionTransactionId": "string",
        "cardExpirationMonth": "string",
        "maskedCreditCardNumber": "string",
        "cardNumber": "string",
        "cardName": "string",
        "cardType": "string",
        "cardFamily": "string",
        "cardIssuer": "string",
        "bankName": "string",
        "posName": "string",
        "cardCvv2": "string",
        "paidDateUtc": "2023-07-20T11:08:37.774Z",
        "installmentCount": 0,
        "paymentAgent": "string"
      }
    ],
    "addresses": [
      {
        "sourceAddressId": "string",
        "addressType": "string",
        "firstName": "string",
        "lastName": "string",
        "companyName": "string",
        "phone": "string",
        "addressLine1": "string",
        "addressLine2": "string",
        "zipCode": "string",
        "countryName": "string",
        "cityName": "string",
        "districtName": "string",
        "neighbourhoodName": "string",
        "identityNumber": "string",
        "taxOffice": "string",
        "taxNumber": "string"
      }
    ]
  }
]

```
POSTMAN / Curl
```sh
curl --location '{path_the_comlab_oms_api}/orders/saveorders' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer ...token...' \
--data-raw '[
    [
  {
    "orderId": "string",
    "orderNumber": "string",
    "channelCode": "string",
    "supplier": "string",
    "orderDate": "2023-07-20T11:08:37.774Z",
    "applicationId": 0,
    "deviceCode": "string",
    "storeId": 0,
    "posId": 0,
    "cashierId": 0,
    "orderSourceTypeCode": "string",
    "erpOrderNumber": "string",
    "isGuest": true,
    "description": "string",
    "packages": [
      {
        "sourcePackageId": "string",
        "lastModifiedDate": "2023-07-20T11:08:37.774Z",
        "lastStatus": "string",
        "packageItems": [
          {
            "sourceOrderItemId": "string",
            "saleTotal": 0,
            "quantity": 0,
            "vendorSku": "string"
          }
        ],
        "shipmentAddress": {
          "sourceAddressId": "string",
          "addressType": "string",
          "firstName": "string",
          "lastName": "string",
          "companyName": "string",
          "phone": "string",
          "addressLine1": "string",
          "addressLine2": "string",
          "zipCode": "string",
          "countryName": "string",
          "cityName": "string",
          "districtName": "string",
          "neighbourhoodName": "string",
          "identityNumber": "string",
          "taxOffice": "string",
          "taxNumber": "string"
        },
        "shipmentAddressId": "string",
        "invoiceAddress": {
          "sourceAddressId": "string",
          "addressType": "string",
          "firstName": "string",
          "lastName": "string",
          "companyName": "string",
          "phone": "string",
          "addressLine1": "string",
          "addressLine2": "string",
          "zipCode": "string",
          "countryName": "string",
          "cityName": "string",
          "districtName": "string",
          "neighbourhoodName": "string",
          "identityNumber": "string",
          "taxOffice": "string",
          "taxNumber": "string"
        },
        "invoiceAddressId": "string",
        "erpOrderNumber": "string",
        "erpOrderCreateDate": "2023-07-20T11:08:37.774Z",
        "vendorCode": "string",
        "cargoIsChangeable": true
      }
    ],
    "customer": {
      "customerId": "string",
      "customerCode": "string",
      "firstName": "string",
      "lastName": "string",
      "phone": "string",
      "mobilePhone": "string",
      "email": "string",
      "identityNumber": "string",
      "taxNumber": "string"
    },
    "items": [
      {
        "sourceOrderItemId": "string",
        "productName": "string",
        "sku": "string",
        "productPhotoPath1": "string",
        "barcode": "string",
        "quantity": 0,
        "productPrice": 0,
        "listPrice": 0,
        "saleTotal": 0,
        "vendorId": 0,
        "salesRepresentativeId": 0,
        "currency": "string",
        "lines": [
          {
            "sourceOrderItemLineId": "string",
            "saleTotal": 0
          }
        ]
      }
    ],
    "payments": [
      {
        "paymentType": "string",
        "paymentStatus": 0,
        "captureTransactionResult": "string",
        "captureTransactionId": "string",
        "authorizationTransactionResult": "string",
        "authorizationTransactionCode": "string",
        "authorizationTransactionId": "string",
        "cardExpirationYear": "string",
        "subscriptionTransactionId": "string",
        "cardExpirationMonth": "string",
        "maskedCreditCardNumber": "string",
        "cardNumber": "string",
        "cardName": "string",
        "cardType": "string",
        "cardFamily": "string",
        "cardIssuer": "string",
        "bankName": "string",
        "posName": "string",
        "cardCvv2": "string",
        "paidDateUtc": "2023-07-20T11:08:37.774Z",
        "installmentCount": 0,
        "paymentAgent": "string"
      }
    ],
    "addresses": [
      {
        "sourceAddressId": "string",
        "addressType": "string",
        "firstName": "string",
        "lastName": "string",
        "companyName": "string",
        "phone": "string",
        "addressLine1": "string",
        "addressLine2": "string",
        "zipCode": "string",
        "countryName": "string",
        "cityName": "string",
        "districtName": "string",
        "neighbourhoodName": "string",
        "identityNumber": "string",
        "taxOffice": "string",
        "taxNumber": "string"
      }
    ]
  }
]
```
> Result
```json
{
  "isSuccess": true,
  "errorType": "string",
  "errorMesssage": "string",
  "errorSource": "string",
  "items": [
    {
      "itemCode": "string",
      "isSuccess": true,
      "errorMesssage": "string"
    }
  ]
}
```




