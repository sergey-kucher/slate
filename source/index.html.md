---
title: Enbro Soho API
language_tabs:
  - json: JSON
  - shell: cURL
---


# Customer create



## Failure

Returning status 422 when email already exist

### Request

#### Endpoint

```plaintext
POST /api/v1/customers
Content-Type: application/json
Authorization: Bearer 892ff6b11daa4737d19fe4bc08c27b6c
```

`POST /api/v1/customers`

#### Parameters


```json
{
  "customer": {
    "email": "clifford@mohr.com",
    "terms_and_conditions": true,
    "privacy_policy": true,
    "registered_from_ip": "98.99.253.30",
    "profile": {
      "first_name": "Danny",
      "last_name": "Ocean",
      "title": "mr",
      "phone": "+32(0)56/98.01.44",
      "birth_date": "2000-04-06",
      "city": "South Seanview",
      "street": "678 Daugherty Corner",
      "building": "71950",
      "postal_code": "15005",
      "language": "en"
    }
  }
}
```


| Name | Description |
|:-----|:------------|
| customer[email] *required* | Customer email |
| customer[terms_and_conditions] *required* | Customer terms and conditions |
| customer[privacy_policy] *required* | Customer privacy policy |
| customer[registered_from_ip] *required* | Customer registered from ip |
| customer[profile] *required* | Customer profile |
| customer[profile][first_name] *required* | Customer profile first name |
| customer[profile][last_name] *required* | Customer profile last name |
| customer[profile][title] *required* | Customer profile title |
| customer[profile][phone] *required* | Customer profile phone |
| customer[profile][birth_date] *required* | Customer profile birth date |
| customer[profile][city] *required* | Customer profile city |
| customer[profile][street] *required* | Customer profile street |
| customer[profile][building] *required* | Customer profile building |
| customer[profile][building_addon]  | Customer profile building addon |
| customer[profile][postal_code] *required* | Customer profile postal code |
| customer[profile][language]  | Values: ["nl", "fr", "en"]. Default: nl |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "error": "confirmed_email_has_already_been_taken",
      "message": "it is already registered",
      "path": "customer.email",
      "type": "custom"
    }
  ]
}
```



## Success

Returning status 200 and Customer hash

### Request

#### Endpoint

```plaintext
POST /api/v1/customers
Content-Type: application/json
Authorization: Bearer b15635ceb5c3e82e46826b17aff3d637
```

`POST /api/v1/customers`

#### Parameters


```json
{
  "customer": {
    "email": "nathalie@abernathy.co",
    "terms_and_conditions": true,
    "privacy_policy": true,
    "registered_from_ip": "108.254.248.163",
    "profile": {
      "first_name": "Danny",
      "last_name": "Ocean",
      "title": "mr",
      "phone": "+32(0)56/98.01.44",
      "birth_date": "2000-04-06",
      "city": "East Mohammedfort",
      "street": "8132 Kindra Islands",
      "building": "14346",
      "postal_code": "68658-3184",
      "language": "fr"
    }
  }
}
```


| Name | Description |
|:-----|:------------|
| customer[email] *required* | Customer email |
| customer[terms_and_conditions] *required* | Customer terms and conditions |
| customer[privacy_policy] *required* | Customer privacy policy |
| customer[registered_from_ip] *required* | Customer registered from ip |
| customer[profile] *required* | Customer profile |
| customer[profile][first_name] *required* | Customer profile first name |
| customer[profile][last_name] *required* | Customer profile last name |
| customer[profile][title] *required* | Customer profile title |
| customer[profile][phone] *required* | Customer profile phone |
| customer[profile][birth_date] *required* | Customer profile birth date |
| customer[profile][city] *required* | Customer profile city |
| customer[profile][street] *required* | Customer profile street |
| customer[profile][building] *required* | Customer profile building |
| customer[profile][building_addon]  | Customer profile building addon |
| customer[profile][postal_code] *required* | Customer profile postal code |
| customer[profile][language]  | Values: ["nl", "fr", "en"]. Default: nl |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "id": 105,
  "email": "nathalie@abernathy.co",
  "created_at": "2020-04-06T08:43:33.409Z",
  "updated_at": "2020-04-06T08:43:33.428Z",
  "profile": {
    "id": 103,
    "customer_id": 105,
    "organisation_id": 18,
    "title": "mr",
    "first_name": "Danny",
    "last_name": "Ocean",
    "birth_date": "2000-04-06",
    "phone": "+3256980144",
    "city": "East Mohammedfort",
    "street": "8132 Kindra Islands",
    "building": "14346",
    "postal_code": "68658-3184",
    "language": "fr",
    "created_at": "2020-04-06T08:43:33.411Z",
    "updated_at": "2020-04-06T08:43:33.411Z"
  }
}
```



# Customer list



## Success

Returning status 200 and array of customers

### Request

#### Endpoint

```plaintext
GET /api/v1/customers?page=1&amp;per=5
Content-Type: application/json
Authorization: Bearer 9aa0d3fb5829cf9e4c35224d23d16877
```

`GET /api/v1/customers`

#### Parameters


```json
page: 1
per: 5
```


| Name | Description |
|:-----|:------------|
| page  |  page |
| per  | Limit of records per page. Max value is 25. |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "current_page": 1,
  "limit_value": 5,
  "next_page": 2,
  "prev_page": null,
  "total_pages": 7,
  "records": [
    {
      "id": 25,
      "email": "gale@rodriguez.name",
      "created_at": "2020-04-06T08:43:32.497Z",
      "updated_at": "2020-04-06T08:43:32.497Z",
      "profile": {
        "id": 23,
        "customer_id": 25,
        "organisation_id": 9,
        "title": "mr",
        "first_name": "Roman",
        "last_name": "Ferry",
        "birth_date": "1968-12-23",
        "phone": "+3232411132",
        "city": "Franklyntown",
        "street": "Johns Route",
        "building": "3401",
        "building_addon": "Apt. 921",
        "postal_code": "88052",
        "language": "nl",
        "created_at": "2020-04-06T08:43:32.501Z",
        "updated_at": "2020-04-06T08:43:32.501Z"
      }
    },
    {
      "id": 26,
      "email": "diedre_towne@langcarroll.name",
      "created_at": "2020-04-06T08:43:32.507Z",
      "updated_at": "2020-04-06T08:43:32.507Z",
      "profile": {
        "id": 24,
        "customer_id": 26,
        "organisation_id": 9,
        "title": "mr",
        "first_name": "Santos",
        "last_name": "Bosco",
        "birth_date": "1971-02-01",
        "phone": "+3256980144",
        "city": "West Brian",
        "street": "Kohler Underpass",
        "building": "55547",
        "building_addon": "Apt. 633",
        "postal_code": "67775",
        "language": "nl",
        "created_at": "2020-04-06T08:43:32.511Z",
        "updated_at": "2020-04-06T08:43:32.511Z"
      }
    },
    {
      "id": 27,
      "email": "shad_johnston@schroeder.io",
      "created_at": "2020-04-06T08:43:32.516Z",
      "updated_at": "2020-04-06T08:43:32.516Z",
      "profile": {
        "id": 25,
        "customer_id": 27,
        "organisation_id": 9,
        "title": "mr",
        "first_name": "Dexter",
        "last_name": "Smith",
        "birth_date": "1977-09-21",
        "phone": "+3256980144",
        "city": "Rachealfurt",
        "street": "Wade Street",
        "building": "46009",
        "building_addon": "Suite 779",
        "postal_code": "04975",
        "language": "nl",
        "created_at": "2020-04-06T08:43:32.519Z",
        "updated_at": "2020-04-06T08:43:32.519Z"
      }
    },
    {
      "id": 28,
      "email": "laurice_boehm@lockman.co",
      "created_at": "2020-04-06T08:43:32.524Z",
      "updated_at": "2020-04-06T08:43:32.524Z",
      "profile": {
        "id": 26,
        "customer_id": 28,
        "organisation_id": 9,
        "title": "mr",
        "first_name": "Tracy",
        "last_name": "Becker",
        "birth_date": "1986-07-23",
        "phone": "+3232411132",
        "city": "West Lewis",
        "street": "Rich Stream",
        "building": "68499",
        "building_addon": "Suite 853",
        "postal_code": "71874",
        "language": "nl",
        "created_at": "2020-04-06T08:43:32.527Z",
        "updated_at": "2020-04-06T08:43:32.527Z"
      }
    },
    {
      "id": 29,
      "email": "marvin.prohaska@wisozkdach.io",
      "created_at": "2020-04-06T08:43:32.531Z",
      "updated_at": "2020-04-06T08:43:32.531Z",
      "profile": {
        "id": 27,
        "customer_id": 29,
        "organisation_id": 9,
        "title": "mr",
        "first_name": "Yael",
        "last_name": "Barton",
        "birth_date": "1978-02-08",
        "phone": "+3232411132",
        "city": "Michalfort",
        "street": "Krajcik Rapid",
        "building": "36435",
        "building_addon": "Suite 906",
        "postal_code": "91771",
        "language": "nl",
        "created_at": "2020-04-06T08:43:32.534Z",
        "updated_at": "2020-04-06T08:43:32.534Z"
      }
    }
  ]
}
```



# Customer show



## Failure

Returning status 404 where the customer is missing

### Request

#### Endpoint

```plaintext
GET /api/v1/customers/116
Content-Type: application/json
Authorization: Bearer 1c9696c9aaddc76d629e9f070919338d
```

`GET /api/v1/customers/:id`

#### Parameters


```json
{
}: 
```


| Name | Description |
|:-----|:------------|
| id *required* |  id |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
404 Not Found
```


```json
"Not found"
```



## Success

Returning status 200 and Customer hash

### Request

#### Endpoint

```plaintext
GET /api/v1/customers/110
Content-Type: application/json
Authorization: Bearer 0d1a6bfd67a8247dc1d4a061fad2da9b
```

`GET /api/v1/customers/:id`

#### Parameters


```json
{
}: 
```


| Name | Description |
|:-----|:------------|
| id *required* |  id |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "id": 110,
  "email": "jewell.feeney@tillman.io",
  "created_at": "2020-04-06T08:43:33.705Z",
  "updated_at": "2020-04-06T08:43:33.705Z",
  "profile": {
    "id": 108,
    "customer_id": 110,
    "organisation_id": 27,
    "title": "mr",
    "first_name": "Jeneva",
    "last_name": "Crist",
    "birth_date": "1967-12-11",
    "phone": "+3256980144",
    "city": "West Laurinda",
    "street": "Faustino Parkway",
    "building": "6781",
    "building_addon": "Suite 730",
    "postal_code": "55302",
    "language": "nl",
    "created_at": "2020-04-06T08:43:33.714Z",
    "updated_at": "2020-04-06T08:43:33.714Z"
  }
}
```



# Customers / Eans

All requests namespaced under /api/v1

## CREATE /eans -&gt; failure

when another customer already has EAN with same number

### Request

#### Endpoint

```plaintext
POST /api/v1/customers/2/eans
Content-Type: application/json
Authorization: Bearer d9f7b2f9dda0fccbfcb20dcd576e719b
```

`POST /api/v1/customers/:customer_id/eans`

#### Parameters


```json
{
  "ean": {
    "product": "electricity",
    "number": "542170967180397340",
    "reason": "normal",
    "supplier_id": 2,
    "street": "street name",
    "building": "15",
    "building_addon": "A",
    "postal_code": "2443",
    "city": "Kiev",
    "consumptions": [
      {
        "name": "mono",
        "volume": "22.25",
        "price": "0.15"
      }
    ],
    "fixed_fee": "1.00",
    "solar_panels": "true",
    "recording_period": "february",
    "contract_end_date": "2020-10-06",
    "respect_contract_end_date": true,
    "tariff_group": "mono",
    "gsc": "0.0214",
    "wkk": "0.00341",
    "inverter_max_power": "315"
  }
}
```


| Name | Description |
|:-----|:------------|
| ean *required* |  ean |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "error": "has_already_been_taken",
      "message": "has already been taken",
      "path": "ean.number",
      "type": "params"
    }
  ]
}
```



## CREATE /eans -&gt; failure

When a customer has already an EAN with the same number

### Request

#### Endpoint

```plaintext
POST /api/v1/customers/4/eans
Content-Type: application/json
Authorization: Bearer aba214cc23035e716072ab7a4c340085
```

`POST /api/v1/customers/:customer_id/eans`

#### Parameters


```json
{
  "ean": {
    "product": "electricity",
    "number": "542170967180397340",
    "reason": "normal",
    "supplier_id": 4,
    "street": "street name",
    "building": "15",
    "building_addon": "A",
    "postal_code": "2443",
    "city": "Kiev",
    "consumptions": [
      {
        "name": "mono",
        "volume": "22.25",
        "price": "0.15"
      }
    ],
    "fixed_fee": "1.00",
    "solar_panels": "true",
    "recording_period": "february",
    "contract_end_date": "2020-10-06",
    "respect_contract_end_date": true,
    "tariff_group": "mono",
    "gsc": "0.0214",
    "wkk": "0.00341",
    "inverter_max_power": "315"
  }
}
```


| Name | Description |
|:-----|:------------|
| ean *required* |  ean |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "error": "has_already_been_added_to_customer",
      "message": "has already been added to customer",
      "path": "ean.number",
      "type": "params"
    },
    {
      "error": "has_already_been_taken",
      "message": "has already been taken",
      "path": "ean.number",
      "type": "params"
    }
  ]
}
```



## CREATE /eans -&gt; failure

when another customer already has EAN with same number

### Request

#### Endpoint

```plaintext
POST /api/v1/customers/117/eans/bulk
Content-Type: application/json
Authorization: Bearer d80eb98d5133143a9bf1280131e2d35e
```

`POST /api/v1/customers/:customer_id/eans/bulk`

#### Parameters


```json
{
  "eans": [
    {
      "ean": {
        "product": "electricity",
        "number": "542170967180397340",
        "reason": "normal",
        "supplier_id": 8,
        "street": "street name",
        "building": "15",
        "building_addon": "A",
        "postal_code": "2443",
        "city": "Kiev",
        "consumptions": [
          {
            "name": "mono",
            "volume": "22.25",
            "price": "0.15"
          }
        ],
        "fixed_fee": "1.00",
        "solar_panels": "true",
        "recording_period": "february",
        "contract_end_date": "2020-10-06",
        "respect_contract_end_date": true,
        "tariff_group": "mono",
        "gsc": "0.0214",
        "wkk": "0.00341",
        "inverter_max_power": "315"
      }
    }
  ]
}
```


| Name | Description |
|:-----|:------------|
| eans *required* |  eans |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "error": "has_already_been_taken",
      "message": "has already been taken",
      "path": "ean.number",
      "type": "params",
      "index": 0
    }
  ]
}
```



## CREATE /eans -&gt; failure

When a customer has already an EAN with the same number

### Request

#### Endpoint

```plaintext
POST /api/v1/customers/119/eans/bulk
Content-Type: application/json
Authorization: Bearer 05a9498bd4a9833f8a00a78039304c84
```

`POST /api/v1/customers/:customer_id/eans/bulk`

#### Parameters


```json
{
  "eans": [
    {
      "ean": {
        "product": "electricity",
        "number": "542170967180397340",
        "reason": "normal",
        "supplier_id": 10,
        "street": "street name",
        "building": "15",
        "building_addon": "A",
        "postal_code": "2443",
        "city": "Kiev",
        "consumptions": [
          {
            "name": "mono",
            "volume": "22.25",
            "price": "0.15"
          }
        ],
        "fixed_fee": "1.00",
        "solar_panels": "true",
        "recording_period": "february",
        "contract_end_date": "2020-10-06",
        "respect_contract_end_date": true,
        "tariff_group": "mono",
        "gsc": "0.0214",
        "wkk": "0.00341",
        "inverter_max_power": "315"
      }
    }
  ]
}
```


| Name | Description |
|:-----|:------------|
| eans *required* |  eans |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "error": "has_already_been_added_to_customer",
      "message": "has already been added to customer",
      "path": "ean.number",
      "type": "params",
      "index": 0
    },
    {
      "error": "has_already_been_taken",
      "message": "has already been taken",
      "path": "ean.number",
      "type": "params",
      "index": 0
    }
  ]
}
```



## CREATE /eans -&gt; success

Create EAN batch

### Request

#### Endpoint

```plaintext
POST /api/v1/customers/1/eans
Content-Type: application/json
Authorization: Bearer 5a6628f340ed98796f38454f873c487a
```

`POST /api/v1/customers/:customer_id/eans`

#### Parameters


```json
{
  "ean": {
    "product": "electricity",
    "number": "542170967180397340",
    "reason": "normal",
    "supplier_id": 1,
    "street": "street name",
    "building": "15",
    "building_addon": "A",
    "postal_code": "2443",
    "city": "Kiev",
    "consumptions": [
      {
        "name": "mono",
        "volume": "22.25",
        "price": "0.15"
      }
    ],
    "fixed_fee": "1.00",
    "solar_panels": "true",
    "recording_period": "february",
    "contract_end_date": "2020-10-06",
    "respect_contract_end_date": true,
    "tariff_group": "mono",
    "gsc": "0.0214",
    "wkk": "0.00341",
    "inverter_max_power": "315"
  }
}
```


| Name | Description |
|:-----|:------------|
| ean *required* |  ean |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
201 Created
```


```json
{
  "id": 1,
  "customer_id": 1,
  "supplier_id": 1,
  "number": "542170967180397340",
  "product": "electricity",
  "building": "15",
  "building_addon": "A",
  "city": "Kiev",
  "consumptions": [
    {
      "name": "mono",
      "volume": "22.25",
      "price": "0.15"
    }
  ],
  "fixed_fee": "1.0",
  "postal_code": "2443",
  "reason": "normal",
  "state": "ready",
  "street": "street name",
  "tariff_group": "mono",
  "recording_period": "february",
  "respect_contract_end_date": true,
  "solar_panels": true,
  "inverter_max_power": 315,
  "wkk": "0.00341",
  "gsc": "0.0214",
  "created_at": "2020-04-06T08:43:31.928Z",
  "confirmed_at": "2020-04-06T08:43:31.918Z",
  "contract_end_date": "2020-10-06",
  "supplier": {
    "id": 1,
    "name": "Beer LLC 1"
  }
}
```



## CREATE /eans -&gt; success

Create EAN batch

### Request

#### Endpoint

```plaintext
POST /api/v1/customers/116/eans/bulk
Content-Type: application/json
Authorization: Bearer a9f8aa5b50593a50d2fc06cfdc4aa1c6
```

`POST /api/v1/customers/:customer_id/eans/bulk`

#### Parameters


```json
{
  "eans": [
    {
      "ean": {
        "product": "electricity",
        "number": "542170967180397340",
        "reason": "normal",
        "supplier_id": 7,
        "street": "street name",
        "building": "15",
        "building_addon": "A",
        "postal_code": "2443",
        "city": "Kiev",
        "consumptions": [
          {
            "name": "mono",
            "volume": "22.25",
            "price": "0.15"
          }
        ],
        "fixed_fee": "1.00",
        "solar_panels": "true",
        "recording_period": "february",
        "contract_end_date": "2020-10-06",
        "respect_contract_end_date": true,
        "tariff_group": "mono",
        "gsc": "0.0214",
        "wkk": "0.00341",
        "inverter_max_power": "315"
      }
    }
  ]
}
```


| Name | Description |
|:-----|:------------|
| eans *required* |  eans |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
201 Created
```


```json
[
  {
    "id": 7,
    "customer_id": 116,
    "supplier_id": 7,
    "number": "542170967180397340",
    "product": "electricity",
    "building": "15",
    "building_addon": "A",
    "city": "Kiev",
    "consumptions": [
      {
        "name": "mono",
        "volume": "22.25",
        "price": "0.15"
      }
    ],
    "fixed_fee": "1.0",
    "postal_code": "2443",
    "reason": "normal",
    "state": "ready",
    "street": "street name",
    "tariff_group": "mono",
    "recording_period": "february",
    "respect_contract_end_date": true,
    "solar_panels": true,
    "inverter_max_power": 315,
    "wkk": "0.00341",
    "gsc": "0.0214",
    "created_at": "2020-04-06T08:43:33.989Z",
    "confirmed_at": "2020-04-06T08:43:33.986Z",
    "contract_end_date": "2020-10-06",
    "supplier": {
      "id": 7,
      "name": "Ernser-Stark 7"
    }
  }
]
```



# Eans list

All requests namespaced under /api/v1

## Success

Returns status 200 and array of the customer's eans

### Request

#### Endpoint

```plaintext
GET /api/v1/customers/5/eans
Content-Type: application/json
Authorization: Bearer 9a9b82be7358a72368090497d7704081
```

`GET /api/v1/customers/:customer_id/eans`

#### Parameters


```json
{
}: 
```

None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
[
  {
    "id": 4,
    "customer_id": 5,
    "supplier_id": 6,
    "number": "545163640862149376",
    "product": "electricity",
    "building": "666",
    "building_addon": "Suite 966",
    "city": "South Nelleview",
    "fixed_fee": "31.0",
    "postal_code": "69057",
    "reason": "new",
    "state": "ready",
    "street": "Reichel Grove",
    "tariff_group": "dualExclusive",
    "recording_period": "automatic",
    "respect_contract_end_date": false,
    "solar_panels": false,
    "inverter_max_power": 689,
    "wkk": "0.00425",
    "gsc": "0.0215",
    "created_at": "2020-04-06T08:43:32.205Z",
    "confirmed_at": "2020-04-06T08:43:32.204Z",
    "supplier": {
      "id": 6,
      "name": "Kunze-Bayer 6"
    }
  },
  {
    "id": 5,
    "customer_id": 5,
    "supplier_id": 6,
    "number": "544001561091240792",
    "product": "electricity",
    "building": "78915",
    "building_addon": "Suite 516",
    "city": "Jacobiborough",
    "fixed_fee": "50.0",
    "postal_code": "84288-7210",
    "reason": "normal",
    "state": "ready",
    "street": "Paucek Mall",
    "tariff_group": "dualExclusive",
    "recording_period": "january",
    "respect_contract_end_date": false,
    "solar_panels": true,
    "inverter_max_power": 1431,
    "wkk": "0.00425",
    "gsc": "0.0215",
    "created_at": "2020-04-06T08:43:32.210Z",
    "confirmed_at": "2020-04-06T08:43:32.210Z",
    "supplier": {
      "id": 6,
      "name": "Kunze-Bayer 6"
    }
  }
]
```



# Me



## Failure

Returning status 401 when token wrong

### Request

#### Endpoint

```plaintext
GET /api/v1/me
Content-Type: application/json
Authorization: wrong_token
```

`GET /api/v1/me`

#### Parameters


```json
{
}: 
```

None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
401 Unauthorized
```


```json
{
  "status": "error",
  "errors": [
    {
      "error": "not_authenticated",
      "message": "not authenticated",
      "path": "request",
      "type": "custom"
    }
  ],
  "payload": {
  }
}
```



## Success

Returning status 200

### Request

#### Endpoint

```plaintext
GET /api/v1/me
Content-Type: application/json
Authorization: Bearer 3cab51c68bcddf6f2a18d9df159c38c1
```

`GET /api/v1/me`

#### Parameters


```json
{
}: 
```

None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "id": 7,
  "name": "Pouros Group",
  "domain": "quitzonrau-kiehn-7",
  "created_at": "2020-04-06T08:43:32.293Z"
}
```



# Ping



## Success

Returning status 200

### Request

#### Endpoint

```plaintext
GET /api/v1/ping
Content-Type: application/json
```

`GET /api/v1/ping`

#### Parameters


```json
{
}: 
```

None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
}
```



