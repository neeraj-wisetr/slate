---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - php

toc_footers:
  - <a href='https://github.com/neeraj-wisetr/slate'>Documentation Powered by Autonami</a>

includes:
  - tags/tags
  - lists/lists
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Autonami Public API
---

# Introduction

Welcome to the Autonami Public API! You can use our API to access Autonami Public API endpoints, which can manage autonami data in our database.

We have language bindings in Shell, Ruby, Python, PHP and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

> Example of how to use api key with endpoint:

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
  CURLOPT_POSTFIELDS =>'',
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;
?>
```

> Make sure to replace `your_api_key` with your API key.

Autonami Public API uses API keys to allow access to the API. New keys can be generated either through the WordPress admin interface or they can be auto-generated through an endpoint.

Autonami Public API expects for the API key to be included in all API requests to the server in a query string that looks like the following:

Parameter | Description
--------- | -----------
bwfan_public_api_key | your_api_key 

<aside class="notice">
You must replace <code>your_api_key</code> with your personal API key.
</aside>


