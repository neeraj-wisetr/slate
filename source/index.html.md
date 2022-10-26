---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - php

toc_footers:
  - Documentation Powered by Autonami

includes:
  - tags/tags
  - lists/lists
  - fields/fields
  - contacts/contacts
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Autonami Public API
---

# Introduction

Welcome to Autonami Public API! Our APIs are perfected to enable all organizations (of any size) to create powerful integrations that are easy to use and customize. You can use our API to access Autonami Public API endpoints, which manage the information in our database.
To further assist you, we have provided code samples on the bottom right section of this page. You can switch the programming language of these examples with the tabs given in the top right.

# Authentication

> Example of how to use api key with endpoint:

```php
<?php
$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/tags';
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
  CURLOPT_POSTFIELDS =>'',
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;
?>
```

> Make sure to replace `your_api_key` with your API key.

Autonami Public API uses API keys to allow access to it. New API keys can either be generated through the admin interface or auto-generated through an endpoint.
Autonami Public API expects the API key to be included in all API requests to the server in a query string that looks like the following:

Parameter | Type | Description | Mandatory
--------- | ----------- | ----------- | -----------
api_key | String | your_api_key | YES

<aside class="notice">
You must replace <code>your_api_key</code> with your personal API key.
</aside>

> JSON response example:

```json
{
  "code": "success",
  "data": {
    "tags": [
      {
        "ID": 1,
        "name": "tag1"
      },
      {
        "ID": 2,
        "name": "tag2"
      },
      {
        "ID": 3,
        "name": "tag3"
      }
    ],
    "limit": 0,
    "offset": 0
  }
}
```

