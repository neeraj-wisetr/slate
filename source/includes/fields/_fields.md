# Fields

The fields API allows you to create, view, update, and delete individual, or a batch of custom fields.

Parameter | Type   | Description | Mandatory
--------- |--------| ----------- | -----------
api_key | string | Api key for authorization | YES

## Get All Fields

Returns the list of all the fields.

```shell
Get All Fields
GET http://example.com/wp-json/funnelkit-automations/fields

    curl --location --request GET 'http://example.com/wp-json/funnelkit-automations/fields' \
    --header 'api_key:{api-key}' \
    --header 'Content-Type: application/json' \
    --data-raw '{
        "page": 1
    }'
```

```php
<?php
$site_url = 'http://example.com';
$endpoint = '/wp-json/funnelkit-automations/fields';
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

`GET http://example.com/wp-json/funnelkit-automations/fields`

Parameter | Type   | Description | Mandatory
--------- |--------| ----------- | -----------
page | integer | Current page of the collection | NO

> JSON response example:

```json
{
  "code": "success",
  "data": {
    "fields": {
      "1": {
        "group_id": "0",
        "ID": "1",
        "name": "Custom Field 1",
        "type": "1",
        "meta": [],
        "created_at": "2022-04-06 11:39:17",
        "slug": "Custom Field 1"
      },
      "2": {
        "group_id": "0",
        "ID": "2",
        "name": "Custom Field 2",
        "type": "4",
        "meta": {
          "options": [
            "Male",
            "Female",
            "Other"
          ]
        },
        "created_at": "2022-04-06 11:39:17",
        "slug": "Custom Field 2"
      }
    },
    "limit": 0,
    "offset": 0
  }
}
```

## Add Field

Adds a specific field.

```shell
Add Field
POST http://example.com/wp-json/funnelkit-automations/field/add

    curl --location --request POST 'wp-json/funnelkit-automations/field/add' \
    --header 'api_key: {api-key}' \
    --header 'Content-Type: application/json' \
    --data-raw '{
        "field_name": "custom_field",
        "type": 7,
        "placeholder": "Custom Field",
        "mode": 1,
        "search": 1
    }'
```

```php
<?php
$site_url = 'http://example.com';
$endpoint = '/wp-json/funnelkit-automations/field/add';
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
    "field_name": "custom_field",
    "type": 7,
    "placeholder": "Custom Field",
    "mode": 1,
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

`POST http://example.com/wp-json/funnelkit-automations/field/add`

Parameter | Type    | Description | Mandatory
--------- |---------| ----------- | -----------
field_name | string  | Name of the field | YES
group_id | integer | Field group id. Default is 0 | NO
type | integer | Input type. <code></br>1 - text, </br>2 - number,</br>3 - textarea,</br>4 - select, </br>5 - radio, </br>6 - checkbox, </br>7 - date</code> | YES
placeholder | string  | Placeholder for the field | NO
mode | integer | Field is editable or not.</br>Default is 1<code></br>1 - editable, </br> 2 - non-editable</code> | NO
search | integer | Field is searchable or not.</br>Default is 1 <code></br>1 - searchable, </br> 2 - non-searchable</code> | NO
options | array   | an array of JSON objects <code></br>['key1'=>'option1',...]</code> | NO

> JSON response example:

```json
{
  "code": "success",
  "data": {
    "fields": {
      "ID": "1",
      "name": "custom_field",
      "slug": "custom_field",
      "type": "7",
      "gid": "0",
      "meta": {
        "placeholder": "Custom Field"
      },
      "mode": "1",
      "search": "1",
      "view": "1",
      "created_at": "2022-08-10 11:50:25"
    },
    "limit": 0,
    "offset": 0
  }
}
```

## Update A Field

Updates a particular field.

```shell
Update A Field
POST http://example.com/wp-json/funnelkit-automations/field/update/{field_id}

    curl --location --request POST 'http://example.com/wp-json/funnelkit-automations/field/update/{field_id}' \
    --header 'api_key: {api-key}' \
    --header 'Content-Type: application/json' \
    --data-raw '{
        "slug":"custom_field",
    "field_name": "custom_field2",
        "type": 7,
        "placeholder": "Custom Field 2",
        "mode": 1,
        "search": 1
    }'
```

```php
<?php
$site_url = 'http://example.com';
$endpoint = '/wp-json/funnelkit-automations/field/update/{field_id}';
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
    "slug":"custom_field",
   "field_name": "custom_field2",
    "type": 7,
    "placeholder": "Custom Field 2",
    "mode": 1,
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

`POST http://example.com/wp-json/funnelkit-automations/field/update/{field_id}`

Parameter | Type    | Description | Mandatory
--------- |---------| ----------- | -----------
slug | string  | Slug of the updating field | YES
field_name | string  | Name of the field | YES
group_id | integer | Field group id. Default is 0 | NO
type | integer | Input type. <code></br>1 - text, </br>2 - number,</br>3 - textarea,</br>4 - select, </br>5 - radio, </br>6 - checkbox, </br>7 - date</code> | NO
placeholder | string  | Placeholder for the field | NO
mode | integer | Field is editable or not.</br>Default is 1<code></br>1 - editable, </br> 2 - non-editable</code> | NO
search | integer | Field is searchable or not.</br>Default is 1 <code></br>1 - searchable, </br> 2 - non-searchable</code> | NO
options | array   | an array of JSON objects <code></br>['key1'=>'option1',...]</code> | NO

> JSON response example:

```json
{
  "code": "success",
  "data": {
    "fields": {
      "ID": "1",
      "name": "custom_field2"
    },
    "limit": 0,
    "offset": 0
  }
}
```

## Delete A Field

Deletes a field permanently.

```shell
Delete A Field
DELETE http://example.com/wp-json/funnelkit-automations/field/{field_id}

    curl --location --request DELETE 'http://example.com/wp-json/funnelkit-automations/field/{field_id}' \
    --header 'api_key: {api-key}' \
    --header 'Content-Type: application/json' \
    --data-raw ''
```

```php
<?php
$site_url = 'http://example.com';
$endpoint = '/wp-json/funnelkit-automations/field/{field_id}';
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

### HTTP Request

`DELETE http://example.com/wp-json/funnelkit-automations/field/{field_id}`

Parameter | Type | Description | Mandatory
--------- |------| ----------- | -----------

> JSON response example:

```json
{
  "code": "success",
  "data": {
    "fields": {
      "ID": "1",
      "name": "custom_field"
    },
    "limit": 0,
    "offset": 0
  }
}
```
