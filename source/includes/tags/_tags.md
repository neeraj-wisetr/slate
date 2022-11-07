# Tags

The tags API allows you to create, view, update, and delete an individual, or a batch of tags.

Parameter | Type   | Description | Mandatory
--------- |--------| ----------- | -----------
api_key | string | Api key for authorization | YES

## Get All Tags

Returns the list of all the tags.

```shell
Get All Tags
GET http://example.com/wp-json/funnelkit-automations/tags

    curl --location --request GET 'http://example.com/wp-json/funnelkit-automations/tags' \
    --header 'api_key: {api-key}' \
    --header 'Content-Type: application/json' \
    --data-raw '{
        "page": 1
    }'
```

```php
<?php
$site_url = 'http://example.com';
$endpoint = '/wp-json/funnelkit-automations/tags';
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

`GET http://example.com/wp-json/funnelkit-automations/tags`

Parameter | Type   | Description | Mandatory
--------- |--------| ----------- | -----------
page | integer | Current page of the collection | NO


> JSON response example:

```json
{
  "code": "success",
  "data": {
    "tags": [
      {
        "ID": 7,
        "name": "xl nextmove"
      },
      {
        "ID": 2,
        "name": "nks2"
      },
      {
        "ID": 1,
        "name": "nks"
      }
    ],
    "limit": 0,
    "offset": 0
  }
}
```

## Add Tags

Adds a specific tag.

```shell
Add Tags
POST http://example.com/wp-json/funnelkit-automations/tag/add
    curl --location --request POST 'http://example.com/wp-json/funnelkit-automations/tag/add' \
    --header 'api_key: {api-key}' \
    --header 'Content-Type: application/json' \
    --data-raw '
    { "tags": ["tag","tag2"]
    }'
```

```php
<?php
$site_url = 'http://example.com';
$endpoint = '/wp-json/funnelkit-automations/tag/add';
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
    "tags": ["tag","tag2"]
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

`POST http://example.com/wp-json/funnelkit-automations/tag/add`

Parameter | Type  | Description | Mandatory
--------- |-------| ----------- | -----------
tags | array | an array of JSON objects, respectively, that includes the tag name - <code>{"tags": ["tag","tag2", ...]}</code> | YES


> JSON response example:

```json
{
  "code": "success",
  "data": {
    "tags": [
      {
        "ID": 30,
        "name": "bulkgate",
        "type": "1",
        "created_at": "2022-08-10 11:15:23",
        "updated_at": null,
        "data": null
      }
    ],
    "limit": 0,
    "offset": 0
  }
}
```

## Update A Tag

Updates a particular tag.

```shell
Update A Tag
POST http://example.com/wp-json/funnelkit-automations/tag/update/{tag_id}

    curl --location --request POST 'http://example.com/wp-json/funnelkit-automations/tag/update/{tag_id}' \
    --header 'api_key: {api-key}' \
    --header 'Content-Type: application/json' \
    --data-raw '{
        "tag": "tag_name"
    }'

```

```php
<?php
$site_url = 'http://example.com';
$endpoint = '/wp-json/funnelkit-automations/tag/update/{tag_id}';
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
    "tag": "tag_name"
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

`POST http://example.com/wp-json/funnelkit-automations/tag/update/{tag_id}`

Parameter | Type   | Description | Mandatory
--------- |--------| ----------- | -----------
tag | string | a JSON object, respectively, that includes the tag name - <code>{"tag": "tag_name"}</code> | YES


> JSON response example:

```json
{
  "code": "success",
  "data": {
    "tags": {
      "ID": "30",
      "name": "Bulkgate2"
    },
    "limit": 0,
    "offset": 0
  }
}
```

## Delete A Tag

Deletes a tag permanently.

```shell
Delete A Tag
DELETE http://example.com/wp-json/funnelkit-automations/tag/{tag_id}

    curl --location --request DELETE 'http://example.com/wp-json/funnelkit-automations/tag/{tag_id}' \
    --header 'api_key: {api-key}' \
    --header 'Content-Type: application/json' \
```

```php
<?php
$site_url = 'http://example.com';
$endpoint = '/wp-json/funnelkit-automations/tag/{tag_id}';
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
`DELETE http://example.com/wp-json/funnelkit-automations/tag/{tag_id}`

Parameter | Type | Description | Mandatory
--------- |------| ----------- | -----------


> JSON response example:

```json
{
  "code": "success",
  "data": {
    "tags": {
      "ID": "30",
      "name": "bulkgate"
    },
    "limit": 0,
    "offset": 0
  }
}
```
