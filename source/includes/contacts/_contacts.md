# Contacts

The contacts API allows you to create, view, update, and delete individual, or a batch of contacts.

Parameter | Type   | Description | Mandatory
--------- |--------| ----------- | ----------- 
bwfan_public_api_key | string | Api key for authorization | YES

## Get All Contacts

This endpoint retrieves all contacts.

```php
<?php
$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/contact';
$params = [
    'bwfan_public_api_key' => 'your_api_key',
];

$query_string = http_build_query( $params );
$endpoint = $site_url . $endpoint . '?' . $query_string;

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => $endpoint,
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'GET',
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;
?>
```

### HTTP Request

`GET http://example.com/wp-json/autonami/contact`

Parameter | Type | Description                                                                                           | Mandatory
--------- |------|-------------------------------------------------------------------------------------------------------| -----------
page | integer | Current page of the collection                                                                        | NO
email | string | Email of the user to get details of                                                                   | NO
sort_order | string | Order of contacts.</br>Default is DESC<code></br> ASC, DESC</code>                                    | NO
sort_field | string | Field to sort by.</br>Default is creation_date<code></br>f_name, l_name,</br>email, creation_date, </br>last_modified</code> | NO
status | string | Contact status. <code></br>unverified, subscribed,</br>bounced, unsubscribed</code>                   | NO
from | date | Filter subscribers added on or</br>after this date (format yyyy-mm-dd).                               | NO
to | date | Filter subscribers added on or</br>before this date (format yyyy-mm-dd).                              | NO
updated_from | date | Filter subscribers who have been</br>updated after this date (format yyyy-mm-dd).                     | NO
updated_to | date | Filter subscribers who have been</br>updated before this date (format yyyy-mm-dd).                    | NO
tag | array | array of tag ids <code>[id1,id2,...]</code>                                                           | NO
list | array | array of list id <code>[id1,id2,...]</code>                                                           | NO

> JSON response example:

```json
{
  "code": 200,
  "message": "Contact(s) listed successfully",
  "result": {
    "contacts": [
      {
        "id": "3",
        "wpid": "0",
        "uid": "f83fe893d5728fa07c595609d45cf426",
        "email": "abc@wisetr.com",
        "f_name": "abc",
        "l_name": "",
        "contact_no": "1234567890",
        "country": "",
        "state": "",
        "timezone": "America/Chicago",
        "type": "lead",
        "source": "",
        "points": "0",
        "tags": "[\"2\"]",
        "lists": "[]",
        "last_modified": "2022-04-12 18:45:54",
        "creation_date": "2022-04-06 19:02:36",
        "status": "1"
      },
      {
        "id": "2",
        "wpid": "2",
        "uid": "9b8673862d199bb9114574205746668e",
        "email": "test@test.com",
        "f_name": "",
        "l_name": "",
        "contact_no": "",
        "country": "",
        "state": "",
        "timezone": "",
        "type": "",
        "source": "",
        "points": "0",
        "tags": "[]",
        "lists": "[]",
        "last_modified": "2021-12-22 11:56:37",
        "creation_date": "2021-12-22 11:56:37",
        "status": "0"
      },
      {},
      {}
    ],
    "total": ""
  },
  "limit": 30,
  "offset": 0
}
```

## Get Contact by ID

This endpoint retrieves contact detail of specified contact id

```php
<?php
$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/contact/{contact_id}';
$params = [
    'bwfan_public_api_key' => 'your_api_key',
];

$query_string = http_build_query( $params );
$endpoint = $site_url . $endpoint . '?' . $query_string;

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => $endpoint,
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'GET',
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;

?>
```

### HTTP Request

`GET http://example.com/wp-json/autonami/contact/{contact_id}`

Parameter | Type | Description | Mandatory
--------- |------|-------------| -----------

> JSON response example:

```json
{
  "code": 200,
  "message": "Contact data successfully listed",
  "result": {
    "id": "1",
    "wpid": "1",
    "uid": "cd81e6dbc125ab85b92a41fabbc0c5c5",
    "email": "abc@wisetr.com",
    "f_name": "t",
    "l_name": "test",
    "contact_no": "+911234567890",
    "country": "IN",
    "state": "Uttar Pradesh",
    "timezone": "Asia/Kolkata",
    "type": "customer",
    "source": "wc_order",
    "points": "0",
    "tags": "[]",
    "lists": "[]",
    "last_modified": "2022-04-06 17:39:11",
    "creation_date": "2021-09-21 06:32:21",
    "status": "0"
  },
  "limit": 30,
  "offset": 0
}
```

## Add Contact

This endpoint add a contact

```php
<?php

$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/contact/add';
$params = [
    'bwfan_public_api_key' => 'your_api_key',
];

$query_string = http_build_query( $params );
$endpoint = $site_url . $endpoint . '?' . $query_string;
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => $endpoint,
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_POSTFIELDS =>'{
    "email":"abc@wisetr.com",
    "f_name": "abc",
    "l_name": "test",
    "contact_no": "1234567890",
    "country": "IN",
    "state": "Delhi",
    "status": "subscribed",
    "tags": [314,315],
    "lists": [310,316],
    "fields": {
        "40":"20-11-1993",
        "6": "Male"
    }
}',
  CURLOPT_HTTPHEADER => array(
    'Content-Type: application/json'
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;

?>
```

### HTTP REQUEST

`POST http://example.com/wp-json/autonami/contact/add`

Parameter | Type | Description                                                                                                         | Mandatory
----- |---------|---------------------------------------------------------------------------------------------------------------------|--------- 
email | string | Email for the contact                                                                                               | YES
f_name | string | First name for the contact                                                                                          | NO
l_name | string | Last name for the contact                                                                                           | NO
contact_no | string | Phone number for the contact                                                                                        | NO
status | string | Status for the contact<br> Default is subscribed</br><code>unverified, subscribed,</br>bounced, unsubscribed</code> | NO
country | string | First two letters of the country. <br> <code>Example : India - IN</code>                                            | NO
state | string | State living in                                                                                                     | NO
tags | array | array of tag ids</br><code>[id1,id2,..]</code>                                                                      | NO
lists | array | array of list ids</br><code>[id1,id2,..]</code>                                                                     | NO
fields | object | a JSON object, respectively,</br>that includes key and value</br><code>{'field_id : field value',...}</code>        | NO
source | string | Contact is getting created from.</br> Default is public_api                                                         | NO

> JSON response example:

```json
{
  "code": 200,
  "message": "Contact created successfully",
  "result": {
    "field_not_exists": [
      40
    ]
  },
  "limit": 30,
  "offset": 0
}
```

## Update a Contact

This endpoint update a contact

```php
<?php

$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/contact/update/{contact_id}';
$params = [
    'bwfan_public_api_key' => 'your_api_key',
];

$query_string = http_build_query( $params );
$endpoint = $site_url . $endpoint . '?' . $query_string;
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => $endpoint,
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_POSTFIELDS =>'{
    "email":"abc@wisetr.com",
    "f_name": "abc",
    "l_name": "test",
    "contact_no": "1234567890",
    "country": "IN",
    "state": "Delhi",
    "status": "unsubscribed",
    "fields": {
        "6": "Male"
    }
}',
  CURLOPT_HTTPHEADER => array(
    'Content-Type: application/json'
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;


?>
```

### HTTP REQUEST

`POST http://example.com/wp-json/autonami/contact/update/{contact_id}`

Parameter | Type | Description                                                                                                         | Mandatory
----- |---------|---------------------------------------------------------------------------------------------------------------------|--------- 
email | string | Email for the contact                                                                                               | NO
f_name | string | First name for the contact                                                                                          | NO
l_name | string | Last name for the contact                                                                                           | NO
contact_no | string | Phone number for the contact                                                                                        | NO
status | string | Status for the contact<br> Default is subscribed</br><code>unverified, subscribed,</br>bounced, unsubscribed</code> | NO
country | string | First two letters of the country. <br> <code>Example : India - IN</code>                                            | NO
state | string | State living in                                                                                                     | NO
tags | array | array of tag ids</br><code>[id1,id2,..]</code>                                                                      | NO
lists | array | array of list ids</br><code>[id1,id2,..]</code>                                                                     | NO
fields | object | a JSON object, respectively,</br>that includes key and value</br><code>{'field_id : field value',...}</code>        | NO
source | string | Contact is getting created from.</br> Default is public_api                                                         | NO

> JSON response example:

```json
{
  "code": 200,
  "message": "Contact updated successfully",
  "result": [],
  "limit": 30,
  "offset": 0
}
```

## Update Eamil

This endpoint update the email of the contact

```php
<?php

$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/contact/update-email/{contact_id}';
$params = [
    'bwfan_public_api_key' => 'your_api_key',
];

$query_string = http_build_query( $params );
$endpoint = $site_url . $endpoint . '?' . $query_string;

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => $endpoint,
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_POSTFIELDS =>'{
    "email": "ronit123@wisetr.com"
}',
  CURLOPT_HTTPHEADER => array(
    'Content-Type: application/json'
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;

?>
```

### HTTP REQUEST

`POST http://example.com/wp-json/autonami/contact/update-email/{contact_id}`

Parameter | Type | Description | Mandatory
----- |---------|------------|--------- 
email | string | Email for the contact | YES

> JSON response example:

```json
{
  "code": 200,
  "message": "Email updated successfully",
  "result": [],
  "limit": 30,
  "offset": 0
}
```

## Change Status

This endpoint change the status of the contact

```php
<?php

$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/contact/change-status/{contact_id}';
$params = [
    'bwfan_public_api_key' => 'your_api_key',
];

$query_string = http_build_query( $params );
$endpoint = $site_url . $endpoint . '?' . $query_string;

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => $endpoint,
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_POSTFIELDS =>'{
    "status":"subscribe"
}',
  CURLOPT_HTTPHEADER => array(
    'Content-Type: application/json'
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;

?>
```

### HTTP REQUEST

`POST http://example.com/wp-json/autonami/contact/change-status/{contact_id}`

Parameter | Type | Description                                                                           | Mandatory
----- |---------|---------------------------------------------------------------------------------------|--------- 
status | string | Status for the contact<code>unverified, </br>subscribed, bounced, unsubscribed</code> | YES

> JSON response example:

```json
{
  "code": 200,
  "message": "Status changed successfully",
  "result": [],
  "limit": 30,
  "offset": 0
}
```

## Assign Tags

This endpoint assign the tags to the contact.

```php
<?php

$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/contact/tag-assign/{contact_id}';
$params = [
    'bwfan_public_api_key' => 'your_api_key',
];

$query_string = http_build_query( $params );
$endpoint = $site_url . $endpoint . '?' . $query_string;

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => $endpoint,
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_POSTFIELDS =>'{
    "tags":[1,2]
}',
  CURLOPT_HTTPHEADER => array(
    'Content-Type: application/json'
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;

?>
```

### HTTP REQUEST

`POST http://example.com/wp-json/autonami/contact/tag-assign/{contact_id}`

Parameter | Type | Description                                 | Mandatory
----- |---------|---------------------------------------------|---------
tags | array | array of tag ids <code>[id1,id2,...]</code> | YES

> JSON response example:

```json
{
  "code": 200,
  "message": "Tag(s) assigned successfully",
  "result": [],
  "limit": 30,
  "offset": 0
}
```

## Unassign Tags

This endpoint unassign the tags from the contact.

```php
<?php

$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/contact/tag-unassign/{contact_id}';
$params = [
    'bwfan_public_api_key' => 'your_api_key',
];

$query_string = http_build_query( $params );
$endpoint = $site_url . $endpoint . '?' . $query_string;

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => $endpoint,
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_POSTFIELDS =>'{
    "tagId": [1]
}',
  CURLOPT_HTTPHEADER => array(
    'Content-Type: application/json'
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;

?>
```

### HTTP REQUEST

`POST http://example.com/wp-json/autonami/contact/tag-unassign/{contact_id}`

Parameter | Type | Description                                 | Mandatory
----- |---------|---------------------------------------------|---------
tagId | array | array of tag ids <code>[id1,id2,...]</code> | YES

> JSON response example:

```json
{
  "code": 200,
  "message": "Tag(s) unassigned successfully",
  "result": [
    1
  ],
  "limit": 30,
  "offset": 0
}
```

## Assign Lists

This endpoint assign the lists to the contact.

```php
<?php

$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/contact/list-assign/{contact_id}';
$params = [
    'bwfan_public_api_key' => 'your_api_key',
];

$query_string = http_build_query( $params );
$endpoint = $site_url . $endpoint . '?' . $query_string;

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => $endpoint,
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_POSTFIELDS =>'{
    "lists": [4]
}',
  CURLOPT_HTTPHEADER => array(
    'Content-Type: application/json'
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;

?>
```

### HTTP REQUEST

`POST http://example.com/wp-json/autonami/contact/list-assign/{contact_id}`

Parameter | Type | Description                                  | Mandatory
----- |---------|----------------------------------------------|---------
lists | array | array of list ids <code>[id1,id2,...]</code> | YES

> JSON response example:

```json
{
  "code": 200,
  "message": "List(s) assigned successfully",
  "result": [],
  "limit": 30,
  "offset": 0
}
```

## Unassign Lists

This endpoint unassign the lists from the contact.

```php
<?php

$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/contact/list-unassign/{contact_id}';
$params = [
    'bwfan_public_api_key' => 'your_api_key',
];

$query_string = http_build_query( $params );
$endpoint = $site_url . $endpoint . '?' . $query_string;

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => $endpoint,
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_POSTFIELDS =>'{
    "listId": [4]
}',
  CURLOPT_HTTPHEADER => array(
    'Content-Type: application/json'
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;

?>
```

### HTTP REQUEST

`POST http://example.com/wp-json/autonami/contact/list-unassign/{contact_id}`

Parameter | Type | Description                                  | Mandatory
----- |---------|----------------------------------------------|---------
listId | array | array of list ids <code>[id1,id2,...]</code> | YES

> JSON response example:

```json
{
  "code": 200,
  "message": "List(s) unassigned successfully",
  "result": [
    4
  ],
  "limit": 30,
  "offset": 0
}
```

## Delete a contact

This endpoint delete a contact.

```php
<?php

$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/contact/delete/{contact_id}';
$params = [
    'bwfan_public_api_key' => 'your_api_key',
];

$query_string = http_build_query( $params );
$endpoint = $site_url . $endpoint . '?' . $query_string;

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => $endpoint,
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'DELETE',
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;

?>
```

### HTTP REQUEST

`DELETE http://example.com/wp-json/autonami/contact/delete/{contact_id}`

Parameter | Type  | Description | Mandatory
----- |-------|-------------|----------

> JSON response example:

```json
{
  "code": 200,
  "message": "Contact deleted successfully",
  "result": [],
  "limit": 30,
  "offset": 0
}
```
