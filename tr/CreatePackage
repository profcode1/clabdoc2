# Paket Yaratma

# Api

Method:`POST`

Security:`Basic Auth` , `Bearer Token`

URL:`{path_the_comlab_oms_api}/orders/createpackage`

Request Body:
```json
{
  "sourceOrderId": "string",
  "sourceOrderNumber": "string",
  "packages": [
    {
      "sourcePackageId": "string",
      "lastModifiedDate": "2023-07-20T11:56:24.980Z",
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
      "erpOrderCreateDate": "2023-07-20T11:56:24.980Z",
      "vendorCode": "string",
      "cargoIsChangeable": true
    }
  ]
}

```
POSTMAN / Curl
```sh
curl --location '{path_the_comlab_oms_api}/orders/createpackage' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer ...token...' \
--data-raw '[
   {
  "sourceOrderId": "string",
  "sourceOrderNumber": "string",
  "packages": [
    {
      "sourcePackageId": "string",
      "lastModifiedDate": "2023-07-20T11:56:24.980Z",
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
      "erpOrderCreateDate": "2023-07-20T11:56:24.980Z",
      "vendorCode": "string",
      "cargoIsChangeable": true
    }
  ]
}
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
