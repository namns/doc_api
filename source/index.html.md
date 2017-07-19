---
title: API doc

language_tabs:
  - php

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>


search: true
---

# Introduction

Welcome to the Kdata API! You can use our API to access Whmcs API endpoints, which can get information on various order, invoice, and billing… in our database.

We have language bindings in Curl! You can view code examples in the dark area to the right.

# Login

> To authorize, use this code:


```php
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/login');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'email'         => 'namns1102@gmail.com',
            'password'      => '123456789'
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
```

> The above command returns JSON structured like this:

```json
{
    "0": {
        "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTMxNzIyOCwiZXhwIjoxNDk5NDAzNjI4LCJuYmYiOjE0OTkzMTcyMjgsImp0aSI6Im53TWdya2lxdDFmQW83MWIifQ.iKI7jwPnGNUB6OhL31qTyXfR2fvhrVDWSBDb5kRAcxU"
    },
    "result": "success",
    "user": [
        {
            "id": 7,
            "uuid": "5c38ad73-73a7-453e-972f-07ac589012c2",
            "firstname": "nam",
            "lastname": "ns",
            "companyname": "appota",
            "email": "namns@appota.com",
            "address1": "quoc oai ha noi",
            "address2": "quoc oai ha noi",
            "city": "ha noi",
            "state": "viet nam",
            "postcode": "3006",
            "country": "VN",
            "phonenumber": "0978973995",
            "authmodule": "",
            "authdata": "",
            "currency": 1,
            "defaultgateway": "",
            "credit": "0.00",
            "taxexempt": 0,
            "latefeeoveride": 0,
            "overideduenotices": 0,
            "separateinvoices": 0,
            "disableautocc": 0,
            "datecreated": "2017-06-27",
            "notes": "",
            "billingcid": 0,
            "securityqid": 0,
            "securityqans": "JvF0PUGA9E/p4AtXrGfjVP1Hia4=",
            "groupid": 0,
            "cardtype": "",
            "cardlastfour": "",
            "cardnum": "",
            "startdate": "",
            "expdate": "",
            "issuenumber": "",
            "bankname": "",
            "banktype": "",
            "bankcode": "",
            "bankacct": "",
            "gatewayid": "",
            "lastlogin": "2017-06-28 09:15:10",
            "ip": "118.70.184.34",
            "host": "118.70.184.34",
            "status": "Active",
            "language": "",
            "pwresetkey": "",
            "emailoptout": 0,
            "overrideautoclose": 0,
            "allow_sso": 1,
            "email_verified": 0,
            "created_at": "-0001-11-30 00:00:00",
            "updated_at": "2017-06-28 09:15:10",
            "pwresetexpiry": "0000-00-00 00:00:00"
        }
    ]
}
```
Login to the system to make another api.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/login`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
email | string | Your email | yes
password | string | Your password | yes

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
user | array | infomation user
token | string | Your token

### Error Responses

Error | Result
-------------- | -----------------
Invalid email or password | { “result”: “error”, “messages”: “User not exists”}
The password field is required. | {"result": "error", “password”: ["The password field is required."]}
The password field is required. | {"result": "error", “email”: ["The email field is required."]}

# Order

## Add order



```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/addorder');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'product'       => 'VPS 01',
            'billingcycle'  => 'monthly',
            'os'            => 'centos 6.x',
            'extraIp'       => '3'
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
  "result": "success",
  "orderid": 170,
  "productids": "171",
  "addonids": "",
  "domainids": "",
  "invoiceid": 171
}
```

Adds an order to a client.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/addorder`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
product | string | VPS package name | yes
billingcycle | string | Billing cycles of the products | yes
os | string | Billing cycles of the products | yes
cpu | string |  | no
hdd | string |  | no
ram | string |  | no
extraIp | interger | Only get the value from 1 to 5 | no
hostname | string | The hostname of server for VPS order | no
rootpw | string |  | no
ns1prefix | string | The first nameserver prefix for the VPS. Eg. ns1 in ns1.hostname.com | no
ns2prefix | string | The second nameserver prefix for the VPS. Eg. ns2 in ns2.hostname.com | no


### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
orderid | int | The Order ID for the created order
productids | string | The Product/Service ID created by the order
addonids | string | The Addon ID created by the order
domainids | string | The domain ID created by the order
invoiceid | int | The invoice ID created for the order


### Error Responses

Error | Result
-------------- | -----------------
Given Client product is not found in the database.| {“result”:“error”,“messages”:“Product not exists”}
Unable to add order when client status is Closed | {“result”:“error”,“message”:“Unable to add order when client status is Closed”}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}

## Get product



```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/getproduct');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'serviceid'     => '171'
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```



> The above command returns JSON structured like this:

```json
{
  "result": "success",
  "serviceid": "171",
  "product": {
    "serviceid": "171",
    "regdate": "2017-01-06",
    "nextduedate": "2017-01-06",
    "status": "Pending",
    "domain": "",
    "dedicatedip": "",
    "assignedips": "",
    "billingcycle": "Monthly",
    "username": "",
    "password": "",
    "os": "Centos 6.x 64Bit",
    "cpu": "2 Core",
    "ram": "1GB",
    "hdd": "40G",
    "Extra ip": "3"
  }
}
```

Obtain a list of Client Purchased Products matching the provided criteria

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/getproduct`

### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
serviceid | int | The specific service id to obtain the details for | yes

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
serviceid | int | The specific service id searched for
product | array | The product returned matching the criteria passed


### Error Responses

Error | Result
-------------- | -----------------
Service id of another account| {“result”:“error”,“messages”:“Permission denied!”}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


# Billing

## ApplyCredit



```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/applycredit');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'invoiceid'     => '171'
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
  "result": "success",
  "invoiceid": "171",
  "amount": 450000,
  "invoicepaid": "true"
}
```

Applies the Client’s Credit to an invoice.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/applycredit`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
invoiceid | int | The ID of the invoice to apply credit | yes

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
invoiceid | int | The id of the invoice the credit has been applied to
amount | float | The amount of credit applied
invoicepaid | string | true/false string


### Error Responses

Error | Result
-------------- | -----------------
Credit amount exceeds customer credit balance| {“result”: “error”,“message”: “Amount exceeds customer credit balance”}
Invoice Not in Unpaid Status | {“result”:“error”,“message”:“Invoice Not in Unpaid Status”}
Invoice id of another accoun | {“result”:“error”,“messages”:“Permission denied!”}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


# Invoice

## Get invoice


```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/getinvoice');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'invoiceid'     => '171'
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```

> The above command returns JSON structured like this:

```json
{
  "result": "success",
  "invoiceid": "171",
  "invoicenum": "",
  "userid": "3",
  "date": "2017-01-06",
  "duedate": "2017-01-06",
  "datepaid": "0000-00-00 00:00:00",
  "subtotal": "450000.00",
  "credit": "0.00",
  "tax": "0.00",
  "tax2": "0.00",
  "total": "450000.00",
  "balance": "450000.00",
  "taxrate": "0.00",
  "taxrate2": "0.00",
  "status": "Unpaid",
  "paymentmethod": "banktransfer",
  "notes": "",
  "ccgateway": false,
  "items": {
    "item": [
      {
        "id": "172",
        "type": "Hosting",
        "relid": "171",
        "description": "VPS 01 (06/01/2017 - 05/02/2017)\nDATA CENTER: VIỆT NAM\nServer OS: Centos 6.x 64Bit\nCPU: 2 Core\nRAM: 1GB\nHDD: 40G\nExtra IP: 3 x IP VND50,000VND",
        "amount": "450000.00",
        "taxed": "0"
      }
    ]
  },
  "transactions": ""
}
```

Adds an order to a client.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/getinvoice`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
invoiceid | int | The ID of the invoice to retrieve | yes


### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
invoiceid | int | The id of the invoice
invoicenum | string | The Sequential invoice number assigned (if enabled)
userid | int | The id of the user owning this invoice
date | \Carbon\Carbon | The date of the invoice YYYY-MM-DD
duedate | \Carbon\Carbon | The due date of the invoice YYYY-MM-DD
datepaid | \Carbon\Carbon | The date the invoice was paid YYYY-MM-DD HH:ii:ss
subtotal | float | The subtotal on the invoice
credit | float | The amount of credit assigned to the invoice
tax | float | The amount of first level tax charged on the invoice
tax2 | float | The amount of second level tax charged on the invoice
total | float | The total of the invoice
balance | float | The amount left to pay on the invoice
taxrate | float | The rate of the first level tax
taxrate2 | float | The rate of the second level tax
status | float | The status of the invoice
paymentmethod | float | The payment method on the invoice in system format
notes | float | The notes associated with the invoice
ccgateway | float | Is the payment method associated with the invoice a CC Gateway
items | string | The items on the invoice
transactions | string | The transactions on the invoice


### Error Responses

Error | Result
-------------- | -----------------
Invoice id of another account	| {“result”:“error”,“messages”:“Permission denied!”}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}

## Get invoice product


```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/getinvoiceproduct');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'serviceid'     => '171'
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
  "result": "true",
  "data": [
    {
      "id": 171,
      "userid": "3",
      "invoicenum": "",
      "date": "2017-01-06",
      "duedate": "2017-01-06",
      "datepaid": "2017-01-09 15:39:30",
      "subtotal": "450000.00",
      "credit": "450000.00",
      "tax": "0.00",
      "tax2": "0.00",
      "total": "0.00",
      "taxrate": "0.00",
      "taxrate2": "0.00",
      "status": "Paid",
      "paymentmethod": "banktransfer",
      "notes": ""
    }
  ]
}
```

Obtain a list of Client Purchased Products matching the provided criteria

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/getinvoiceproduct`

### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
serviceid | int | The specific service id to obtain the details for | yes
status | string | Find invoices for a specific status | no


### Error Responses

Error | Result
-------------- | -----------------
Product not exists or Permission denied!| {“result”:“error”,“messages”:“Product not exists or Permission denied!”}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


# Support

## Add cancel request

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/cancelrequest');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'serviceid'     => '171',
            'reason'        => 'Customer Request'
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
  "result": "success",
  "serviceid": "171",
  "userid": "3"
}
```

Applies the Client’s Credit to an invoice.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/cancelrequest`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
serviceid | int | The Service ID to cancel | yes
reason | string | 	The customer reason for cancellation | yes

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
serviceid | int | The id of the service the request was for
userid | float | The id of the user the service belongs to


### Error Responses

Error | Result
-------------- | -----------------
Service id of another account | {“result”:“error”,“messages”:“Permission denied!”}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


# AcceptQuote

## AcceptQuote

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/acceptQuote');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'quoteid' => '1',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
    "result": "success"
}
```

Applies the Client’s Credit to an invoice.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/acceptQuote`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
quoteid | int | The quote id to be accepted and converted to an invoice | yes

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
invoiceid | int | The newly created invoice id


### Error Responses

Error | Result
-------------- | -----------------
Quote ID Not Found | {"result": "error","message": "Quote ID Not Found"}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


# ADD

## AddAnnouncement

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/addAnnouncement');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'date' => '2016-01-01 15:30:00',
            'title' => 'Sample announcement',
            'announcement' => 'Text goes here...',
            'published' => '1',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
    "result": "success",
    "announcementid": "1"
}
```

Adds an announcement.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/addAnnouncement`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
date | \datetime | Date in the format YYYY-MM-DD HH:MM:SS | yes
title | string |  | yes
announcement | string | Announcement text | yes
published | bool | Pass as true to publish | no

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
announcementid | int | The id of the new announcement

### Error Responses

Error | Result
-------------- | -----------------
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


## AddBannedIp

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/addBannedIp');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'ip' => '1.2.3.4',
            'reason' => 'Abuse',
            'days' => '30',
            'expires' => '2017-08-01 15:30:00'
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
     "result": "success",
     "banid": "1"
}
```

Adds an IP to the ban list.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/addBannedIp`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
ip | string |  | yes
reason | string | Admin only reason | yes
days | int | 	If passed, expires date is auto calculated | yes
expires | datetime | YYYY-MM-DD HH:MM:SS | no

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
banid | int | The id of the new ban entry


### Error Responses

Error | Result
-------------- | -----------------
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


## AddBillableItem

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/addBillableItem');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
             'clientid' => '1',
            'description' => 'This is a billable item',
            'amount' => '10.00',
            'invoiceaction' => 'recur',
            'recur' => '1',
            'recurcycle' => 'Months',
            'recurfor' => '12',
            'duedate' => '2016-01-01',
            'hours' => '2',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
     "result": "success",
    "billableid": "1"
}
```

Adds a Billable Item

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/addBillableItem`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
clientid | int |  The client to add the item to| yes
description | string | The description of the Billable Item. This will appear on the invoice | yes
amount | float | the total amount to invoice for | yes
invoiceaction | string | One of ‘noinvoice’, ‘nextcron’, ‘nextinvoice’, ‘duedate’, ‘recur’ | no
recur | int | When $invoiceaction=recur. The frequency of the recurrence | no
recurcycle | string | How often to recur the Billable Item. Days, Weeks, Months or Years. | no
recurfor | int | How many times the Billable Item should create an invoice. | no
duedate | \Carbon\Carbon | Date the invoice should be due (only required for duedate & recur invoice actions). YYYY-mm-dd | no
hours | float | number of hours/quantity the item corresponds to. (not required for single quantities) | no

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
billableid | int | The id of the newly created billable item


### Error Responses

Error | Result
-------------- | -----------------
Client ID not Found | {"result": "error","message": "Client ID not Found"}
You must provide a description | {"result": "error","message": "You must provide a description"}
Invalid Invoice Action | {"result": "error","message": "Invalid Invoice Action"}
Recurring must have a unit, cycle and limit | {"result": "error","message": "Recurring must have a unit, cycle and limit"}
Due date is required | {"result": "error","message": "Due date is required"}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


## AddClient

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/AddClient');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
              'firstname' => 'John',
            'lastname' => 'Doe',
            'email' => 'john.doe@example.com',
            'address1' => '123 Main Street',
            'city' => 'Anytown',
            'state' => 'ST',
            'postcode' => '12345',
            'country' => 'US',
            'phonenumber' => '800-555-1234',
            'password2' => 'password',
            'cardtype' => 'Visa',
            'cardnum' => '4111111111111111',
            'expdate' => '0721',
            'clientip' => '1.2.3.4',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
     "result": "success",
    "clientid": "1"
}
```

Adds a client.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/AddClient`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
firstname | string |  | yes
lastname | string |  | yes
companyname | string |  | yes
email | string |  | yes
address1 | string |  | yes
address2 | string |  | no
city | string |  | yes
state | string |  | yes
postcode | string |  | yes
country | string | 2 character ISO country code | yes
phonenumber | string |  | yes
password2 | int |  | yes
securityqid | string | Security Question ID from tbladminsecurityquestions | no
securityqans | string | Security Question Answer | no
cardtype | string | Credit card type. Provide full name: Visa, Mastercard, American Express, etc… | no
cardnum | string | Credit card number | no
expdate | string | Format: MMYY | no
startdate | string | Format: MMYY (if applicable) | no
issuenumber | string | Credit card issue number (if applicable) | no
cvv | string | Credit card CVV number (will not be stored) | no
currency | int | Currency ID from tblcurrencies | no
groupid | int | Client Group ID from tblclientgroups | no
customfields | string | Base64 encoded serialized array of custom field values | no
language | string | Default language setting. Provide full name: ‘english’, ‘french’, etc… | no
clientip | string | IP address of the user | no
notes | string | Admin only notes | no
noemail | bool | Pass as true to skip sending welcome email | no
skipvalidation | bool | Pass as true to ignore required fields validation | no


### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
clientid | int | The id of the newly created client


### Error Responses

Error | Result
-------------- | -----------------
You did not enter your first name | {"result": "error","message": "You did not enter your first name"}
You did not enter your last name | {"result": "error","message": "You did not enter your last name"}
You did not enter your email address | {"result": "error","message": "You did not enter your email address"}
The email address you entered was not valid | {"result": "error","message": "The email address you entered was not valid"}
You did not enter your email address | {"result": "error","message": "You did not enter your email address"}
You did not enter your address line 1 | {"result": "error","message": "You did not enter your address line 1"}
You did not enter your city | {"result": "error","message": "You did not enter your city"}
You did not enter your state | {"result": "error","message": "You did not enter your state"}
You did not enter your postcode | {"result": "error","message": "You did not enter your postcode"}
You did not enter your country | {"result": "error","message": "You did not enter your country"}
You did not enter your phone number | {"result": "error","message": "You did not enter your phone number"}
Invalid telephone phone number | {"result": "error","message": "Invalid telephone phone number"}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}

## AddClientNote

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/AddClientNote');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'userid' => '1',
            'notes' => 'Note to add',
            'sticky' => true,
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
     "result": "success",
    "noteid": "1"
}
```

Adds a Client Note

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/AddClientNote`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
userid | int |  The Client ID to apply the note to| yes
notes | string | The note to add | yes
sticky | bool | Should the note be made sticky. Makes the note ‘sticky’ and displays the note throughout the client’s account and on any tickets they submit in the admin area | no


### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
noteid | int | 	The id of the newly created note


### Error Responses

Error | Result
-------------- | -----------------
Client ID not found | {"result": "error","message": "Client ID not found"}
Notes can not be empty | {"result": "error","Notes can not be empty"}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}

## AddContact

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/AddContact');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
             'clientid' => '7',
            'firstname' => 'Nam',
            'lastname' => 'ns',
            'email' => 'namns@appota.com',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
     "result": "success",
    "contactid": "1"
}
```

Adds a contact to a client account.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/AddContact`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
clientid | int |  | yes
firstname | string |  | no
lastname | string |  | no
companyname | string |  | no
email | string | Email address to identify the contact. This should be unique if the contact will be a sub-account | no
address1 | string |  | no
address2 | string |  | no
city | string |  | no
state | string |  | no
postcode | string |  | no
country | string | 2 character ISO country code | no
phonenumber | string |  | no
password2 | int | if creating a sub-account | no
generalemails | bool | set true to receive general email types | no
productemails | bool | set true to receive product related emails | no
domainemails | bool | set true to receive domain related emails | no
invoiceemails | bool | set true to receive billing related emails | no
supportemails | bool | set true to receive support ticket related emails | no
permissions | bool | A comma separated list of sub-account permissions. eg manageproducts,managedomains | no


### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
contactid | int | The id of the newly added contact.


### Error Responses

Error | Result
-------------- | -----------------
Client ID Not Found | {"result": "error","message": "Client ID Not Found"}
Duplicate Email Address| {"result": "error","message": "Duplicate Email Address"}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


## AddCredit

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/AddCredit');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
             'clientid' => '1',
            'description' => 'Adding funds via api',
            'amount' => '12.34',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
     "result": "success",
    "newbalance": "123.45"
}
```

Adds credit to a given client.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/AddCredit`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
clientid | int |  | yes
description | string | 	Admin only notes for credit justification | yes
amount | float |  | yes


### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
newbalance | float | The new total credit balance


### Error Responses

Error | Result
-------------- | -----------------
Client ID not found | {"result": "error","message": "Client ID not found"}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


## AddInvoicePayment

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/AddInvoicePayment');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
             'invoiceid' => '1',
            'transid' => 'D28DJIDJW393JDWQKQI332',
            'gateway' => 'mailin',
            'date' => '2016-01-01 12:33:12',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
     "result": "success"
}
```

Adds payment to a given invoice.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/AddInvoicePayment`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
invoiceid | int |  | yes
transid | string | The unique transaction id that should be applied to the payment | yes
gateway | string | the gateway used in system name format, eg. paypal, authorize | yes
date | \Carbon\Carbon | The date that the payment should have assigned. Format: YYYY-MM-DD HH:mm:ss | no
amount | float | the amount paid, can be left undefined to take full amount of invoice | no
fees | float | the amount of the payment that was taken as a fee by the gateway | no
noemail | bool | set to true to not send an email for the invoice payment | no

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
newbalance | float | The new total credit balance


### Error Responses

Error | Result
-------------- | -----------------
Client ID not found | {"result": "error","message": "Client ID not found"}
It is not possible to add a payment to an invoice that is Cancelled | {"result": "error","message": "It is not possible to add a payment to an invoice that is Cancelled"}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


## AddProduct

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/AddProduct');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
             'type' => 'other',
            'gid' => '1',
            'name' => 'Sample Product',
            'welcomeemail' => '5',
            'paytype' => 'recurring',
            'pricing[1][monthly]' => '5.00',
            'pricing[1][annually]' => '50.00',
            'pricing[2][monthly]' => '8.00',
            'pricing[2][annually]' => '80.00',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
    "result": "success",
    "pid": 68
}
```

Adds a product to the system to be available for purchase.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/AddProduct`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
name | string | The name of the product to be added | yes
gid | int | The id of the product group to add the product | yes
type | string | One of ‘hostingaccount’, ‘reselleraccount’, ‘server’ or ‘other’ | no
stockcontrol | bool | Set to true to enable stock control on the product | no
qty | int | How much of this product is in stock | no
paytype | string | The payment type of the product. One of ‘free’, ‘onetime’, ‘recurring’ | no
hidden | bool | Should the product be hidden from the client order form | no
showdomainoptions | bool | Should the product show the domain registration options. | no
tax | bool | Does tax apply to the product. | no
isFeatured | bool | Should the product be featured in the Product Group. | no
proratabilling | bool | Is pro-rata billing enabled for this product. | no
description | string | The description of the product to show on the product listing in the cart | no
welcomeemail | int | The id of the Email Template to use as the welcome email. Product/Service Messages only | no
proratadate | int | See http://docs.whmcs.com/Products_and_Services#Pricing_Tab | no
proratachargenextmonth | int | See http://docs.whmcs.com/Products_and_Services#Pricing_Tab | no
subdomain | string | A comma separated list of subdomains to offer on the domain register page. eg: .domain1.com,.domain2.com | no
autosetup | string | When should the product be automatically setup. One of “ (never), ‘on’ (pending order), ‘payment’ (on payment), ‘order’ (on order) | no
module | string | The server module system name to associate with the product. eg: cpanel, autorelease, plesk | no
servergroupid | int | The server group id used on product creation to associate an appropriate server | no
configoption1 | mixed | The first module configuration value | no
configoption2 | mixed | The second module configuration value | no
configoption3 | mixed | The third module configuration value | no
configoption4 | mixed | The fourth module configuration value | no
configoption5 | mixed | The fifth module configuration value | no
configoption6 | mixed | The sixth module configuration value | no
order | int | The order to in which to display on the order form | no
pricing | array | The pricing array to associate with the product. format $pricing[currencyid]cycle | no

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
pid | int | The id of the newly created product


### Error Responses

Error | Result
-------------- | -----------------
You must supply a name for the product | {"result": "error","message": "You must supply a name for the product"}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


## AddTicketNote

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/AddTicketNote');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
             'ticketid' => '1',
            'message' => 'This is a sample ticket note',
            'markdown' => true,
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
    "result": "success",
}
```

Add a note to a ticket by Ticket ID or Ticket Number.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/AddTicketNote`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
message | string | The content of the ticket note | yes
ticketnum | string | The Client Ticket Number ID to apply the note to | no
ticketid | int | The id of the ticket in the database. Either $ticketnum or $ticketid is required | no
markdown | bool | Should markdown be used on the ticket note output | no

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error

### Error Responses

Error | Result
-------------- | -----------------
Ticket ID not found | {"result": "error","message": "Ticket ID not found"}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


## AddTicketReply

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/AddTicketReply');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
             'ticketid' => '1',
            'message' => 'This is a sample ticket reply',
            'clientid' => '1',
            'customfields' => '("1" => "Google")',
            'useMarkdown' => 'true'
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
    "result": "success"
}
```

Add a reply to a ticket by Ticket ID.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/AddTicketReply`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
ticketid | int | The id of the ticket in the database. Either $ticketnum or $ticketid is required | yes
message | string | The content of the ticket reply | no
useMarkdown | bool | Should markdown be used on the ticket reply output | no
userid | int | Pass a userid to associate the ticket reply with a specific client | no
contactid | string | Pass a contactid to associate the ticket reply with a specific contact belonging to $userid | no
adminusername | string | The admin username to associate the ticket reply with | no
name | string | The name to associate with the ticket reply if not an admin or client response | no
email | string | The email to associate with the ticket reply if not an admin or client response | no
status | string | The status to set on the ticket after the reply is made if the default status on admin/client response is not required. See GetSupportStatuses API command | no
noemail	 | bool | Set to true to stop the ticket reply email being sent | no
customfields | string | A base64 encoded array of the custom fields to update | no

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error

### Error Responses

Error | Result
-------------- | -----------------
Ticket ID not found | {"result": "error","message": "Ticket ID not found"}
Client ID Not Found | {"result": "error","message": "Client ID Not Found"}
Contact ID Not Found | {"result": "error","message": "Contact ID Not Found"}
Name and email address are required if not a client | {"result": "error","message": "Name and email address are required if not a client"}
Message is required | {"result": "error","message": "Message is required"}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


## AddTransaction

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/AddTransaction');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
             'paymentmethod' => 'paypal',
            'userid' => '1',
            'transid' => 'FJWEK32DWO329JFW',
            'date' => '01/01/2016',
            'description' => 'A sample API payment',
            'amountin' => '10.00',
            'fees' => '0.89',
            'rate' => '1.00000',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
    "result": "success"
}
```

Add a transaction to the system.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/AddTransaction`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
paymentmethod | string | The payment method of the transaction in system format | yes
userid | int | The ID of the user to apply the transaction to | no
invoiceid | int | The ID of the invoice the transaction is for | no
transid | string | The unique transaction id for this payment | no
date | string | The date of the transaction in your Localisation Format (eg DD/MM/YYYY) | no
currencyid | int | The currency id for the transaction if not associated with a user | no
description | string | 	The description of the transaction | no
amountin | float | The amount received by the payment | no
fees | float | The amount of fee charged on the transaction by the merchant - This can be negative | no
amountout | float | The amount paid out by the payment | no
rate | float | The exchange rate for the payment based on the default currency | no
credit | bool | Should the payment be applied to credit on the client account. Invoice ID must not be provided. | no

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error

### Error Responses

Error | Result
-------------- | -----------------
Invoice ID Not Found | {"result": "error","message": "Invoice ID Not Found"}
Client ID Not Found | {"result": "error","message": "Client ID Not Found"}
Payment Method is required | {"result": "error","message": "Payment Method is required"}
Transaction ID must be Unique | {"result": "error","message": "Transaction ID must be Unique"}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}

#CancelOrder

##CancelOrder

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/CancelOrder');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
             'orderid' => '1',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
    "result": "success",
}
```

Cancel a Pending Order

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/CancelOrder`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
orderid | int | The ID of the pending order | yes
cancelsub | bool | Attempt to cancel the subscription associated with the products | no
noemail | bool | Set to true to stop the invoice payment email being sent if the invoice becomes paid | no

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error

### Error Responses

Error | Result
-------------- | -----------------
Order ID not found or Status not Pending | {"result": "error","message": "Order ID not found or Status not Pending "}
Subscription Cancellation Failed - Please check the gateway log for further information | {"result": "error","message": "Subscription Cancellation Failed - Please check the gateway log for further information "}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


#AffiliateActivate

## AffiliateActivate

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/AffiliateActivate');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'userid' => '1',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
    "result": "success"
}
```

Activate affiliate referrals for a client.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/AffiliateActivate`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
userid | int | The client ID to activate affiliate status for | yes

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error

### Error Responses

Error | Result
-------------- | -----------------
Client ID Not Found | {"result": "error","message": "Client ID Not Found"}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


#AcceptOrder

## AcceptOrder

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/AcceptOrder');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
           'orderid' => '1',
            'registrar' => 'enom',
            'autosetup' => true,
            'sendemail' => true,
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
    "result": "success",
}
```

Accepts a pending order

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/AcceptOrder`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
orderid | int | The order id to be accepted | yes
serverid | int | The specific server to assign to products within the order | no
serviceusername | string | The specific username to assign to products within the order | no
servicepassword | string | The specific password to assign to products within the order | no
registrar | string | The specific registrar to assign to domains within the order | no
sendregistrar | bool | Send the request to the registrar to register the domain. | no
autosetup | bool | Send the request to the product module to activate the service. This can override the product configuration. | no
sendemail | bool | Send any automatic emails. This can be Product Welcome, Domain Renewal, Domain Transfer etc. | no


### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error

### Error Responses

Error | Result
-------------- | -----------------
Order ID not found or Status not Pending | {"result": "error","message": "Order ID not found or Status not Pending"}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


#CapturePayment

## CapturePayment

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/CapturePayment');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
             'invoiceid' => '1',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
    "result": "success"
}
```

Attempt to capture a payment on an unpaid CC Invoice

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/CapturePayment`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
invoiceid | int | The ID of the pending order | yes
cvv |  | string The CVV Number for the card being attempted | no


### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error

### Error Responses

Error | Result
-------------- | -----------------
Invoice Not Found or Not Unpaid | {"result": "error","message": "Invoice Not Found or Not Unpaid"}
Payment Attempt Failed | {"result": "error","message": "Payment Attempt Failed"}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}



#CreateInvoice

## CreateInvoice

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/CreateInvoice');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
             'userid' => '1',
	    'status' => 'Unpaid',
	    'sendinvoice' => '1',
	    'paymentmethod' => 'mailin',
	    'taxrate' => '10.00',
	    'date' => '2016-01-01',
	    'duedate' => '2016-01-08',
	    'itemdescription1' => 'Sample Invoice Item',
	    'itemamount1' => '15.95',
	    'itemtaxed1' => '0',
	    'itemdescription2' => 'Sample Second Invoice Item',
	    'itemamount2' => '1.00',
	    'itemtaxed2' => '1',
	    'autoappliedcredit' => '0',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
    "result": "success",
    "invoiceid": "1",
    "status": "Unpaid"
}
```

Create an invoice using the provided parameters.


### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/CreateInvoice`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
userid | int | 	The ID of the client to close | yes
status | string | The status of the invoice being created (Defaults to Unpaid) | no
draft | bool | Should the invoice be created in draft status (No need to pass $status also) | no
sendinvoice | bool | Should the Invoice Created Email be sent to the client (cannot be used with $draft) | no
paymentmethod | string | The payment method of the created invoice in system format | no
taxrate | float | The first level tax rate to apply to the invoice to override the system default | no
taxrate2 | float| The second level tax rate to apply to the invoice to override the system default | no
date | \Carbon\Carbon | The date that the invoice should show as created YYYY-mm-dd | no
duedate | \Carbon\Carbon | The due date of the newly created invoice YYYY-mm-dd | no
notes | string | The notes to appear on the created invoice | no
itemdescriptionx | string | The line items description X is an integer to add multiple invoice items | no
itemamountx | float | The line items amount | no
itemtaxedx | bool | The line items is taxed value | no
autoapplycredit | bool | Should credit on the client account be automatically applied to the invoice | no


### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
invoiceid | int | The ID of the newly created invoice
status | string | The status of the newly created invoice.

### Error Responses

Error | Result
-------------- | -----------------
Client ID Not Found | {"result": "error","message": "Client ID Not Found"}
Cannot create and send a draft invoice in a single API request. Please create and send separately. | {"result": "error","message": "Cannot create and send a draft invoice in a single API request. Please create and send separately."}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


#CreateProject

## CreateProject

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/CreateProject');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
             'title' => 'This is a Test Project',
    		'adminid' => '2',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
    "result": "success",
    "message": "Project has been created"
}
```

Creates a new project


### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/CreateProject`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
title | string | The title of the new project | yes
adminid | int | The adminId the project will be associated with| yes
userid | int | The user that the project is for | no
status | string | The status of the project as defined in Project Management Settings | no
created | \Carbon\Carbon | The created date of the project in Y-m-d format | no
duedate | \Carbon\Carbon | The duedate date of the project in Y-m-d format | no
completed | bool| Is the project completed | no
ticketids | string| A comma separated list of ticket IDs to associate with the project | no
invoiceids | string| A comma separated list of invoice IDs to associate with the project | no

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
message | string | ‘Project has been created’


### Error Responses

Error | Result
-------------- | -----------------
Client ID Not Found | {"result": "error","message": "Client ID Not Found"}
Admin ID not Set. | {"result": "error","message": "Admin ID not Set."}
Admin ID Not Found | {"result": "error","message": "Admin ID Not Found"}
Project Management is not active. | {"result": "error","message": "Project Management is not active."}
Project Title is Required. | {"result": "error","message": "Project Title is Required."}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}

#CreateQuote

## CreateQuote

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/CreateQuote');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'subject' => 'Test Quote Subject',
	    'stage' => 'Draft',
	    'userid' => '1',
	    'validuntil' => '01/01/2016',
	    'lineitems' => base64_encode(serialize(array(array("desc"=>"Test Description 1","qty"=>1,"up"=>"10.00","discount"=>"10.00","taxable"=>true),array("desc"=>"Test Description 2","qty"=>4,"up"=>"15.00","discount"=>"0.00","taxable"=>false))));,
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
    "result": "success",
    "quoteid": "1"
}
```

Creates a new quote


### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/CreateQuote`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
subject | string | The subject of the new quote | yes
stage | string | The current stage of the quote (‘Draft’,‘Delivered’,‘On Hold’,‘Accepted’,‘Lost’,‘Dead’)| yes
validuntil | string | The date the quote is valid until in localised format (eg DD/MM/YYYY) | yes
datecreated | string | The date the quote was created in localised format (eg DD/MM/YYYY) | no
lineitems | aray | A base64 encoded serialized array containing the following keys: | no
lineitems[x][desc] | string | For $lineitems. The description of the line item | no
lineitems[x][qty] | int| For $lineitems. The quantity of the line item being quoted for | no
lineitems[x][up] | float| For $lineitems. The Unit Price of the line item | no
lineitems[x][discount] | float| For $lineitems. The amount of discount to provide on the line items | no
lineitems[x][taxable] | bool| 	For $lineitems. Is the line item taxable | no
userid | int| If the quote is for an exising client, the client ID the quote is for | no
firstname | string| The first name of the client the quote is for if no $userid | no
lastname | string| The last name of the client the quote is for if no $userid | no
companyname | string| The company of the client the quote is for if no $userid | no
email | string| The email address of the client the quote is for if no $userid | no
address1 | string| The address1 of the client the quote is for if no $userid | no
address2 | string| The address2 of the client the quote is for if no $userid | no
city | string| The city of the client the quote is for if no $userid | no
state | string| The state of the client the quote is for if no $userid | no
country | string| The country of the client the quote is for if no $userid | no
phonenumber | string| The phone number of the client (no country code) the quote is for if no $userid. Local format eg 4035551234 | no
currency | int| The id of the currency for the quote is for if no $userid | no
proposal | string| The proposal text displayed to the end user | no
customernotes | string| The notes on the quote displayed to the end user | no
adminnotes | string|The notes on the quote displayed to the staff only | no


### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
quoteid | int | The id of the newly created quote


### Error Responses

Error | Result
-------------- | -----------------
Subject is required | {"result": "error","message": "Subject is required"}
Invalid Stage. | {"result": "error","message": "Invalid Stage."}
Valid Until is required | {"result": "error","message": "Valid Until is required"}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


#DeactivateModule

## DeactivateModule

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/DeactivateModule');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
             'moduleType' => 'gateway',
            'moduleName' => 'paypal',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
     "result": "success"
}
```

Deactivates a given module.


### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/DeactivateModule`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
moduleType | string | 	The module type to be deactivated | yes
moduleName | string | The module name to be deactivated| yes

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error


### Error Responses

Error | Result
-------------- | -----------------
Invalid module type provided. Supported module types include: xxx | {"result": "error","message": "Invalid module type provided. Supported module types include: xxx"}
Invalid module name provided. | {"result": "error","message": "Invalid module name provided."}
Module deactivation not supported by module type. | {"result": "error","message": "Module deactivation not supported by module type."}
Failed to deactivate: xxx | {"result": "error","message": "Failed to deactivate: xxx"}
An unexpected error occurred: xxx | {"result": "error","message": "An unexpected error occurred: xxx"}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


#DecryptPassword

## DecryptPassword

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/DecryptPassword');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
              'password2' => '12345678',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
    "result": "success",
    "password": "teststring"
}
```

Decrypt an encrypted string.


### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/DecryptPassword`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
password2 | string | The string to decrypt | yes

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error


### Error Responses

Error | Result
-------------- | -----------------
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


#Delete

## DeleteContact

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/DeleteContact');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
             'contactid' => '1',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
    "result": "success",
    "contactid": "1"
}
```

Deletes a contact.

Removes contact record. This action cannot be undone.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/DeleteContact`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
contactid | int | The contact id to be deleted | yes

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
contactid | int | The contact id that was deleted


### Error Responses

Error | Result
-------------- | -----------------
Contact ID Not Found | {"result": "error","message": "Contact ID Not Found"}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


## DeleteOrder

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/DeleteOrder');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
              'orderid' => '1',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
   "result": "success"
}
```

Deletes a cancelled or fraud order.

Removes an order from the system. This cannot be undone. This will remove all items associated with the order (services, addons, domains, invoices etc)

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/DeleteOrder`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
orderid | int | The order to be deleted | yes

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error


### Error Responses

Error | Result
-------------- | -----------------
Order ID not found | {"result": "error","message": "Order ID not found"}
The order status must be in Cancelled or Fraud to be deleted | {"result": "error","message": "The order status must be in Cancelled or Fraud to be deleted"}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


## DeleteTicket

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/DeleteTicket');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
             'ticketid' => '1',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
    "result": "success"
}
```

Deletes a ticket.

Removes a ticket and all replies from the system. This cannot be undone.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/DeleteTicket`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
ticketid | int | The ticket to be deleted | yes

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error


### Error Responses

Error | Result
-------------- | -----------------
Ticket ID not found | {"result": "error","message": "Ticket ID not found"}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


## DeleteTicketNote

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/DeleteTicketNote');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
             'noteid' => '1',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
    "result": "success"
}
```

Deletes a ticket note.

Removes a ticket note from the system. This cannot be undone.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/DeleteTicketNote`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
noteid | int | The ticket note to be deleted | yes

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error


### Error Responses

Error | Result
-------------- | -----------------
Note ID Not Found | {"result": "error","message": "Note ID Not Found"}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}

# Domain

## DomainGetLockingStatus

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/DomainGetLockingStatus');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'domainid' => '1',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
    "result": "success",
    "lockstatus": "locked"
}
```

Obtains the current lock status of the domain.

Connects to the registrar and obtains the current lock status of the domain

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/DomainGetLockingStatus`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
domainid | int | The id of the domain to obtain the lock status for | yes

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
lockstatus | string | The current status of the lock.

### Error Responses

Error | Result
-------------- | -----------------
Domain ID Not Found | {"result": "error","message": "Domain ID Not Found"}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


## DomainGetNameservers

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/DomainGetNameservers');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'domainid' => '1',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
   "result": "success",
    "ns1": "ns1.example.com",
    "ns2": "ns1.example.com"
}
```

Obtains the current nameservers for the domain.

Connects to the registrar and obtains the nameservers for the domain

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/DomainGetNameservers`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
domainid | int | The id of the domain to obtain the nameservers for | yes

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
ns1 | string | The first nameserver on the domain.
ns2 | string | The second nameserver on the domain.
ns3 | string | The third nameserver on the domain.
ns4 | string | The fourth nameserver on the domain
ns5 | string | The fifth nameserver on the domain

### Error Responses

Error | Result
-------------- | -----------------
Domain ID Not Found | {"result": "error","message": "Domain ID Not Found"}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


## DomainRegister

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/DomainRegister');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'domainid' => '1',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
   "result": "success"
}
```

Sends the Register command to the registrar for the domain

Connects to the registrar and attempts to register the domain.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/DomainRegister`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
domainid | int | The id of the domain to obtain the whois information for recommended | no
domain | string | The domain name to be registered. This or $domainid is required | no


### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error


### Error Responses

Error | Result
-------------- | -----------------
Domain Not Found | {"result": "error","message": "Domain ID Not Found"}
Registrar Error Message | {"result": "error","message": "Registrar Error Message"}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


## DomainRelease

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/DomainRelease');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'domainid' => '1',
    	    'newtag' => 'ENOM',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
   "result": "success"
}
```

Sends the Release command to the registrar for the domain to a new tag

Connects to the registrar and attempts to release the domain.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/DomainRelease`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
domainid | int | The id of the domain to obtain the whois information for recommended | no
domain | string | The domain name to be registered. This or $domainid is required | no
newtag | string | The receiving tag for the domain | yes

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error


### Error Responses

Error | Result
-------------- | -----------------
Domain Not Found | {"result": "error","message": "Domain Not Found"}
Registrar Error Message | {"result": "error","message": "Registrar Error Message"}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


## DomainToggleIdProtect

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/DomainToggleIdProtect');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
             'domainid' => '1',
    	   'idprotect' => true,
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
   "result": "success"
}
```

Sends the Toggle ID Protect command to the registrar for the domain

Connects to the registrar and attempts to toggle the ID Protect state


### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/DomainToggleIdProtect`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
domainid | int | The id of the domain to obtain the whois information for | yes
idprotect | bool | Should ID Protection be turned on | no

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error


### Error Responses

Error | Result
-------------- | -----------------
Domain ID Not Found | {"result": "error","message": "Domain ID Not Found"}
Registrar Error Message | {"result": "error","message": "Registrar Error Message"}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


## DomainWhois

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/DomainWhois');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
           'domain' => 'example.com',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
   "result": "success",
    "status": "unavailable",
    "whois": "xxx"
}
```

Retrieve domain whois information.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/DomainWhois`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
domain | string | The domain name to lookup | yes

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
status | string | The registration status: available or unavailable
whois | string | Whois server response

### Error Responses

Error | Result
-------------- | -----------------
Domain not valid | {"result": "error","message": "Domain not valid"}
The given TLD is not supported for WHOIS lookups | {"result": "error","message": "The given TLD is not supported for WHOIS lookups"}
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}

#Get

##GetActivityLog

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/GetActivityLog');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
           'description' => 'Cron Job',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
   "result": "success",
    "totalresults": "2",
    "startnumber": "0",
    "activity[entry][0][id]": "2",
    "activity[entry][0][userid]": "0",
    "activity[entry][0][date]": "2016-01-01 17:24:26",
    "activity[entry][0][description]": "Cron Job: Check for Updates: No new updates available",
    "activity[entry][0][username]": "admin",
    "activity[entry][0][ipaddress]": "192.168.99.1",
    "activity[entry][1][id]": "1",
    "activity[entry][1][userid]": "0",
    "activity[entry][2][date]": "2016-01-01 17:24:20",
    "activity[entry][1][description]": "Cron Job: Perform WHMCS Update Check",
    "activity[entry][1][username]": "admin",
    "activity[entry][1][ipaddress]": "192.168.99.1"
}
```

Obtain the Activity Log that matches passed criteria

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/GetActivityLog`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
limitstart | int | The offset for the returned log data (default: 0) | no
limitnum | int | The number of records to return (default: 25) | no
userid | int | The ID of the user to obtain the log for | no
date | string | The date of the activity log to retrieve in localised format (eg 01/01/2016) | no
user | string | The name of the user to retrieve the log entries for | no
description | string | Search the log for a specific string | no
ipaddress | string | The IP Address to search the activity log for | no

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
totalresults | int | The total number of results available
startnumber | int | The starting number for the returned results
activity | array | The activity log entries returned

### Error Responses

Error | Result
-------------- | -----------------
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


##GetAffiliates

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/GetAffiliates');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
   "result": "success",
    "totalresults": "2",
    "startnumber": "0",
    "numreturned": "2",
    "affiliates[affiliate][0][id]": "1",
    "affiliates[affiliate][0][date]": "2016-01-01",
    "affiliates[affiliate][0][clientid]": "1",
    "affiliates[affiliate][0][visitors]": "145",
    "affiliates[affiliate][0][paytype]": "percentage",
    "affiliates[affiliate][0][payamount]": "15.00",
    "affiliates[affiliate][0][onetime]": "1",
    "affiliates[affiliate][0][balance]": "15.00",
    "affiliates[affiliate][0][withdrawn]": "0.00",
    "affiliates[affiliate][0][created_at]": "0000-00-00 00:00:00",
    "affiliates[affiliate][0][updated_at]": "0000-00-00 00:00:00",
    "affiliates[affiliate][1][id]": "1",
    "affiliates[affiliate][1][date]": "2016-01-08",
    "affiliates[affiliate][1][clientid]": "4",
    "affiliates[affiliate][1][visitors]": "0",
    "affiliates[affiliate][1][paytype]": "",
    "affiliates[affiliate][1][payamount]": "0.00",
    "affiliates[affiliate][1][onetime]": "1",
    "affiliates[affiliate][1][balance]": "0.00",
    "affiliates[affiliate][1][withdrawn]": "0.00",
    "affiliates[affiliate][1][created_at]": "0000-00-00 00:00:00",
    "affiliates[affiliate][1][updated_at]": "0000-00-00 00:00:00"
}
```

Obtain an array of affiliates

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/GetAffiliates`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
limitstart | int | The offset for the returned log data (default: 0) | no
limitnum | int | The number of records to return (default: 25) | no
userid | int | Obtain affiliate data for a specific client account | no
visitors | int | Provide affiliates that match a specific visitor count | no
paytype | string | Provide affiliates matching the paytype provided. One of “, ‘percentage’, ‘fixedamount’ | no
payamount | float | Provide affiliates matching a specific overridden payout amount | no
onetime | int | Provide affiliates configured to receive one time affiliates | no
balance | float | Provide affiliates that have this balance | no
withdrawn | float | Provide affiliates that have withdrawn this amount | no

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
totalresults | int | The total number of results available
startnumber | int | The starting number for the returned results
numreturned | int | The number of results returned
affiliates | array | The affiliates entries returned

### Error Responses

Error | Result
-------------- | -----------------
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


##GetAnnouncements

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/GetAnnouncements');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
  "result": "success",
    "totalresults": "1",
    "startnumber": "0",
    "numreturned": "1",
    "announcements[announcement][0][id]": "1",
    "announcements[announcement][0][date]": "2016-02-24 21:27:04",
    "announcements[announcement][0][title]": "Thank you for choosing WHMCS!",
    "announcements[announcement][0][announcement]": "<p>Welcome to <a title=\"WHMCS\" href=\"http:\/\/whmcs.com\" target=\"_blank\">WHMCS<\/a>! You have made a great choice and we want to help you get up and running as quickly as possible.<\/p><p>This is a sample announcement. Announcements are a great way to keep your customers informed about news and special offers. You can edit or delete this announcement by logging into the admin area and navigating to <em>Support &gt; Announcements<\/em>.<\/p><p>If at any point you get stuck, our support team is available 24x7 to assist you. Simply visit <a title=\"www.whmcs.com\/support\" href=\"http:\/\/www.whmcs.com\/support\" target=\"_blank\">www.whmcs.com\/support<\/a> to request assistance.<\/p>",
    "announcements[announcement][0][published]": "1",
    "announcements[announcement][0][parentid]": "0",
    "announcements[announcement][0][language]": "",
    "announcements[announcement][0][created_at]": "0000-00-00 00:00:00",
    "announcements[announcement][0][updated_at]": "0000-00-00 00:00:00"
}
```

Obtain an array of announcements

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/GetAnnouncements`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
limitstart | int | The offset for the returned log data (default: 0) | no
limitnum | int | The number of records to return (default: 25) | no

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
totalresults | int | The total number of results available
startnumber | int | The starting number for the returned results
numreturned | int | The number of results returned
announcements | array | The announcement entries returned

### Error Responses

Error | Result
-------------- | -----------------
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


##GetAutomationLog

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/GetAutomationLog');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
 	    'startdate' => '2016-11-01',
	    'enddate' => '2016-11-07',
	    'namespace' => 'createinvoices',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
  "result": "success",
    "currentDatetime": "2016-11-09 15:37:58",
    "lastDailyCronInvocationTime": "2016-11-09 11:00:00",
    "startdate": "2016-11-01 00:00:00",
    "enddate": "2016-11-07 23:59:59",
    "statistics": "...."
}
```

Get Automation Task Log.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/GetAutomationLog`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
startdate | string | Defaults to today | no
enddate | string | Defaults to today | no
namespace | string | Optional filter for a specific namespace | no

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
currentDatetime | string | The current system datetime.
lastDailyCronInvocationTime | string | The last daily cron invokation time.
startdate | string| The start date/time filter applied
enddate | string | The end date/time filter applied
statistics | array | The log output, grouped by date and namespace

### Error Responses

Error | Result
-------------- | -----------------
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


##GetCancelledPackages

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/GetCancelledPackages');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
 	   
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
  "result": "success",
    "totalresults": "2",
    "startnumber": "0",
    "numreturned": "2",
    "packages[package][0][id]": "1",
    "packages[package][0][date]": "2016-02-24 21:27:04",
    "packages[package][0][relid]": "1",
    "packages[package][0][reason]": "Client Requested",
    "packages[package][0][type]": "End of Billing Period",
    "packages[package][0][created_at]": "0000-00-00 00:00:00",
    "packages[package][0][updated_at]": "0000-00-00 00:00:00",
    "packages[package][1][id]": "2",
    "packages[package][1][date]": "2016-02-24 21:27:04",
    "packages[package][1][relid]": "2",
    "packages[package][1][reason]": "Client Requested",
    "packages[package][1][type]": "Immediate",
    "packages[package][1][created_at]": "0000-00-00 00:00:00",
    "packages[package][1][updated_at]": "0000-00-00 00:00:00"
}
```

Obtain an array of cancellation requests.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/GetCancelledPackages`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
limitstart | string | The offset for the returned cancellation request data (default: 0) | no
limitnum | string | The number of records to return (default: 25) | no

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
totalresults | int | The total number of results available
startnumber | int | The total number of results available
numreturned | int| The number of results returned
packages | array | The cancellation request entries returned


### Error Responses

Error | Result
-------------- | -----------------
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}

##GetCurrencies

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/GetCurrencies');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
 	   
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
  "result": "success",
    "totalresults": "1",
    "currencies[currency][0][id]": "1",
    "currencies[currency][0][code]": "USD",
    "currencies[currency][0][prefix]": "$",
    "currencies[currency][0][suffix]": " USD",
    "currencies[currency][0][format]": "1",
    "currencies[currency][0][rate]": "1.00000"
}
```

Obtain the Currencies configured in the System.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/GetCurrencies`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
totalresults | int | The total number of results available
currencies | array | The currency entries returned


### Error Responses

Error | Result
-------------- | -----------------
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


##GetEmailTemplates

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/GetEmailTemplates');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
 	    'type' => 'general',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
   "result": "success",
    "totalresults": "2",
    "emailtemplates[emailtemplate][0][id]": "38",
    "emailtemplates[emailtemplate][0][name]": "Automated Password Reset",
    "emailtemplates[emailtemplate][0][subject]": "Your new password for {$company_name}",
    "emailtemplates[emailtemplate][0][custom]": "0",
    "emailtemplates[emailtemplate][1][id]": "64",
    "emailtemplates[emailtemplate][1][name]": "Client Email Address Verification",
    "emailtemplates[emailtemplate][1][subject]": "Confirm Your Registration",
    "emailtemplates[emailtemplate][1][custom]": "0"
}
```

Obtain a list of email templates from the system.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/GetEmailTemplates`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
type | string | The type of email template to retrieve | no
language | string | The language of the email template to retrieve | no

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
totalresults | int | The total number of results available
emailtemplates | array | 	The email templates entries returned


### Error Responses

Error | Result
-------------- | -----------------
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


##GetOrderStatuses

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/GetOrderStatuses');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
 	    
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
   "result": "success",
    "totalresults": 4,
    "statuses": {
        "status": [
            {
                "title": "Pending",
                "count": "239"
            },
            {
                "title": "Active",
                "count": "29"
            },
            {
                "title": "Fraud",
                "count": 0
            },
            {
                "title": "Cancelled",
                "count": "3"
            }
        ]
    }
}
```

Obtain a list of email templates from the system.

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/GetOrderStatuses`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----


### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
totalresults | int | The total number of results available
statuses | array | An array of order statuses


### Error Responses

Error | Result
-------------- | -----------------
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


##GetPaymentMethods

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/GetPaymentMethods');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
 	    
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
   "result": "success",
    "totalresults": 1,
    "paymentmethods": {
        "paymentmethod": [
            {
                "module": "banktransfer",
                "displayname": "Bank Transfer"
            }
        ]
    }
}
```

Retrieve Activated Payment Methods

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/GetPaymentMethods`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----


### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
totalresults | int | The total number of results available
paymentmethods | array | An array of available payment methods


### Error Responses

Error | Result
-------------- | -----------------
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}


##GetPromotions

```php
<?php 
$authorization = array('Authorization: Bearer ' . 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9sb2dpbiIsImlhdCI6MTQ5OTIyNjM5NSwiZXhwIjoxNDk5MzEyNzk1LCJuYmYiOjE0OTkyMjYzOTUsImp0aSI6ImRqQjhnbGhCaVBhdG5WOU0ifQ.EMXB-xHdHGIzwbDWrIuQHff-NEe3qIZJ4lzxssjiPw8');
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://api.dichvuchothuechodat.top/api/v1/GetPromotions');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $authorization);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
 	    
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
?>
```


> The above command returns JSON structured like this:

```json
{
   "result": "success",
    "totalresults": 1,
    "paymentmethods": {
        "paymentmethod": [
            {
                "id": 1,
                "code": "sample",
                "type": "Percentage",
                "recurring": 1,
                "value": 10,
                "cycles": "",
                "appliesto": "1,2",
                "requires": "1,2",
                "requiresexisting": 0,
                "startdate": "0000-00-00",
                "expirationdate": "0000-00-00",
                "maxuses": 0,
                "uses": 1,
                "lifetimepromo": 0,
                "applyonce": 0,
                "newsignups": 0,
                "existingclient": 0,
                "onceperclient": 0,
                "recurfor": 0,
                "upgrades": 0,
                "upgradeconfig": "a:4:{s:5:\"value\";s:4:\"0.00\";s:4:\"type\";s:0:\"\";s:12:\"discounttype\";s:10:\"Percentage\";s:13:\"configoptions\";s:0:\"\";}",
                "notes": ""
            }
        ]
    }
}
```

Obtain promotions matching the passed criteria

### HTTP Request

`POST http://api.dichvuchothuechodat.top/api/v1/GetPromotions`
### Request Parameters

Parameter | Type | Description | Required
-------------- | ------- | ----------------- | -----
code|string|Retrieve a specific promotion code. Do not pass to retrieve all|no

### Response Parameters

Parameter | Type | Description
-------------- | ------- | -----------------
result | string | The result of the operation: success or error
totalresults | int | The total number of results available
promotions | array | An array of promotional codes matching the criteria passed


### Error Responses

Error | Result
-------------- | -----------------
token expired | { “error”: “token expired”}
token invalid | { “error”: “token invalid”}
