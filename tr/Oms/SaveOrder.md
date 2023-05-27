# Sipariş Kaydetme

# Api

Method:`POST`

Security:`Basic Auth` , `Bearer Token`

URL:`{path_the_comlab_oms_api}/orders/saveorders`

Request Body:
```json
[
    {
        "orderId": "av61685196446",
        "orderNumber": "llb1685196446",
        "ChannelCode": "WEB",
        "orderDate": "2023-05-24T11:07:57.032Z",
        "Payments":[],
        "items":[
                    {
                        "SourceOrderItemId": "item1685178507565",
                        "productName": "pname1685196446",
                         "sku": "sku7",
                        "barcode": "barcode7",
                        "quantity": 2,
                        "productPrice": 880,
                        "listPrice": 306,
                        "saleTotal": 436
                    },
                    {
                        "SourceOrderItemId": "item1685178507449",
                        "productName": "pname1685196446682",
                        "sku": "sku6",
                        "barcode": "barcode6",
                        "quantity": 3,
                        "productPrice": 176,
                        "listPrice": 678,
                        "saleTotal": 777
                    }
                ],
        "packages": [
            {
                "VendorCode":"Tiamob",
                "SourcePackageId": "pid1685196446470",
                "packageItems": [
                    {
                        "SourceOrderItemId": "item1685178507565",
                        "productName": "pname1685196446",
                        "sku": "sku7",
                        "barcode": "barcode7",
                        "quantity": 1,
                        "productPrice": 346,
                        "listPrice": 533,
                        "saleTotal": 733
                    },
                    {
                        "SourceOrderItemId": "item1685178507449",
                        "productName": "pname1685196446671",
                         "sku": "sku6",
                        "barcode": "barcode6",
                        "quantity": 2,
                        "productPrice": 598,
                        "listPrice": 879,
                        "saleTotal": 829
                    }
                ],
                "shipmentAddress": {
                    "AddressType":"Shipment",
                    "SourceAddressId":"a1",
                    "firstName": "firstNameo0f",
                    "lastName": "lastNamejsi",
                    "company": "string",
                    "phone": "5991685196446",
                    "addressLine1": "address string la2 9qy",
                    "addressLine2": "jqv",
                    "zipCode": "676703",
                    "countryName": "türkiye",
                    "cityName": "istanbul",
                     "DistrictName": "sarıyer",
                    "NeighbourhoodName": "ayazağa mahallesi"
                },
                "invoiceAddress": {
                    "AddressType":"Invoice",
                    "SourceAddressId":"a2",
                    "firstName": "firstNamek0f",
                    "lastName": "lastName3d5",
                    "company": "string",
                    "phone": "5991685196446",
                    "addressLine1": "address string snm cl9",
                    "addressLine2": "gba",
                    "zipCode": "142932",
                    "countryName": "türkiye",
                    "cityName": "istanbul",
                    "DistrictName": "sarıyer",
                    "NeighbourhoodName": "ayazağa mahallesi"
                }
            },
            {
                "SourcePackageId": "pid1685196446945",
                "packageItems": [
                    {
                        "SourceOrderItemId": "item1685178507565",
                        "productName": "pname1685196446131",
                        "sku": "sku1685196446",
                        "barcode": "1685196446",
                        "quantity": 1,
                        "productPrice": 308,
                        "listPrice": 543,
                        "saleTotal": 819
                    },
                    {
                        "SourceOrderItemId": "item1685178507449",
                        "productName": "pname168519644621",
                        "sku": "sku1685196446",
                        "barcode": "1685196446",
                        "quantity": 1,
                        "productPrice": 324,
                        "listPrice": 102,
                        "saleTotal": 720
                    }
                ],
                "shipmentAddress": {
                    "AddressType":"Shipment",
                    "SourceAddressId":"a1",
                    "firstName": "firstName75q",
                    "lastName": "lastNameid2",
                    "company": "string",
                    "phone": "5991685196446",
                    "addressLine1": "address string vp1 szv",
                    "addressLine2": "gi4",
                    "zipCode": "625557",
                    "countryName": "türkiye",
                    "cityName": "istanbul",
                    "DistrictName": "sarıyer",
                    "NeighbourhoodName": "ayazağa mahallesi"
                },
                "invoiceAddress": {
                    "AddressType":"Invoice",
                    "SourceAddressId":"a2",
                    "firstName": "firstName4oq",
                    "lastName": "lastNamejyp",
                    "company": "string",
                    "phone": "5991685196446",
                    "addressLine1": "address string rzm gb0",
                    "addressLine2": "k5z",
                    "zipCode": "226871",
                    "countryName": "türkiye",
                    "cityName": "istanbul",
                     "DistrictName": "sarıyer",
                    "NeighbourhoodName": "ayazağa mahallesi"
                }
            }
        ],
        "customer": {
            "customerCode": "w2q1685196446",
            "firstName": "firstNamenhx",
            "lastName": "lastNameggz",
            "phone": "5991255456",
            "mobilePhone": "5991685196446",
            "email": "7gg9cx@string.com",
            "identityNumber": "994832771",
            "taxNumber": "204579"
        }
    }
]

```
POSTMAN / Curl
```sh
curl --location '{path_the_comlab_oms_api}/orders/saveorders' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer ...token...' \
--data-raw '[
    {
        "orderId": "av61685196446",
        "orderNumber": "llb1685196446",
        "ChannelCode": "WEB",
        "orderDate": "2023-05-24T11:07:57.032Z",
        "Payments":[],
        "items":[
                    {
                        "SourceOrderItemId": "item1685178507565",
                        "productName": "pname1685196446",
                         "sku": "sku7",
                        "barcode": "barcode7",
                        "quantity": 2,
                        "productPrice": 880,
                        "listPrice": 306,
                        "saleTotal": 436
                    },
                    {
                        "SourceOrderItemId": "item1685178507449",
                        "productName": "pname1685196446682",
                        "sku": "sku6",
                        "barcode": "barcode6",
                        "quantity": 3,
                        "productPrice": 176,
                        "listPrice": 678,
                        "saleTotal": 777
                    }
                ],
        "packages": [
            {
                "VendorCode":"Tiamob",
                "SourcePackageId": "pid1685196446470",
                "packageItems": [
                    {
                        "SourceOrderItemId": "item1685178507565",
                        "productName": "pname1685196446",
                        "sku": "sku7",
                        "barcode": "barcode7",
                        "quantity": 1,
                        "productPrice": 346,
                        "listPrice": 533,
                        "saleTotal": 733
                    },
                    {
                        "SourceOrderItemId": "item1685178507449",
                        "productName": "pname1685196446671",
                         "sku": "sku6",
                        "barcode": "barcode6",
                        "quantity": 2,
                        "productPrice": 598,
                        "listPrice": 879,
                        "saleTotal": 829
                    }
                ],
                "shipmentAddress": {
                    "AddressType":"Shipment",
                    "SourceAddressId":"a1",
                    "firstName": "firstNameo0f",
                    "lastName": "lastNamejsi",
                    "company": "string",
                    "phone": "5991685196446",
                    "addressLine1": "address string la2 9qy",
                    "addressLine2": "jqv",
                    "zipCode": "676703",
                    "countryName": "türkiye",
                    "cityName": "istanbul",
                     "DistrictName": "sarıyer",
                    "NeighbourhoodName": "ayazağa mahallesi"
                },
                "invoiceAddress": {
                    "AddressType":"Invoice",
                    "SourceAddressId":"a2",
                    "firstName": "firstNamek0f",
                    "lastName": "lastName3d5",
                    "company": "string",
                    "phone": "5991685196446",
                    "addressLine1": "address string snm cl9",
                    "addressLine2": "gba",
                    "zipCode": "142932",
                    "countryName": "türkiye",
                    "cityName": "istanbul",
                    "DistrictName": "sarıyer",
                    "NeighbourhoodName": "ayazağa mahallesi"
                }
            },
            {
                "SourcePackageId": "pid1685196446945",
                "packageItems": [
                    {
                        "SourceOrderItemId": "item1685178507565",
                        "productName": "pname1685196446131",
                        "sku": "sku1685196446",
                        "barcode": "1685196446",
                        "quantity": 1,
                        "productPrice": 308,
                        "listPrice": 543,
                        "saleTotal": 819
                    },
                    {
                        "SourceOrderItemId": "item1685178507449",
                        "productName": "pname168519644621",
                        "sku": "sku1685196446",
                        "barcode": "1685196446",
                        "quantity": 1,
                        "productPrice": 324,
                        "listPrice": 102,
                        "saleTotal": 720
                    }
                ],
                "shipmentAddress": {
                    "AddressType":"Shipment",
                    "SourceAddressId":"a1",
                    "firstName": "firstName75q",
                    "lastName": "lastNameid2",
                    "company": "string",
                    "phone": "5991685196446",
                    "addressLine1": "address string vp1 szv",
                    "addressLine2": "gi4",
                    "zipCode": "625557",
                    "countryName": "türkiye",
                    "cityName": "istanbul",
                    "DistrictName": "sarıyer",
                    "NeighbourhoodName": "ayazağa mahallesi"
                },
                "invoiceAddress": {
                    "AddressType":"Invoice",
                    "SourceAddressId":"a2",
                    "firstName": "firstName4oq",
                    "lastName": "lastNamejyp",
                    "company": "string",
                    "phone": "5991685196446",
                    "addressLine1": "address string rzm gb0",
                    "addressLine2": "k5z",
                    "zipCode": "226871",
                    "countryName": "türkiye",
                    "cityName": "istanbul",
                     "DistrictName": "sarıyer",
                    "NeighbourhoodName": "ayazağa mahallesi"
                }
            }
        ],
        "customer": {
            "customerCode": "w2q1685196446",
            "firstName": "firstNamenhx",
            "lastName": "lastNameggz",
            "phone": "",
            "mobilePhone": "5991685196446",
            "email": "7gg9cx@string.com",
            "identityNumber": "994832771",
            "taxNumber": "204579"
        }
    }
]'
```
> Result
```json
{
    "isSuccess": true,
    "items": [
        {
            "itemCode": "pl21685178507",
            "isSuccess": true
        }
    ]
}
```




