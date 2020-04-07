---
title: Enbro Soho HTTP API
language_tabs:
  - json: JSON
  - shell: cURL
---

Enbro Soho HTTP API.

The enbro soho system can find new gas and electricity offers for a customer if it has all the necessary data.
Therefore the API allows you to create customers and provide all the necessary data for them,
including data of their EAN records.

According to customer records you can:

- Create new customers for your organisation through the API.
  The created customers are treated by the system the same way
  as the customers who registered using enbro soho registration forms.
- Get a list of the customers that have been created for the organisation.
- Get attributes of a customer by his ID.

When you have an ID of a customer, you can use it to create EAN records for him.

# Customers

    Allows to manage list of customers of the current organisation.
    Current organisation defined based on a provided API token.
    You can provide an API token using `Authorization` request header.

    For example: `Authorization: Bearer 2453797fc41e0cfa5c7a00f5acfd6915`


## CREATE 201 Created

Creates a customer for the current organisation and returns it's attributes

### Request

#### Endpoint

```plaintext
POST /api/v1/customers
Content-Type: application/json
Authorization: Bearer f4a0a5e6904602309cc51377d03f7f48
```

`POST /api/v1/customers`

#### Parameters


```json
{
  "customer": {
    "email": "misty_hansen@west.name",
    "terms_and_conditions": true,
    "privacy_policy": true,
    "registered_from_ip": "44.132.61.13",
    "profile": {
      "first_name": "Danny",
      "last_name": "Ocean",
      "title": "mr",
      "phone": "+3256980144",
      "birth_date": "2000-04-07",
      "city": "Huelborough",
      "street": "10109 Rodriguez Mountains",
      "building": "8962",
      "building_addon": "Suite 316",
      "postal_code": "84783",
      "language": "en"
    }
  }
}
```


| Name | Description |
|:-----|:------------|
| customer[email] *required* | A customer's email. Serves as an unique identifier of a customer. A customer with the same email must be not registered before. |
| customer[terms_and_conditions] *required* | Type: *boolean*. Flag that terms and conditions is accepted |
| customer[privacy_policy] *required* | Type: *boolean*. Flag that the privacy policy is accepted |
| customer[registered_from_ip] *required* | Customer registered from ip |
| customer[profile] *required* | Attributes for the profile of a customer |
| customer[profile][first_name] *required* | Customer profile first name |
| customer[profile][last_name] *required* | Customer profile last name |
| customer[profile][title] *required* | Values: ["mr", "mrs"]. Example: "mr". Customer profile title |
| customer[profile][phone] *required* | Example: "+3256980144". Customer profile phone |
| customer[profile][birth_date] *required* | Example: "2000-04-06". Customer profile birth date |
| customer[profile][city] *required* | Customer profile city |
| customer[profile][street] *required* | Customer profile street |
| customer[profile][building] *required* | Customer profile building |
| customer[profile][building_addon]  | Customer profile building addon |
| customer[profile][postal_code] *required* | Customer profile postal code |
| customer[profile][language]  | Values: ["nl", "fr", "en"]. Default: "nl". Customer profile language |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
201 Created
```


```json
{
  "id": 9,
  "email": "misty_hansen@west.name",
  "created_at": "2020-04-07T13:51:11.880Z",
  "updated_at": "2020-04-07T13:51:11.948Z",
  "organisation": {
    "id": 10,
    "name": "Cronin, Cremin and Gutmann",
    "domain": "uptonwitting-pagacrutherford-8",
    "created_at": "2020-04-07T13:51:11.806Z"
  },
  "profile": {
    "id": 8,
    "customer_id": 9,
    "title": "mr",
    "first_name": "Danny",
    "last_name": "Ocean",
    "birth_date": "2000-04-07",
    "phone": "+3256980144",
    "city": "Huelborough",
    "street": "10109 Rodriguez Mountains",
    "building": "8962",
    "building_addon": "Suite 316",
    "postal_code": "84783",
    "language": "en",
    "created_at": "2020-04-07T13:51:11.883Z",
    "updated_at": "2020-04-07T13:51:11.883Z"
  }
}
```



#### Fields

| Name       | Description         |
|:-----------|:--------------------|
| id | ID of the customer |
| email | Unique email of the customer |
| organisation | Attributes of the organisation to which the customer belongs to |
| organisation[id] | ID of the customer's organisation |
| organisation[name] | Name of the organisation |
| organisation[domain] | Domain of the organisation. Usually it's a subdomain under the parent organisation's domain |
| organisation[created_at] | Date and time when the organisation has been created |
| profile[id] | ID of the customer's profile |
| profile[customer_id] | ID of the customer to whom the profile belongs to |
| profile[title] | Values: ["mr", "mrs"]. Example: "mr". Customer profile title |
| profile[first_name] | The customer's first name |
| profile[last_name] | The customer's last name |
| profile[birth_date] | The customer's birth date |
| profile[phone] | Example: "+32460123456". The phone number (full format - only country code with digits) |
| profile[city] | The customer's address - city |
| profile[street] | The customer's address - street |
| profile[building] | The customer's address - building |
| profile[building_addon] | The customer's address - buildin addon |
| profile[postal_code] | The customer's address - zip code |
| profile[language] | Values: ["nl", "fr", "en"]. Customer profile language |
| profile[created_at] | Date and time when the customer profile has been created |
| profile[updated_at] | Date and time when the customer profile has been updated |


## CREATE 422 Validation Error

          At least one of the specified parameters contains an error.
          Check if all the required parameters have been specified.
          Also specified email must be unique.
          You can find details about the error in the response.


### Request

#### Endpoint

```plaintext
POST /api/v1/customers
Content-Type: application/json
Authorization: Bearer 4e9679ea36d4d88c264e7747e4e43aa5
```

`POST /api/v1/customers`

#### Parameters


```json
{
  "customer": {
    "email": "lynn_cartwright@boehm.org",
    "terms_and_conditions": true,
    "privacy_policy": true,
    "registered_from_ip": "231.177.1.50",
    "profile": {
      "first_name": null,
      "last_name": "Ocean",
      "title": "mr",
      "phone": "+3256980144",
      "birth_date": "2000-04-07",
      "city": "Port Wallymouth",
      "street": "666 Alla Squares",
      "building": "649",
      "building_addon": "Suite 994",
      "postal_code": "21339-6250",
      "language": "en"
    }
  }
}
```


| Name | Description |
|:-----|:------------|
| customer[email] *required* | A customer's email. Serves as an unique identifier of a customer. A customer with the same email must be not registered before. |
| customer[terms_and_conditions] *required* | Type: *boolean*. Flag that terms and conditions is accepted |
| customer[privacy_policy] *required* | Type: *boolean*. Flag that the privacy policy is accepted |
| customer[registered_from_ip] *required* | Customer registered from ip |
| customer[profile] *required* | Attributes for the profile of a customer |
| customer[profile][first_name] *required* | Customer profile first name |
| customer[profile][last_name] *required* | Customer profile last name |
| customer[profile][title] *required* | Values: ["mr", "mrs"]. Example: "mr". Customer profile title |
| customer[profile][phone] *required* | Example: "+3256980144". Customer profile phone |
| customer[profile][birth_date] *required* | Example: "2000-04-06". Customer profile birth date |
| customer[profile][city] *required* | Customer profile city |
| customer[profile][street] *required* | Customer profile street |
| customer[profile][building] *required* | Customer profile building |
| customer[profile][building_addon]  | Customer profile building addon |
| customer[profile][postal_code] *required* | Customer profile postal code |
| customer[profile][language]  | Values: ["nl", "fr", "en"]. Default: "nl". Customer profile language |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "path": "customer.profile.first_name",
      "error": "must_be_filled",
      "message": "must be filled",
      "type": "params"
    }
  ]
}
```



#### Fields

| Name       | Description         |
|:-----------|:--------------------|
| errors | Type: *array*. Items type: *object*. Contains a list of occurred errors |
| path | A full name of an erroneous field |
| error | A string identifier of the error |
| message | An error message |
| type | A type of the error |


## LIST 200 OK

Returns customers of the current organisation.
Current organisation defined based on provided API token.


### Request

#### Endpoint

```plaintext
GET /api/v1/customers?page=1&amp;per=2
Content-Type: application/json
Authorization: Bearer adb343a0860c10f32ce2581884c8618a
```

`GET /api/v1/customers`

#### Parameters


```json
page: 1
per: 2
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
  "limit_value": 2,
  "next_page": 2,
  "prev_page": null,
  "total_pages": 2,
  "records": [
    {
      "id": 27,
      "email": "bennie@gleason.com",
      "created_at": "2020-04-07T13:51:13.124Z",
      "updated_at": "2020-04-07T13:51:13.124Z",
      "organisation": {
        "id": 28,
        "name": "West-Turner",
        "domain": "daughertyledner-schowalterschmeler-20",
        "created_at": "2020-04-07T13:51:13.042Z"
      },
      "profile": {
        "id": 26,
        "customer_id": 27,
        "title": "mr",
        "first_name": "Latanya",
        "last_name": "Kilback",
        "birth_date": "1967-03-15",
        "phone": "+3256980144",
        "city": "Scottchester",
        "street": "Pacocha Trafficway",
        "building": "249",
        "building_addon": "Apt. 466",
        "postal_code": "49586",
        "language": "nl",
        "created_at": "2020-04-07T13:51:13.132Z",
        "updated_at": "2020-04-07T13:51:13.132Z"
      }
    },
    {
      "id": 23,
      "email": "bertram@schuppe.com",
      "created_at": "2020-04-07T13:51:13.049Z",
      "updated_at": "2020-04-07T13:51:13.049Z",
      "organisation": {
        "id": 28,
        "name": "West-Turner",
        "domain": "daughertyledner-schowalterschmeler-20",
        "created_at": "2020-04-07T13:51:13.042Z"
      },
      "profile": {
        "id": 22,
        "customer_id": 23,
        "title": "mr",
        "first_name": "Cole",
        "last_name": "Franecki",
        "birth_date": "1978-10-06",
        "phone": "+3225551212",
        "city": "Lupeland",
        "street": "Breitenberg Prairie",
        "building": "1407",
        "building_addon": "Suite 103",
        "postal_code": "76169",
        "language": "fr",
        "created_at": "2020-04-07T13:51:13.056Z",
        "updated_at": "2020-04-07T13:51:13.056Z"
      }
    }
  ]
}
```



#### Fields

| Name       | Description         |
|:-----------|:--------------------|
| current_page | The current page number |
| limit_value | Limit of records on a page |
| next_page | The next page number |
| prev_page | The previous page number |
| total_pages | Total available pages |
| records | The list of found records |
| id | ID of the customer |
| email | Unique email of the customer |
| organisation | Attributes of the organisation to which the customer belongs to |
| organisation[id] | ID of the customer's organisation |
| organisation[name] | Name of the organisation |
| organisation[domain] | Domain of the organisation. Usually it's a subdomain under the parent organisation's domain |
| organisation[created_at] | Date and time when the organisation has been created |
| profile[id] | ID of the customer's profile |
| profile[customer_id] | ID of the customer to whom the profile belongs to |
| profile[title] | Values: ["mr", "mrs"]. Example: "mr". Customer profile title |
| profile[first_name] | The customer's first name |
| profile[last_name] | The customer's last name |
| profile[birth_date] | The customer's birth date |
| profile[phone] | Example: "+32460123456". The phone number (full format - only country code with digits) |
| profile[city] | The customer's address - city |
| profile[street] | The customer's address - street |
| profile[building] | The customer's address - building |
| profile[building_addon] | The customer's address - buildin addon |
| profile[postal_code] | The customer's address - zip code |
| profile[language] | Values: ["nl", "fr", "en"]. Customer profile language |
| profile[created_at] | Date and time when the customer profile has been created |
| profile[updated_at] | Date and time when the customer profile has been updated |


## SHOW 200 OK

          Returns the attributes of the customer with provided ID.
          The customer must belong to the current organisation.


### Request

#### Endpoint

```plaintext
GET /api/v1/customers/12
Content-Type: application/json
Authorization: Bearer e5f910186aab561b6a6bf5db76d9e775
```

`GET /api/v1/customers/:id`

#### Parameters



| Name | Description |
|:-----|:------------|
| id *required* | Type: *integer*. ID of a customer |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "id": 12,
  "email": "pok@watsica.com",
  "created_at": "2020-04-07T13:51:12.371Z",
  "updated_at": "2020-04-07T13:51:12.371Z",
  "organisation": {
    "id": 16,
    "name": "Crona and Sons",
    "domain": "millsbeer-padberg-12",
    "created_at": "2020-04-07T13:51:12.364Z"
  },
  "profile": {
    "id": 11,
    "customer_id": 12,
    "title": "mr",
    "first_name": "Taylor",
    "last_name": "Jerde",
    "birth_date": "1992-03-18",
    "phone": "+32460123456",
    "city": "Lesleymouth",
    "street": "Feil Walks",
    "building": "5768",
    "building_addon": "Suite 409",
    "postal_code": "01014",
    "language": "fr",
    "created_at": "2020-04-07T13:51:12.383Z",
    "updated_at": "2020-04-07T13:51:12.383Z"
  }
}
```



#### Fields

| Name       | Description         |
|:-----------|:--------------------|
| id | ID of the customer |
| email | Unique email of the customer |
| organisation | Attributes of the organisation to which the customer belongs to |
| organisation[id] | ID of the customer's organisation |
| organisation[name] | Name of the organisation |
| organisation[domain] | Domain of the organisation. Usually it's a subdomain under the parent organisation's domain |
| organisation[created_at] | Date and time when the organisation has been created |
| profile[id] | ID of the customer's profile |
| profile[customer_id] | ID of the customer to whom the profile belongs to |
| profile[title] | Values: ["mr", "mrs"]. Example: "mr". Customer profile title |
| profile[first_name] | The customer's first name |
| profile[last_name] | The customer's last name |
| profile[birth_date] | The customer's birth date |
| profile[phone] | Example: "+32460123456". The phone number (full format - only country code with digits) |
| profile[city] | The customer's address - city |
| profile[street] | The customer's address - street |
| profile[building] | The customer's address - building |
| profile[building_addon] | The customer's address - buildin addon |
| profile[postal_code] | The customer's address - zip code |
| profile[language] | Values: ["nl", "fr", "en"]. Customer profile language |
| profile[created_at] | Date and time when the customer profile has been created |
| profile[updated_at] | Date and time when the customer profile has been updated |


## SHOW 404 Not Found

          A customer with specified ID haven't been found.
          The customer must belong to the current organisation.
          Current organisation defined based on provided API token.


### Request

#### Endpoint

```plaintext
GET /api/v1/customers/18
Content-Type: application/json
Authorization: Bearer dbc28b264edc367051d2a1a6ed8538ba
```

`GET /api/v1/customers/:id`

#### Parameters



| Name | Description |
|:-----|:------------|
| id *required* | Type: *integer*. ID of a customer |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
404 Not Found
```


```json
"Not found"
```



# Customers / Eans

All requests namespaced under /api/v1

## CREATE /eans -&gt; failure

When a customer has already an EAN with the same number

### Request

#### Endpoint

```plaintext
POST /api/v1/customers/2/eans/bulk
Content-Type: application/json
Authorization: Bearer 1c0d5ecdf9669ff21a38aca7c2534900
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
        "contract_end_date": "2020-10-07",
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



## CREATE /eans -&gt; failure

when another customer already has EAN with same number

### Request

#### Endpoint

```plaintext
POST /api/v1/customers/3/eans/bulk
Content-Type: application/json
Authorization: Bearer e46beb077056b4700e6c362b5db49d96
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
        "contract_end_date": "2020-10-07",
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

when another customer already has EAN with same number

### Request

#### Endpoint

```plaintext
POST /api/v1/customers/35/eans
Content-Type: application/json
Authorization: Bearer be494c40dca7cc198e6e0add1e64441a
```

`POST /api/v1/customers/:customer_id/eans`

#### Parameters


```json
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
    "contract_end_date": "2020-10-07",
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
| customer_id *required* | ID of the customer |
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
POST /api/v1/customers/38/eans
Content-Type: application/json
Authorization: Bearer 0a68a845425d710a8611ae2203c32a73
```

`POST /api/v1/customers/:customer_id/eans`

#### Parameters


```json
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
    "contract_end_date": "2020-10-07",
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
| customer_id *required* | ID of the customer |
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
Authorization: Bearer cb3f3c4acb80173a4211e1aed3afe12b
```

`GET /api/v1/me`

#### Parameters


None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "id": 1,
  "name": "Runolfsdottir-Cassin",
  "domain": "leuschke-okonfadel-1",
  "created_at": "2020-04-07T13:51:10.654Z"
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



