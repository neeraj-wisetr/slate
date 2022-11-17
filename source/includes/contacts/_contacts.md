# Contacts

The contacts API allows you to create, view, update, and delete individual, or a batch of contacts.

Parameter | Type   | Description | Mandatory
--------- |--------| ----------- | ----------- 
api_key | string | Api key for authorization | YES

## Get All Contacts

Returns the list of all the contacts.

```shell
Get All Contacts
GET http://example.com/wp-json/funnelkit-automations/contacts

    curl --location --request GET 'http://example.com/wp-json/funnelkit-automations/contacts' \
    --header 'api_key: {api-key}' \
    --header 'Content-Type: application/json' \
    --data-raw ''
```

```php
<?php
$site_url = 'http://example.com';
$endpoint = '/wp-json/funnelkit-automations/contacts';
$params = [
    'api_key' => 'your_api_key',
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

`GET http://example.com/wp-json/funnelkit-automations/contacts`

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
  "code": "success",
  "data": {
    "contact": {
      "contacts": [
        {
          "id": "1",
          "wpid": "0",
          "uid": "8264f563ca27ab672b9665a8da42a500",
          "email": "gary@gmail.com",
          "f_name": "Gary",
          "l_name": "Watson",
          "contact_no": "1234567890",
          "country": "AU",
          "state": "Sydney",
          "timezone": "",
          "type": "lead",
          "source": "public_api",
          "points": "0",
          "tags": "[]",
          "lists": "[]",
          "last_modified": "2022-08-09 16:23:20",
          "creation_date": "2022-08-09 16:23:20",
          "status": "0"
        },
        {
          "id": "2",
          "wpid": "12",
          "uid": "d7b6762adbcf73f382b12a37b3cdf5e9",
          "email": "rosy@gmail.com",
          "f_name": "Rosy",
          "l_name": "Maria",
          "contact_no": "+1234567890",
          "country": "USA",
          "state": "New York",
          "timezone": "America/New York",
          "type": "customer",
          "source": "wc_order",
          "points": "0",
          "tags": "[1,2,3]",
          "lists": "[]",
          "last_modified": "2022-08-01 17:33:48",
          "creation_date": "2022-07-13 11:23:16",
          "status": "1"
        }
      ],
      "total": ""
    },
    "limit": 0,
    "offset": 0
  }
}
```

## Get Contact by ID or Email

Returns contact details of specified id or email.

```shell
Get Contact by ID or Email
GET http://example.com/wp-json/funnelkit-automations/contact

    curl --location --request GET 'http://example.com/wp-json/funnelkit-automations/contact' \
    --header 'api_key: {api-key}' \
    --header 'Content-Type: application/json' \
    --header 'id: 1' \
    --header 'email: gary@gmail.com' \
    --data-raw ''
```

```php
<?php
$site_url = 'http://example.com';
$endpoint = '/wp-json/funnelkit-automations/contact';
$params = [
    'api_key' => 'your_api_key',
    'id'      => 1,
    'email'   => 'gary@gmail.com'
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

`GET http://example.com/wp-json/funnelkit-automations/contact`

Parameter | Type | Description          | Mandatory
--------- |------|----------------------| -----------
id  | integer | Id of the contact | NO
email | string | Email of the contact | NO

<aside class="notice">
One of the id or email need to be provided. If provided both, then contact will be fetched by id.
</aside>

> JSON response example:

```json
{
  "code": "success",
  "data": {
    "contact": {
      "contact": {
        "id": "1",
        "uid": null,
        "email": "gary@gmail.com",
        "wp_id": "3",
        "meta": {},
        "children": {},
        "db_contact": {
          "id": "1",
          "wpid": "0",
          "uid": "8264f563ca27ab672b9665a8da42a500",
          "email": "gary@gmail.com",
          "f_name": "Gary",
          "l_name": "Watson",
          "contact_no": "1234567890",
          "country": "AU",
          "state": "Sydney",
          "timezone": "",
          "type": "lead",
          "source": "public_api",
          "points": "0",
          "tags": "[]",
          "lists": "[]",
          "last_modified": "2022-08-09 16:23:20",
          "creation_date": "2022-08-09 16:23:20",
          "status": "0"
        },
        
        "blank_values_update": false,
        "is_subscribed": false
      },
      "customer": null,
      "fields": {
        "1": "New York",
        "2": "America",
        "3": "USA",
        "4": "abc",
        "5": "Male"
      }
    },
    "limit": 0,
    "offset": 0
  }
}
```

## Add Contact

Adds a specific contact.

```shell
Add Contact
POST http://example.com/wp-json/funnelkit-automations/contact/add
    curl --location --request POST 'http://example.com/wp-json/funnelkit-automations/contact/add' \
    --header 'api_key: {api-key}' \
    --header 'Content-Type: application/json' \
    --data-raw '{
        "email":"tyson@gmail.com",
        "f_name": "Tyson",
        "l_name": "Andrew",
        "contact_no": "1234567890",
        "country": "AU",
        "state": "Melbourne",
        "status": "subscribed",
        "tags": [1,2],
        "lists": [1,2],
        "fields": {
            "40":"20-11-1993",
            "6": "Male"
        }
    }' 
```

```php
<?php

$site_url = 'http://example.com';
$endpoint = '/wp-json/funnelkit-automations/contact/add';
$params = [
    'api_key' => 'your_api_key',
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
        "email":"tyson@gmail.com",
        "f_name": "Tyson",
        "l_name": "Andrew",
        "contact_no": "1234567890",
        "country": "AU",
        "state": "Melbourne",
        "status": "subscribed",
        "tags": [1,2],
        "lists": [1,2],
        "fields": {
            "1":"20-11-1993",
            "2": "Male"
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

`POST http://example.com/wp-json/funnelkit-automations/contact/add`

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
  "code": "success",
  "data": {
    "contact": {
      "contact": {
        "id": 1,
        "uid": "f1b1bbeb5258c9ec4896c025118b23da",
        "email": "tyson@gmail.com",
        "wp_id": 0,
        "meta": {},
        "children": {},
        "db_contact": null,
        "blank_values_update": false,
        "is_subscribed": false,
        "f_name": "Tyson",
        "l_name": "Andrew",
        "state": "Melbourne",
        "country": "AU",
        "contact_no": "1234567890",
        "status": 0,
        "source": "public_api",
        "type": "lead"
      },
      "customer": null,
      "fields": {
        "1":"20-11-1993",
        "2": "Male"
      }
    },
    "limit": 0,
    "offset": 0
  }
}
```

## Update a Contact

Updates a particular contact.

```shell
Update a Contact
POST http://example.com/wp-json/funnelkit-automations/contact/update/{contact_id}
    curl --location --request POST 'http://example.com/wp-json/funnelkit-automations/contact/update/{contact_id}' \
    --header 'api_key: {api-key}' \
    --header 'Content-Type: application/json' \
    --data-raw '{
        "email":"gary@gmail.com",
        "f_name": "Gary",
        "l_name": "Watson",
        "contact_no": "1234567890",
        "country": "Au",
        "state": "Sydney",
        "status": "unsubscribed",
        "fields": {
            "6": "Male"
        }
    }'
```

```php
<?php

$site_url = 'http://example.com';
$endpoint = '/wp-json/funnelkit-automations/contact/update/{contact_id}';
$params = [
    'api_key' => 'your_api_key',
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
        "email":"gary@gmail.com",
        "f_name": "Gary",
        "l_name": "Watson",
        "contact_no": "1234567890",
        "country": "Au",
        "state": "Sydney",
        "status": "unsubscribed",
        "fields": {
            "5": "Male"
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

`POST http://example.com/wp-json/funnelkit-automations/contact/update/{contact_id}`

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
  "code": "success",
  "data": {
    "contact": {
      "contact": {
        "id": "1",
        "uid": null,
        "email": "gary@gmail.com",
        "wp_id": "3",
        "meta": {},
        "children": {},
        "db_contact": {
          "id": "1",
          "wpid": "3",
          "uid": "9f20c97f3dcba190c31c7f811f11c730",
          "email": "gary@gmail.com",
          "f_name": "Gary",
          "l_name": "Watson",
          "contact_no": "1234567890",
          "country": "AU",
          "state": "Sydney",
          "timezone": "Australia/Sydney",
          "type": "customer",
          "source": "wc_order",
          "points": "0",
          "tags": "[1,2,3]",
          "lists": "[]",
          "last_modified": "2022-08-10 14:00:03",
          "creation_date": "2022-04-21 12:08:22",
          "status": "1"
        },
        "blank_values_update": false,
        "is_subscribed": false
      },
      "customer": null,
      "fields": {
        "1": "Sydney",
        "2": "Australia",
        "3": "2009",
        "4": "abc",
        "5": "Male"
      }
    },
    "limit": 0,
    "offset": 0
  }
}
```

## Update Email

Updates email of the contact

```shell
Update Email
POST http://example.com/wp-json/funnelkit-automations/contact/update-email/{contact_id}
    curl --location --request POST 'POST http://example.com/wp-json/funnelkit-automations/contact/update-email/{contact_id}' \
    --header 'api_key: {api-key}' \
    --header 'Content-Type: application/json' \
    --data-raw '{
        "email": "gary.w@gmail.com"
    }'
```

```php
<?php

$site_url = 'http://example.com';
$endpoint = '/wp-json/funnelkit-automations/contact/update-email/{contact_id}';
$params = [
    'api_key' => 'your_api_key',
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
    "email": "gary.w@gmail.com"
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

`POST http://example.com/wp-json/funnelkit-automations/contact/update-email/{contact_id}`

Parameter | Type | Description | Mandatory
----- |---------|------------|--------- 
email | string | Email for the contact | YES

> JSON response example:

```json
{
  "code": "success",
  "data": {
    "contact": {
      "contact": {
        "id": "1",
        "uid": null,
        "email": "gary.w@gmail.com",
        "wp_id": "3",
        "meta": {},
        "children": {},
        "db_contact": {
          "id": "9",
          "wpid": "3",
          "uid": "9f20c97f3dcba190c31c7f811f11c730",
          "email": "gary.w@gmail.com",
          "f_name": "Gary",
          "l_name": "Watson",
          "contact_no": "1234567890",
          "country": "AU",
          "state": "Sydney",
          "timezone": "America/Sydney",
          "type": "customer",
          "source": "wc_order",
          "points": "0",
          "tags": "[1,2,3]",
          "lists": "[]",
          "last_modified": "2022-08-10 17:46:30",
          "creation_date": "2022-04-21 12:08:22",
          "status": "1"
        },
        "blank_values_update": false,
        "is_subscribed": false
      },
      "customer": null,
      "fields": {
        "1": "Sydney",
        "2": "Australia",
        "3": "2009",
        "4": "abc",
        "5": "Male"
      }
    },
    "limit": 0,
    "offset": 0
  }
}
```

## Change Status

Updates status of the contact

```shell
Change Status
POST http://example.com/wp-json/funnelkit-automations/contact/change-status/{contact_id}
    curl --location --request POST 'http://example.com/wp-json/funnelkit-automations/contact/change-status/{contact_id}' \
    --header 'api_key: {api-key}' \
    --header 'Content-Type: application/json' \
    --data-raw '{
        "status":"subscribe"
    }'

```

```php
<?php

$site_url = 'http://example.com';
$endpoint = '/wp-json/funnelkit-automations/contact/change-status/{contact_id}';
$params = [
    'api_key' => 'your_api_key',
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

`POST http://example.com/wp-json/funnelkit-automations/contact/change-status/{contact_id}`

Parameter | Type | Description                                                                                | Mandatory
----- |---------|--------------------------------------------------------------------------------------------|--------- 
status | string | Status for the contact</br><code>unverified, subscribed, bounced, </br>unsubscribed</code> | YES

> JSON response example:

```json
{
  "code": "success",
  "data": {
    "contact": {
      "contact": {
        "id": "1",
        "uid": null,
        "email": "gary.w@gmail.com",
        "wp_id": "3",
        "meta": {},
        "children": {},
        "db_contact": {
          "id": "1",
          "wpid": "3",
          "uid": "9f20c97f3dcba190c31c7f811f11c730",
          "email": "gary.w@gmail.com",
          "f_name": "Gary",
          "l_name": "Watson",
          "contact_no": "1234567890",
          "country": "AU",
          "state": "Sydney",
          "timezone": "Australia/Sydney",
          "type": "customer",
          "source": "wc_order",
          "points": "0",
          "tags": "[1,2,3]",
          "lists": "[]",
          "last_modified": "2022-08-10 17:46:30",
          "creation_date": "2022-04-21 12:08:22",
          "status": "1"
        },
        "blank_values_update": false,
        "is_subscribed": false
      },
      "customer": null,
      "fields": {
        "1": "Sydney",
        "2": "Australia",
        "3": "2009",
        "4": "abc",
        "5": "Male"
      }
    },
    "limit": 0,
    "offset": 0
  }
}
```

## Assign Tags

Assign tags to the contact.

```shell
Assign Tags
POST http://example.com/wp-json/funnelkit-automations/contact/tag-assign/{contact_id}
    curl --location -g --request POST 'http://example.com/wp-json/funnelkit-automations/contact/tag-assign/{contact_id}' \
    --header 'api_key: {api-key}' \
    --header 'Content-Type: application/json' \
    --data-raw '{
        "tags":[1,2]
    }'
```

```php
<?php

$site_url = 'http://example.com';
$endpoint = '/wp-json/funnelkit-automations/contact/tag-assign/{contact_id}';
$params = [
    'api_key' => 'your_api_key',
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

`POST http://example.com/wp-json/funnelkit-automations/contact/tag-assign/{contact_id}`

Parameter | Type | Description                                 | Mandatory
----- |---------|---------------------------------------------|---------
tags | array | array of tag ids <code>[id1,id2,...]</code> | YES

> JSON response example:

```json
{
  "code": "success",
  "data": {
    "tags": [
      {
        "id": "1",
        "value": "Tag 1"
      },
      {
        "id": "2",
        "value": "Tag 2"
      }
    ],
    "limit": 0,
    "offset": 0
  }
}
```

## Unassign Tags

Unassign tags from the contact.

```shell
Unassign Tags
POST http://example.com/wp-json/funnelkit-automations/contact/tag-unassign/{contact_id}
    curl --location -g --request POST 'http://example.com/wp-json/funnelkit-automations/contact/tag-unassign/{contact_id}' \
    --header 'api_key: {api-key}' \
    --header 'Content-Type: application/json' \
    --data-raw '{
        "tagId": [1]
    }' 
```

```php
<?php

$site_url = 'http://example.com';
$endpoint = '/wp-json/funnelkit-automations/contact/tag-unassign/{contact_id}';
$params = [
    'api_key' => 'your_api_key',
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

`POST http://example.com/wp-json/funnelkit-automations/contact/tag-unassign/{contact_id}`

Parameter | Type | Description                                 | Mandatory
----- |---------|---------------------------------------------|---------
tagId | array | array of tag ids <code>[id1,id2,...]</code> | YES

> JSON response example:

```json
{
  "code": "success",
  "data": {
    "tags": [
      {
        "id": "1",
        "value": "Tag 1"
      }
    ],
    "limit": 0,
    "offset": 0
  }
}
```

## Assign Lists

Assign lists to the contact.

```shell
Assign Lists
POST http://example.com/wp-json/funnelkit-automations/contact/list-assign/{contact_id}
    curl --location -g --request POST 'http://example.com/wp-json/funnelkit-automations/contact/list-assign/{contact_id}' \
    --header 'api_key: {api-key}' \
    --header 'Content-Type: application/json' \
    --data-raw '{
        "lists": [1]
    }'
```

```php
<?php

$site_url = 'http://example.com';
$endpoint = '/wp-json/funnelkit-automations/contact/list-assign/{contact_id}';
$params = [
    'api_key' => 'your_api_key',
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
    "lists": [1]
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

`POST http://example.com/wp-json/funnelkit-automations/contact/list-assign/{contact_id}`

Parameter | Type | Description                                  | Mandatory
----- |---------|----------------------------------------------|---------
lists | array | array of list ids <code>[id1,id2,...]</code> | YES

> JSON response example:

```json
{
  "code": "success",
  "data": {
    "lists": [
      {
        "id": "1",
        "value": "List 1"
      }
    ],
    "limit": 0,
    "offset": 0
  }
}
```

## Unassign Lists

Unassign lists from the contact.

```shell
Unassign Lists
POST http://example.com/wp-json/funnelkit-automations/contact/list-unassign/{contact_id}
    curl --location --request POST 'http://example.com/wp-json/funnelkit-automations/contact/list-unassign/{contact_id}' \
    --header 'api_key: {api-key}' \
    --header 'Content-Type: application/json' \
    --data-raw '{
        "listId": [1]
    }'
```

```php
<?php

$site_url = 'http://example.com';
$endpoint = '/wp-json/funnelkit-automations/contact/list-unassign/{contact_id}';
$params = [
    'api_key' => 'your_api_key',
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
    "listId": [1]
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

`POST http://example.com/wp-json/funnelkit-automations/contact/list-unassign/{contact_id}`

Parameter | Type | Description                                  | Mandatory
----- |---------|----------------------------------------------|---------
listId | array | array of list ids <code>[id1,id2,...]</code> | YES

> JSON response example:

```json
{
  "code": "success",
  "data": {
    "lists": [
      {
        "id": "1",
        "value": "List 1"
      }
    ],
    "limit": 0,
    "offset": 0
  }
}
```

## Delete a contact

Deletes a contact permanently.

```shell
Delete a contact
DELETE http://example.com/wp-json/funnelkit-automations/contact/{contact_id}
    curl --location -g --request DELETE 'http://example.com/wp-json/funnelkit-automations/contact/{contact_id}' \
    --header 'api_key: {api-key}' \
    --header 'Content-Type: application/json' \
    --data-raw ''  
```

```php
<?php

$site_url = 'http://example.com';
$endpoint = '/wp-json/funnelkit-automations/contact/{contact_id}';
$params = [
    'api_key' => 'your_api_key',
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

`DELETE http://example.com/wp-json/funnelkit-automations/contact/{contact_id}`

Parameter | Type  | Description | Mandatory
----- |-------|-------------|----------

> JSON response example:

```json
{
  "code": "success",
  "data": {
    "limit": 0,
    "offset": 0
  }
}
```
