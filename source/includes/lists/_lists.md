# Lists

The Lists API allows you to create, view, update, and delete an individual, or a batch of lists.

Parameter | Type   | Description | MANDATORY
--------- |--------| ----------- | -----------
api_key | string | Api key for authorization | YES

## Get All Lists

Returns all the lists.

```shell
Get All Lists
GET http://example.com/wp-json/funnelkit-automations/lists
    curl --location --request GET 'http://example.com/wp-json/funnelkit-automations/lists' \
    --header 'api_key: b457e81b66663e7839ff318c806b4a2f' \
    --header 'Content-Type: application/json' \
    --data-raw '
    {
        "page": 1
    }'

```

```php
<?php
$site_url = 'http://example.com';
$endpoint = '/wp-json/funnelkit-automations/lists';
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

`GET http://example.com/wp-json/funnelkit-automations/lists`

Parameter | Type   | Description | MANDATORY
--------- |--------| ----------- | -----------
page | integer | Current page of the collection | NO

> JSON response example:

```json
{
  "code": "success",
  "data": {
    "lists": [
      {
        "ID": 6,
        "name": "list2"
      },
      {
        "ID": 4,
        "name": "list1"
      }
    ],
    "limit": 0,
    "offset": 0
  }
}
```

## Add Lists

Adds a specific list.

```shell
Add Lists
POST http://example.com/wp-json/funnelkit-automations/list/add

    curl --location --request POST 'http://example.com/wp-json/funnelkit-automations/list/add' \
    --header 'api_key: {api-key}' \
    --header 'Content-Type: application/json' \
    --data-raw '
    {
    "lists": ["list"]
    }'
```

```php
<?php
$site_url = 'http://example.com';
$endpoint = '/wp-json/funnelkit-automations/list/add';
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
  "lists": ["list","lists2", ...]
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

`POST http://example.com/wp-json/funnelkit-automations/list/add`

Parameter | Type  | Description | MANDATORY
--------- |-------| ----------- | -----------
lists | array | an array of JSON objects, respectively, that includes the list name - <code>{"lists": ["list","lists2", ...]}</code> | YES

> JSON response example:

```json
{
  "code": "success",
  "data": {
    "lists": [
      {
        "ID": 31,
        "name": "bulkgate",
        "type": "2",
        "created_at": "2022-08-10 11:22:00",
        "updated_at": null,
        "data": null
      }
    ],
    "limit": 0,
    "offset": 0
  }
}
```

## Update A List

Updates a particular list.

```shell
Update A List
POST http://example.com/wp-json/funnelkit-automations/list/update/{list_id}

    curl --location --request POST 'http://example.com/wp-json/funnelkit-automations/list/update/{list_id}' \
    --header 'api_key: {api-key}' \
    --header 'Content-Type: application/json' \
    --data-raw ''
```

```php
<?php
$site_url = 'http://example.com';
$endpoint = '/wp-json/funnelkit-automations/list/update/{list_id}';
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
  "list": "list_name"
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

`POST http://example.com/wp-json/funnelkit-automations/list/update/{list_id}`

Parameter | Type   | Description | MANDATORY
--------- |--------| ----------- | -----------
list | string | a JSON object, respectively, that includes the list name - <code>{"list": "list_name"}</code> | YES

> JSON response example:

```json
{
  "code": "success",
  "data": {
    "lists": {
      "ID": "31",
      "name": "bulkgate2"
    },
    "limit": 0,
    "offset": 0
  }
}
```

## Delete A List

Deletes a list permanently.

```shell
Delete A List
DELETE http://example.com/wp-json/funnelkit-automations/list/{list_id}
    curl --location --request DELETE 'http://example.com/wp-json/funnelkit-automations/list/{list_id}' \
    --header 'api_key: {api-key}' \
    --header 'Content-Type: application/json' \
    --data-raw ''
```

```php
<?php
$site_url = 'http://example.com';
$endpoint = '/wp-json/funnelkit-automations/list/{list_id}';
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

`DELETE http://example.com/wp-json/funnelkit-automations/list/{list_id}`

Parameter | Type | Description | MANDATORY
--------- |------| ----------- | -----------

> JSON response example:

```json
{
  "code": "success",
  "data": {
    "lists": {
      "ID": "31",
      "name": "bulkgate2"
    },
    "limit": 0,
    "offset": 0
  }
}
```
