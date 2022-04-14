# Tags

The tags API allows you to create, view, update, and delete individual, or a batch, of tags.

Parameter | Type   | Description | Mandatory
--------- |--------| ----------- | -----------
bwfan_public_api_key | string | Api key for authorization | YES

## Get All Tags

This endpoint retrieves all tags.

```php
<?php
$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/tags';
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

`GET http://example.com/wp-json/autonami/tags`

Parameter | Type   | Description | Mandatory
--------- |--------| ----------- | -----------
page | integer | Current page of the collection | NO.


> JSON response example:

```json
{
  "code": 200,
  "message": "Tag(s) Listed successfully",
  "result": [
    {
      "ID": 2,
      "name": "nks2"
    },
    {
      "ID": 1,
      "name": "nks"
    }
  ],
  "limit": 30,
  "offset": 0
}
```

## Add Tags

This endpoint add the tags.

```php
<?php
$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/tag/add';
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

`POST http://example.com/wp-json/autonami/tag/add`

Parameter | Type  | Description | Mandatory
--------- |-------| ----------- | -----------
tags | array | an array of JSON objects, respectively, that includes the tag name - <code>{"tags": ["tag","tag2", ...]}</code> | YES


> JSON response example:

```json
{
  "code": 200,
  "message": "Tag(s) created successfully",
  "result": [
    {
      "ID": 3,
      "name": "tag",
      "type": "1",
      "created_at": "2022-04-13 12:22:06",
      "updated_at": null,
      "data": null
    },
    {
      "ID": 4,
      "name": "tag2",
      "type": "1",
      "created_at": "2022-04-13 12:22:06",
      "updated_at": null,
      "data": null
    }
  ],
  "limit": 30,
  "offset": 0
}
```

## Update A Tag

This endpoint update the tag.

```php
<?php
$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/tag/update/{tag_id}';
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

`POST http://example.com/wp-json/autonami/tag/update/{tag_id}`

Parameter | Type   | Description | Mandatory
--------- |--------| ----------- | -----------
tag | string | a JSON object, respectively, that includes the tag name - <code>{"tag": "tag_name"}</code> | YES


> JSON response example:

```json
{
  "code": 200,
  "message": "Tag updated successfully",
  "result": [],
  "limit": 30,
  "offset": 0
}
```

## Delete A Tag

This endpoint delete the tag.

```php
<?php
$site_url = 'http://example.com';
$endpoint = '/wp-json/tag/delete/{tag_id}';
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

`DELETE http://example.com/wp-json/autonami/tag/delete/{tag_id}`

Parameter | Type | Description | Mandatory
--------- |------| ----------- | -----------


> JSON response example:

```json
{
  "code": 200,
  "message": "Tag deleted successfully",
  "result": [],
  "limit": 30,
  "offset": 0
}
```
