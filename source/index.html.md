---
title: API Reference

language_tabs:
  - shell
  - ruby
  - python
  - javascript

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