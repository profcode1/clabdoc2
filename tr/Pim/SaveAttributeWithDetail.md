# API Dökümantasyonu - SaveAttributeWithDetail

Bu dökümantasyon, SaveAttributeWithDetail API'sini tanımlar. Bu API, bir özellik (attribute) ve ayrıntılarıyla birlikte kaydetmek için kullanılır.

## API Endpoint Bilgisi

API'nin temel URL'i: `https://pim_api_url/pim/SaveAttributeWithDetail`

## Kullanılacak HTTP Metodu

API, `POST` HTTP metodu kullanılarak çağrılmalıdır.

Eğer "AttributeId": verilirse günceller verilmezse yeni yaratır.

## Örnek bir cURL Komutu

Aşağıda, API'yi çağırmak için kullanabileceğiniz örnek bir cURL komutu bulunmaktadır:

```plaintext
curl 'https://pim_api_url/pim/SaveAttributeWithDetail' 
  -H 'authorization: Bearer token' 
  -H 'content-type: application/json;charset=UTF-8' 
  --data-raw '{
    "AttributeId": 476,
    "Type": "Attribute",
    "MetaType": "other",
    "Name": "Renk",
    "PimSource": "renk",
    "ValidationRules": [],
    "Options": [
      {"Key": "allowFiltering", "Value": "True"},
      {"Key": "defaultValueSorting", "Value": "False"},
      {"Key": "isAutoMap", "Value": "False"},
      {"Key": "isComparable", "Value": "False"},
      {"Key": "isSameValues", "Value": "False"},
      {"Key": "isSearchable", "Value": "False"},
      {"Key": "showOnDescription", "Value": "False"},
      {"Key": "showOnProduct", "Value": "True"},
      {"Key": "splitSeperator", "Value": "/"},
      {"Key": "valueIdentifierType", "Value": "auto"}
    ],
    "Detail": {
      "AttributeId": 476,
      "AttributeDataType": "Boolean",
      "AttributeType": "Display Option",
      "AttributeRelationLevel": "Option",
      "AttributeBindingType": "All",
      "ValidationDurationUnit": null,
      "AttributeDataTypeId": 3,
      "AttributeTypeId": 2,
      "AttributeRelationLevelId": 2,
      "AttributeBindingTypeId": 3,
      "IsActive": true,
      "ValidationRecursion": null,
      "ValidationDurationUnitId": null,
      "ValidationDuration": null,
      "ValidStartDate": null,
      "ValidEndDate": null,
      "JsonConfig": null,
      "Tag": null
    },
    "ValuesDetail": []
  }'
```

Bu kod bloğunu kopyalayarak kullanabilirsiniz.
