# Fields

The fields API allows you to create, view, update, and delete individual, or a batch of custom fields.

Parameter | Type   | Description | Mandatory
--------- |--------| ----------- | -----------
bwfan_public_api_key | string | Api key for authorization | YES

## Get All Fields

This endpoint retrieves all fields.

```php
<?php
$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/fields';
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
  CURLOPT_POSTFIELDS =>'{
    "page": 1
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

### HTTP Request

`GET http://example.com/wp-json/autonami/fields`

Parameter | Type   | Description | Mandatory
--------- |--------| ----------- | -----------
page | integer | Current page of the collection | NO.


> JSON response example:

```json
{
  "code": 200,
  "message": "Fields listed successfully",
  "result": {
    "1": {
      "group_id": "0",
      "ID": "1",
      "name": "Address 1",
      "type": "1",
      "meta": [],
      "created_at": "2022-04-06 11:39:17",
      "slug": "address-1"
    },
    "2": {
      "group_id": "0",
      "ID": "2",
      "name": "Address 2",
      "type": "1",
      "meta": [],
      "created_at": "2022-04-06 11:39:17",
      "slug": "address-2"
    },
    "3": {
      "group_id": "0",
      "ID": "3",
      "name": "City",
      "type": "1",
      "meta": [],
      "created_at": "2022-04-06 11:39:17",
      "slug": "city"
    },
    "4": {
      "group_id": "0",
      "ID": "4",
      "name": "Pincode",
      "type": "1",
      "meta": [],
      "created_at": "2022-04-06 11:39:17",
      "slug": "postcode"
    },
    "5": {
      "group_id": "0",
      "ID": "5",
      "name": "Company",
      "type": "1",
      "meta": [],
      "created_at": "2022-04-06 11:39:17",
      "slug": "company"
    },
    "6": {
      "group_id": "0",
      "ID": "6",
      "name": "Gender",
      "type": "4",
      "meta": {
        "options": [
          "Male",
          "Female",
          "Other"
        ]
      },
      "created_at": "2022-04-06 11:39:17",
      "slug": "gender"
    },
    "7": {
      "group_id": "0",
      "ID": "7",
      "name": "Date of Birth",
      "type": "7",
      "meta": [],
      "created_at": "2022-04-06 11:39:17",
      "slug": "dob"
    }
  },
  "limit": 30,
  "offset": 0
}
```

## Add Field

This endpoint add the field.

```php
<?php
$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/field/add';
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
    "field_name": "doa",
    "type": 7,
    "placeholder": "Date of appoinment",
    "mode": 1,
    "vmode": 1,
    "search": 1
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

### HTTP Request

`POST http://example.com/wp-json/autonami/field/add`

Parameter | Type    | Description | Mandatory
--------- |---------| ----------- | -----------
field_name | string  | Name of the field | YES
group_id | integer | Field group id. Default is 0 | NO
type | integer | Input type. <code></br>1 - text, </br>2 - number,</br>3 - textarea,</br>4 - select, </br>5 - radio, </br>6 - checkbox, </br>7 - date</code> | YES
placeholder | string  | Placeholder for the field | NO
mode | integer | Field is editable or not.</br>Default is 1<code></br>1 - editable, </br> 2 - non-editable</code> | NO
vmode | integer | Field is editable or not.</br>Default is 1<code></br>1 - editable, </br> 2 - non-editable</code> | NO
search | integer | Field is searchable or not.</br>Default is 1 <code></br>1 - searchable, </br> 2 - non-searchable</code> | NO
options | array   | an array of JSON objects <code></br>['key1'=>'option1',...]</code> | NO

> JSON response example:

```json
{
  "code": 200,
  "message": "Field created successfully",
  "result": {
    "ID": "19",
    "name": "doa",
    "slug": "doa",
    "type": "7",
    "gid": "0",
    "meta": {
      "placeholder": "Date of appoinment"
    },
    "mode": "1",
    "vmode": "1",
    "search": "1",
    "view": "1",
    "created_at": "2022-04-14 04:13:55"
  },
  "limit": 30,
  "offset": 0
}
```

## Update A Field

This endpoint update the field.

```php
<?php
$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/field/update/{field_id}';
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
    "slug":"doa",
   "field_name": "doj",
    "type": 7,
    "placeholder": "Date of joining",
    "mode": 1,
    "vmode": 1,
    "search": 1
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

### HTTP Request

`POST http://example.com/wp-json/autonami/field/update/{field_id}`

Parameter | Type    | Description | Mandatory
--------- |---------| ----------- | -----------
slug | string  | Slug of the updating field | YES
field_name | string  | Name of the field | YES
group_id | integer | Field group id. Default is 0 | NO
type | integer | Input type. <code></br>1 - text, </br>2 - number,</br>3 - textarea,</br>4 - select, </br>5 - radio, </br>6 - checkbox, </br>7 - date</code> | NO
placeholder | string  | Placeholder for the field | NO
mode | integer | Field is editable or not.</br>Default is 1<code></br>1 - editable, </br> 2 - non-editable</code> | NO
vmode | integer | Field is editable or not.</br>Default is 1<code></br>1 - editable, </br> 2 - non-editable</code> | NO
search | integer | Field is searchable or not.</br>Default is 1 <code></br>1 - searchable, </br> 2 - non-searchable</code> | NO
options | array   | an array of JSON objects <code></br>['key1'=>'option1',...]</code> | NO

> JSON response example:

```json
{
  "code": 200,
  "message": "Field updated successfully",
  "result": [],
  "limit": 30,
  "offset": 0
}
```

## Delete A Field

This endpoint delete the field.

```php
<?php
$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/field/delete/{field_id}';
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

### HTTP Request

`DELETE http://example.com/wp-json/autonami/field/delete/{field_id}`

Parameter | Type | Description | Mandatory
--------- |------| ----------- | -----------

> JSON response example:

```json
{
  "code": 200,
  "message": "Field deleted successfully",
  "result": [],
  "limit": 30,
  "offset": 0
}
```
