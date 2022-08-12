# Contacts

The contacts API allows you to create, view, update, and delete individual, or a batch of contacts.

Parameter | Type   | Description | Mandatory
--------- |--------| ----------- | ----------- 
api_key | string | Api key for authorization | YES

## Get All Contacts

This endpoint retrieves all contacts.

```php
<?php
$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/contacts';
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

`GET http://example.com/wp-json/autonami/contacts`

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
          "id": "56",
          "wpid": "0",
          "uid": "8264f563ca27ab672b9665a8da42a500",
          "email": "rohit@wisetr.com",
          "f_name": "Ronit",
          "l_name": "Roy",
          "contact_no": "1234567890",
          "country": "AU",
          "state": "Delhi",
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
          "id": "51",
          "wpid": "12",
          "uid": "d7b6762adbcf73f382b12a37b3cdf5e9",
          "email": "ajay@wisetr.com",
          "f_name": "Daman",
          "l_name": "Jeet",
          "contact_no": "+1234567890",
          "country": "IN",
          "state": "Delhi",
          "timezone": "Asia/Kolkata",
          "type": "customer",
          "source": "wc_order",
          "points": "0",
          "tags": "[\"16\",\"19\",\"20\"]",
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

## Get Contact by ID

This endpoint retrieves contact detail of specified id or email

```php
<?php
$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/contact';
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

`GET http://example.com/wp-json/autonami/contact`

Parameter | Type | Description          | Mandatory
--------- |------|----------------------| -----------
id  | integer | Id of the contact | NO
email | string | Email of the contact | NO

> JSON response example:

```json
{
  "code": "success",
  "data": {
    "contact": {
      "contact": {
        "db_operations": {
          "wp_db": {
            "show_errors": false,
            "suppress_errors": false,
            "last_error": "",
            "num_queries": 241,
            "num_rows": 0,
            "rows_affected": 0,
            "insert_id": 135166,
            "last_query": "",
            "last_result": [],
            "queries": null,
            "prefix": "wp_",
            "base_prefix": "wp_",
            "ready": true,
            "blogid": 0,
            "siteid": 0,
            "tables": [
              "posts",
              "comments",
              "links"
            ],
            "old_tables": [
              "categories",
              "post2cat",
              "link2cat"
            ],
            "global_tables": [
              "users",
              "usermeta"
            ],
            "ms_global_tables": [
              "blogs",
              "blogmeta",
              "signups",
            ],
            "comments": "wp_comments",
            "commentmeta": "wp_commentmeta",
            "links": "wp_links",
            "options": "wp_options",
            "postmeta": "wp_postmeta",
            "posts": "wp_posts",
            "terms": "wp_terms",
            "term_relationships": "wp_term_relationships",
            "term_taxonomy": "wp_term_taxonomy",
            "termmeta": "wp_termmeta",
            "usermeta": "wp_usermeta",
            "users": "wp_users",
            "blogs": null,
            "blogmeta": null,
            "registration_log": null,
            "signups": null,
            "site": null,
            "sitecategories": null,
            "sitemeta": null,
            "field_types": {
              "post_author": "%d",
              "post_parent": "%d",
              "menu_order": "%d",
              "term_id": "%d",
              "term_group": "%d",
              "term_taxonomy_id": "%d",
              "parent": "%d",
              "count": "%d",
              "object_id": "%d",
              "term_order": "%d",
              "ID": "%d",
              "comment_ID": "%d",
              "comment_post_ID": "%d",
              "comment_parent": "%d",
              "user_id": "%d",
              "link_id": "%d",
              "link_owner": "%d",
              "link_rating": "%d",
              "option_id": "%d",
              "blog_id": "%d",
              "meta_id": "%d",
              "post_id": "%d",
              "user_status": "%d",
              "umeta_id": "%d",
              "comment_karma": "%d",
              "comment_count": "%d",
              "active": "%d",
              "cat_id": "%d",
              "deleted": "%d",
              "lang_id": "%d",
              "mature": "%d",
              "public": "%d",
              "site_id": "%d",
              "spam": "%d"
            },
            "charset": "utf8mb4",
            "collate": "utf8mb4_unicode_520_ci",
            "func_call": "$db->query(\"UPDATE `wp_bwfan_api_keys` SET `last_access` = '2022-08-10 17:29:57' WHERE `id` = '1'\")",
            "is_mysql": true,
            "time_start": null,
            "error": null,
            "categories": "wp_categories",
            "post2cat": "wp_post2cat",
            "link2cat": "wp_link2cat",
            "snippets": "wp_snippets",
            "ms_snippets": "wp_ms_snippets",
            "pmpro_membership_levels": "wp_pmpro_membership_levels",
            "pmpro_memberships_users": "wp_pmpro_memberships_users",
            "pmpro_memberships_categories": "wp_pmpro_memberships_categories",
            "pmpro_memberships_pages": "wp_pmpro_memberships_pages",
            "pmpro_membership_orders": "wp_pmpro_membership_orders",
            "pmpro_discount_codes": "wp_pmpro_discount_codes",
            "pmpro_discount_codes_levels": "wp_pmpro_discount_codes_levels",
            "pmpro_discount_codes_uses": "wp_pmpro_discount_codes_uses",
            "pmpro_membership_levelmeta": "wp_pmpro_membership_levelmeta",
            "pmpro_membership_ordermeta": "wp_pmpro_membership_ordermeta",
            "payment_tokenmeta": "wp_woocommerce_payment_tokenmeta",
            "order_itemmeta": "wp_woocommerce_order_itemmeta",
            "wc_product_meta_lookup": "wp_wc_product_meta_lookup",
            "wc_tax_rate_classes": "wp_wc_tax_rate_classes",
            "wc_reserved_stock": "wp_wc_reserved_stock",
            "bwfan_abandonedcarts": "wp_bwfan_abandonedcarts",
            "bwfan_automations": "wp_bwfan_automations",
            "bwfan_automationmeta": "wp_bwfan_automationmeta",
            "bwfan_tasks": "wp_bwfan_tasks",
            "bwfan_taskmeta": "wp_bwfan_taskmeta",
            "bwfan_task_claim": "wp_bwfan_task_claim",
            "bwfan_logs": "wp_bwfan_logs",
            "bwfan_logmeta": "wp_bwfan_logmeta",
            "bwfan_message_unsubscribe": "wp_bwfan_message_unsubscribe",
            "bwfan_contact_automations": "wp_bwfan_contact_automations",
            "bwfan_automation_contact": "wp_bwfan_automation_contact",
            "bwfan_automation_contact_claim": "wp_bwfan_automation_contact_claim",
            "bwfan_automation_contact_trail": "wp_bwfan_automation_contact_trail",
            "bwfan_automation_complete_contact": "wp_bwfan_automation_complete_contact",
            "bwfan_automation_step": "wp_bwfan_automation_step",
            "bwfan_broadcast": "wp_bwfan_broadcast",
            "bwfan_bulk_action": "wp_bwfan_bulk_action",
            "bwfan_contact_note": "wp_bwfan_contact_note",
            "bwfan_conversions": "wp_bwfan_conversions",
            "bwfan_engagement_tracking": "wp_bwfan_engagement_tracking",
            "bwfan_engagement_trackingmeta": "wp_bwfan_engagement_trackingmeta",
            "bwfan_fields": "wp_bwfan_fields",
            "bwfan_field_groups": "wp_bwfan_field_groups",
            "bwfan_form_feeds": "wp_bwfan_form_feeds",
            "bwfan_import_export": "wp_bwfan_import_export",
            "bwfan_link_triggers": "wp_bwfan_link_triggers",
            "bwfan_message": "wp_bwfan_message",
            "bwfan_templates": "wp_bwfan_templates",
            "bwfan_terms": "wp_bwfan_terms",
            "bwf_contact_fields": "wp_bwf_contact_fields",
            "bwf_contact_lms_fields": "wp_bwf_contact_lms_fields",
            "bwf_contact_wlm_fields": "wp_bwf_contact_wlm_fields",
            "wfacp_stats": "wp_wfacp_stats",
            "affiliatemeta": "wp_affiliate_wp_affiliatemeta",
            "referralmeta": "wp_affiliate_wp_referralmeta",
            "affwp_customermeta": "wp_affiliate_wp_customermeta",
            "actionscheduler_actions": "wp_actionscheduler_actions",
            "actionscheduler_claims": "wp_actionscheduler_claims",
            "actionscheduler_groups": "wp_actionscheduler_groups",
            "actionscheduler_logs": "wp_actionscheduler_logs",
            "wc_category_lookup": "wp_wc_category_lookup"
          },
          "contact_tbl": "wp_bwf_contact",
          "customer_tbl": "wp_bwf_wc_customers",
          "contact_meta_tbl": "wp_bwf_contact_meta"
        },
        "id": "9",
        "uid": null,
        "email": "abc@gmail.com",
        "wp_id": "3",
        "meta": {},
        "children": {},
        "db_contact": {
          "id": "9",
          "wpid": "3",
          "uid": "9f20c97f3dcba190c31c7f811f11c730",
          "email": "abc@gmail.com",
          "f_name": "Rahul",
          "l_name": "Kumar",
          "contact_no": "1234567890",
          "country": "IN",
          "state": "Delhi",
          "timezone": "Asia/Kolkata",
          "type": "customer",
          "source": "wc_order",
          "points": "0",
          "tags": "[\"16\",\"24\",\"1\"]",
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
        "1": "Vasant Vihar",
        "2": "New Delhi",
        "3": "Delhi",
        "4": "110057",
        "5": "abc",
        "6": "Male",
        "7": "2022-06-27",
        "8": "2022-07-12",
        "9": "2022-08-03",
        "10": "2022-08-03",
        "11": null,
        "12": "[4,6,14]",
        "13": null,
        "14": null,
        "15": "2022-08-10",
        "16": "{\"0\":\"47\",\"1\":\"52\",\"2\":\"53\",\"3\":\"54\",\"4\":\"55\",\"5\":\"56\",\"6\":\"57\",\"7\":\"58\",\"8\":\"59\",\"9\":\"60\",\"10\":\"61\",\"11\":\"65\",\"12\":\"67\",\"13\":\"71\",\"14\":\"73\",\"15\":\"74\",\"16\":\"75\",\"17\":\"78\",\"18\":\"79\",\"19\":\"82\",\"20\":\"84\",\"21\":\"88\",\"22\":\"90\",\"23\":\"91\",\"24\":\"95\",\"25\":\"98\",\"26\":\"99\",\"27\":\"100\",\"28\":\"101\",\"29\":\"104\",\"30\":\"106\",\"31\":\"107\",\"32\":\"112\",\"33\":\"113\",\"34\":\"115\",\"35\":\"122\",\"36\":\"123\",\"37\":\"143\",\"38\":\"144\",\"39\":\"146\",\"40\":\"147\",\"41\":\"148\",\"42\":\"153\",\"43\":\"157\",\"44\":\"158\",\"45\":\"159\",\"46\":\"179\",\"47\":\"180\",\"48\":\"181\",\"49\":\"182\",\"50\":\"184\",\"51\":\"185\",\"52\":\"216\",\"53\":\"217\",\"54\":\"218\",\"55\":\"219\",\"56\":\"232\",\"57\":\"233\",\"58\":\"237\",\"59\":\"239\",\"60\":\"241\",\"61\":\"243\",\"62\":\"244\",\"63\":\"246\",\"64\":\"262\",\"65\":\"263\",\"66\":\"267\",\"67\":\"269\",\"68\":\"270\",\"69\":\"272\",\"70\":\"274\",\"71\":\"278\",\"73\":\"282\",\"74\":\"283\",\"75\":\"292\"}",
        "17": "[\"53\",\"99\",\"144\",\"184\",\"185\",\"233\",\"239\",\"241\",\"243\",\"244\",\"246\",\"269\",\"274\",\"278\"]",
        "18": "[\"47\",\"52\",\"53\",\"54\",\"55\",\"56\",\"57\",\"58\",\"59\",\"60\",\"61\",\"65\",\"67\",\"71\",\"72\",\"73\",\"74\",\"75\",\"78\",\"79\",\"82\",\"84\",\"88\",\"90\",\"91\",\"95\",\"98\",\"100\",\"101\",\"104\",\"106\",\"107\",\"112\",\"113\",\"115\",\"122\",\"123\",\"143\",\"144\",\"146\",\"147\",\"148\",\"153\",\"157\",\"158\",\"159\",\"179\",\"180\",\"181\",\"182\",\"184\",\"185\",\"216\",\"217\",\"218\",\"219\",\"232\",\"237\",\"262\",\"263\",\"267\",\"269\",\"270\",\"272\",\"274\",\"278\",\"282\",\"283\",\"292\"]",
        "20": "nks_active_email",
        "24": "om campaign",
        "25": "om campaign id",
        "26": "[\"True\"]",
        "28": "Two times a month",
        "36": ""
      },
      "already_exists": true,
      "task_localized": [],
      "was_unsubscribed": false,
      "unsubscribe_date": null,
      "assigned_tags": [],
      "assigned_lists": [],
      "removed_tags": [],
      "removed_lists": []
    },
    "limit": 0,
    "offset": 0
  }
}
```

## Add Contact

This endpoint add a contact

```php
<?php

$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/contact/add';
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
  "code": "success",
  "data": {
    "contact": {
      "contact": {
        "db_operations": {
          "wp_db": {
            "show_errors": false,
            "suppress_errors": false,
            "last_error": "",
            "num_queries": 226,
            "num_rows": 0,
            "rows_affected": 0,
            "insert_id": 54,
            "last_query": "",
            "last_result": [],
            "queries": null,
            "prefix": "wp_",
            "base_prefix": "wp_",
            "ready": true,
            "blogid": 0,
            "siteid": 0,
            "tables": [
              "posts",
              "comments",
              "links",
              "options",
            ],
            "old_tables": [
              "categories",
              "post2cat",
              "link2cat"
            ],
            "global_tables": [
              "users",
              "usermeta"
            ],
            "ms_global_tables": [
              "blogs",
              "blogmeta",
              "signups",
            ],
            "comments": "wp_comments",
            "commentmeta": "wp_commentmeta",
            "links": "wp_links",
            "options": "wp_options",
            "postmeta": "wp_postmeta",
            "posts": "wp_posts",
            "terms": "wp_terms",
            "term_relationships": "wp_term_relationships",
            "term_taxonomy": "wp_term_taxonomy",
            "termmeta": "wp_termmeta",
            "usermeta": "wp_usermeta",
            "users": "wp_users",
            "blogs": null,
            "blogmeta": null,
            "registration_log": null,
            "signups": null,
            "site": null,
            "sitecategories": null,
            "sitemeta": null,
            "field_types": {
              "post_author": "%d",
              "post_parent": "%d",
              "menu_order": "%d",
              "term_id": "%d",
              "term_group": "%d",
              "term_taxonomy_id": "%d",
              "parent": "%d",
              "count": "%d",
              "object_id": "%d",
              "term_order": "%d",
              "ID": "%d",
              "comment_ID": "%d",
              "comment_post_ID": "%d",
              "comment_parent": "%d",
              "user_id": "%d",
              "link_id": "%d",
              "link_owner": "%d",
              "link_rating": "%d",
              "option_id": "%d",
              "blog_id": "%d",
              "meta_id": "%d",
              "post_id": "%d",
              "user_status": "%d",
              "umeta_id": "%d",
              "comment_karma": "%d",
              "comment_count": "%d",
              "active": "%d",
              "cat_id": "%d",
              "deleted": "%d",
              "lang_id": "%d",
              "mature": "%d",
              "public": "%d",
              "site_id": "%d",
              "spam": "%d"
            },
            "charset": "utf8mb4",
            "collate": "utf8mb4_unicode_520_ci",
            "func_call": "$db->query(\"UPDATE `wp_bwfan_api_keys` SET `last_access` = '2022-08-10 17:43:54' WHERE `id` = '1'\")",
            "is_mysql": true,
            "time_start": null,
            "error": null,
            "categories": "wp_categories",
            "post2cat": "wp_post2cat",
            "link2cat": "wp_link2cat",
            "snippets": "wp_snippets",
            "ms_snippets": "wp_ms_snippets",
            "pmpro_membership_levels": "wp_pmpro_membership_levels",
            "pmpro_memberships_users": "wp_pmpro_memberships_users",
            "pmpro_memberships_categories": "wp_pmpro_memberships_categories",
            "pmpro_memberships_pages": "wp_pmpro_memberships_pages",
            "pmpro_membership_orders": "wp_pmpro_membership_orders",
            "pmpro_discount_codes": "wp_pmpro_discount_codes",
            "pmpro_discount_codes_levels": "wp_pmpro_discount_codes_levels",
            "pmpro_discount_codes_uses": "wp_pmpro_discount_codes_uses",
            "pmpro_membership_levelmeta": "wp_pmpro_membership_levelmeta",
            "pmpro_membership_ordermeta": "wp_pmpro_membership_ordermeta",
            "payment_tokenmeta": "wp_woocommerce_payment_tokenmeta",
            "order_itemmeta": "wp_woocommerce_order_itemmeta",
            "wc_product_meta_lookup": "wp_wc_product_meta_lookup",
            "wc_tax_rate_classes": "wp_wc_tax_rate_classes",
            "wc_reserved_stock": "wp_wc_reserved_stock",
            "bwfan_abandonedcarts": "wp_bwfan_abandonedcarts",
            "bwfan_automations": "wp_bwfan_automations",
            "bwfan_automationmeta": "wp_bwfan_automationmeta",
            "bwfan_tasks": "wp_bwfan_tasks",
            "bwfan_taskmeta": "wp_bwfan_taskmeta",
            "bwfan_task_claim": "wp_bwfan_task_claim",
            "bwfan_logs": "wp_bwfan_logs",
            "bwfan_logmeta": "wp_bwfan_logmeta",
            "bwfan_message_unsubscribe": "wp_bwfan_message_unsubscribe",
            "bwfan_contact_automations": "wp_bwfan_contact_automations",
            "bwfan_automation_contact": "wp_bwfan_automation_contact",
            "bwfan_automation_contact_claim": "wp_bwfan_automation_contact_claim",
            "bwfan_automation_contact_trail": "wp_bwfan_automation_contact_trail",
            "bwfan_automation_complete_contact": "wp_bwfan_automation_complete_contact",
            "bwfan_automation_step": "wp_bwfan_automation_step",
            "bwfan_broadcast": "wp_bwfan_broadcast",
            "bwfan_bulk_action": "wp_bwfan_bulk_action",
            "bwfan_contact_note": "wp_bwfan_contact_note",
            "bwfan_conversions": "wp_bwfan_conversions",
            "bwfan_engagement_tracking": "wp_bwfan_engagement_tracking",
            "bwfan_engagement_trackingmeta": "wp_bwfan_engagement_trackingmeta",
            "bwfan_fields": "wp_bwfan_fields",
            "bwfan_field_groups": "wp_bwfan_field_groups",
            "bwfan_form_feeds": "wp_bwfan_form_feeds",
            "bwfan_import_export": "wp_bwfan_import_export",
            "bwfan_link_triggers": "wp_bwfan_link_triggers",
            "bwfan_message": "wp_bwfan_message",
            "bwfan_templates": "wp_bwfan_templates",
            "bwfan_terms": "wp_bwfan_terms",
            "bwf_contact_fields": "wp_bwf_contact_fields",
            "bwf_contact_lms_fields": "wp_bwf_contact_lms_fields",
            "bwf_contact_wlm_fields": "wp_bwf_contact_wlm_fields",
            "wfacp_stats": "wp_wfacp_stats",
            "affiliatemeta": "wp_affiliate_wp_affiliatemeta",
            "referralmeta": "wp_affiliate_wp_referralmeta",
            "affwp_customermeta": "wp_affiliate_wp_customermeta",
            "actionscheduler_actions": "wp_actionscheduler_actions",
            "actionscheduler_claims": "wp_actionscheduler_claims",
            "actionscheduler_groups": "wp_actionscheduler_groups",
            "actionscheduler_logs": "wp_actionscheduler_logs",
            "wc_category_lookup": "wp_wc_category_lookup"
          },
          "contact_tbl": "wp_bwf_contact",
          "customer_tbl": "wp_bwf_wc_customers",
          "contact_meta_tbl": "wp_bwf_contact_meta"
        },
        "id": 57,
        "uid": "f1b1bbeb5258c9ec4896c025118b23da",
        "email": "abc@gmail.com",
        "wp_id": 0,
        "meta": {},
        "children": {},
        "db_contact": null,
        "blank_values_update": false,
        "is_subscribed": false,
        "f_name": "Ronit",
        "l_name": "Roy",
        "state": "Delhi",
        "country": "AU",
        "contact_no": "1234567890",
        "status": 0,
        "source": "public_api",
        "type": "lead"
      },
      "customer": null,
      "fields": {
        "6": "Male"
      },
      "already_exists": false,
      "task_localized": [],
      "was_unsubscribed": false,
      "unsubscribe_date": null,
      "assigned_tags": [],
      "assigned_lists": [],
      "removed_tags": [],
      "removed_lists": []
    },
    "limit": 0,
    "offset": 0
  }
}
```

## Update a Contact

This endpoint update a contact

```php
<?php

$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/contact/update/{contact_id}';
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
  "code": "success",
  "data": {
    "contact": {
      "contact": {
        "db_operations": {
          "wp_db": {
            "show_errors": false,
            "suppress_errors": false,
            "last_error": "",
            "num_queries": 251,
            "num_rows": 0,
            "rows_affected": 0,
            "insert_id": 135176,
            "last_query": "",
            "last_result": [],
            "queries": null,
            "prefix": "wp_",
            "base_prefix": "wp_",
            "ready": true,
            "blogid": 0,
            "siteid": 0,
            "tables": [
              "posts",
              "comments",
              "links",
            ],
            "old_tables": [
              "categories",
              "post2cat",
              "link2cat"
            ],
            "global_tables": [
              "users",
              "usermeta"
            ],
            "ms_global_tables": [
              "blogs",
              "blogmeta",
              "signups"
            ],
            "comments": "wp_comments",
            "commentmeta": "wp_commentmeta",
            "links": "wp_links",
            "options": "wp_options",
            "postmeta": "wp_postmeta",
            "posts": "wp_posts",
            "terms": "wp_terms",
            "term_relationships": "wp_term_relationships",
            "term_taxonomy": "wp_term_taxonomy",
            "termmeta": "wp_termmeta",
            "usermeta": "wp_usermeta",
            "users": "wp_users",
            "blogs": null,
            "blogmeta": null,
            "registration_log": null,
            "signups": null,
            "site": null,
            "sitecategories": null,
            "sitemeta": null,
            "field_types": {
              "post_author": "%d",
              "post_parent": "%d",
              "menu_order": "%d",
              "term_id": "%d",
              "term_group": "%d",
              "term_taxonomy_id": "%d",
              "parent": "%d",
              "count": "%d",
              "object_id": "%d",
              "term_order": "%d",
              "ID": "%d",
              "comment_ID": "%d",
              "comment_post_ID": "%d",
              "comment_parent": "%d",
              "user_id": "%d",
              "link_id": "%d",
              "link_owner": "%d",
              "link_rating": "%d",
              "option_id": "%d",
              "blog_id": "%d",
              "meta_id": "%d",
              "post_id": "%d",
              "user_status": "%d",
              "umeta_id": "%d",
              "comment_karma": "%d",
              "comment_count": "%d",
              "active": "%d",
              "cat_id": "%d",
              "deleted": "%d",
              "lang_id": "%d",
              "mature": "%d",
              "public": "%d",
              "site_id": "%d",
              "spam": "%d"
            },
            "charset": "utf8mb4",
            "collate": "utf8mb4_unicode_520_ci",
            "func_call": "",
            "is_mysql": true,
            "time_start": null,
            "error": null,
            "categories": "wp_categories",
            "post2cat": "wp_post2cat",
            "link2cat": "wp_link2cat",
            "snippets": "wp_snippets",
            "ms_snippets": "wp_ms_snippets",
            "pmpro_membership_levels": "wp_pmpro_membership_levels",
            "pmpro_memberships_users": "wp_pmpro_memberships_users",
            "pmpro_memberships_categories": "wp_pmpro_memberships_categories",
            "pmpro_memberships_pages": "wp_pmpro_memberships_pages",
            "pmpro_membership_orders": "wp_pmpro_membership_orders",
            "pmpro_discount_codes": "wp_pmpro_discount_codes",
            "pmpro_discount_codes_levels": "wp_pmpro_discount_codes_levels",
            "pmpro_discount_codes_uses": "wp_pmpro_discount_codes_uses",
            "pmpro_membership_levelmeta": "wp_pmpro_membership_levelmeta",
            "pmpro_membership_ordermeta": "wp_pmpro_membership_ordermeta",
            "payment_tokenmeta": "wp_woocommerce_payment_tokenmeta",
            "order_itemmeta": "wp_woocommerce_order_itemmeta",
            "wc_product_meta_lookup": "wp_wc_product_meta_lookup",
            "wc_tax_rate_classes": "wp_wc_tax_rate_classes",
            "wc_reserved_stock": "wp_wc_reserved_stock",
            "bwfan_abandonedcarts": "wp_bwfan_abandonedcarts",
            "bwfan_automations": "wp_bwfan_automations",
            "bwfan_automationmeta": "wp_bwfan_automationmeta",
            "bwfan_tasks": "wp_bwfan_tasks",
            "bwfan_taskmeta": "wp_bwfan_taskmeta",
            "bwfan_task_claim": "wp_bwfan_task_claim",
            "bwfan_logs": "wp_bwfan_logs",
            "bwfan_logmeta": "wp_bwfan_logmeta",
            "bwfan_message_unsubscribe": "wp_bwfan_message_unsubscribe",
            "bwfan_contact_automations": "wp_bwfan_contact_automations",
            "bwfan_automation_contact": "wp_bwfan_automation_contact",
            "bwfan_automation_contact_claim": "wp_bwfan_automation_contact_claim",
            "bwfan_automation_contact_trail": "wp_bwfan_automation_contact_trail",
            "bwfan_automation_complete_contact": "wp_bwfan_automation_complete_contact",
            "bwfan_automation_step": "wp_bwfan_automation_step",
            "bwfan_broadcast": "wp_bwfan_broadcast",
            "bwfan_bulk_action": "wp_bwfan_bulk_action",
            "bwfan_contact_note": "wp_bwfan_contact_note",
            "bwfan_conversions": "wp_bwfan_conversions",
            "bwfan_engagement_tracking": "wp_bwfan_engagement_tracking",
            "bwfan_engagement_trackingmeta": "wp_bwfan_engagement_trackingmeta",
            "bwfan_fields": "wp_bwfan_fields",
            "bwfan_field_groups": "wp_bwfan_field_groups",
            "bwfan_form_feeds": "wp_bwfan_form_feeds",
            "bwfan_import_export": "wp_bwfan_import_export",
            "bwfan_link_triggers": "wp_bwfan_link_triggers",
            "bwfan_message": "wp_bwfan_message",
            "bwfan_templates": "wp_bwfan_templates",
            "bwfan_terms": "wp_bwfan_terms",
            "bwf_contact_fields": "wp_bwf_contact_fields",
            "bwf_contact_lms_fields": "wp_bwf_contact_lms_fields",
            "bwf_contact_wlm_fields": "wp_bwf_contact_wlm_fields",
            "wfacp_stats": "wp_wfacp_stats",
            "affiliatemeta": "wp_affiliate_wp_affiliatemeta",
            "referralmeta": "wp_affiliate_wp_referralmeta",
            "affwp_customermeta": "wp_affiliate_wp_customermeta",
            "actionscheduler_actions": "wp_actionscheduler_actions",
            "actionscheduler_claims": "wp_actionscheduler_claims",
            "actionscheduler_groups": "wp_actionscheduler_groups",
            "actionscheduler_logs": "wp_actionscheduler_logs",
            "wc_category_lookup": "wp_wc_category_lookup"
          },
          "contact_tbl": "wp_bwf_contact",
          "customer_tbl": "wp_bwf_wc_customers",
          "contact_meta_tbl": "wp_bwf_contact_meta"
        },
        "id": "9",
        "uid": null,
        "email": "abc@gmail.com",
        "wp_id": "3",
        "meta": {},
        "children": {},
        "db_contact": {
          "id": "9",
          "wpid": "3",
          "uid": "9f20c97f3dcba190c31c7f811f11c730",
          "email": "abc@gmail.com",
          "f_name": "Rahul",
          "l_name": "Kumar",
          "contact_no": "1234567890",
          "country": "IN",
          "state": "Delhi",
          "timezone": "Asia/Kolkata",
          "type": "customer",
          "source": "wc_order",
          "points": "0",
          "tags": "[\"16\",\"24\",\"1\"]",
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
        "1": "Vasant Vihar",
        "2": "New Delhi",
        "3": "Delhi",
        "4": "110057",
        "5": "abc",
        "6": "Male",
        "7": "2022-06-27",
        "8": "2022-07-12",
        "9": "2022-08-03",
        "10": "2022-08-03",
        "11": null,
        "12": "[4,6,14]",
        "13": null,
        "14": null,
        "15": "2022-08-10",
        "16": "{\"0\":\"47\",\"1\":\"52\",\"2\":\"53\",\"3\":\"54\",\"4\":\"55\",\"5\":\"56\",\"6\":\"57\",\"7\":\"58\",\"8\":\"59\",\"9\":\"60\",\"10\":\"61\",\"11\":\"65\",\"12\":\"67\",\"13\":\"71\",\"14\":\"73\",\"15\":\"74\",\"16\":\"75\",\"17\":\"78\",\"18\":\"79\",\"19\":\"82\",\"20\":\"84\",\"21\":\"88\",\"22\":\"90\",\"23\":\"91\",\"24\":\"95\",\"25\":\"98\",\"26\":\"99\",\"27\":\"100\",\"28\":\"101\",\"29\":\"104\",\"30\":\"106\",\"31\":\"107\",\"32\":\"112\",\"33\":\"113\",\"34\":\"115\",\"35\":\"122\",\"36\":\"123\",\"37\":\"143\",\"38\":\"144\",\"39\":\"146\",\"40\":\"147\",\"41\":\"148\",\"42\":\"153\",\"43\":\"157\",\"44\":\"158\",\"45\":\"159\",\"46\":\"179\",\"47\":\"180\",\"48\":\"181\",\"49\":\"182\",\"50\":\"184\",\"51\":\"185\",\"52\":\"216\",\"53\":\"217\",\"54\":\"218\",\"55\":\"219\",\"56\":\"232\",\"57\":\"233\",\"58\":\"237\",\"59\":\"239\",\"60\":\"241\",\"61\":\"243\",\"62\":\"244\",\"63\":\"246\",\"64\":\"262\",\"65\":\"263\",\"66\":\"267\",\"67\":\"269\",\"68\":\"270\",\"69\":\"272\",\"70\":\"274\",\"71\":\"278\",\"73\":\"282\",\"74\":\"283\",\"75\":\"292\"}",
        "17": "[\"53\",\"99\",\"144\",\"184\",\"185\",\"233\",\"239\",\"241\",\"243\",\"244\",\"246\",\"269\",\"274\",\"278\"]",
        "18": "[\"47\",\"52\",\"53\",\"54\",\"55\",\"56\",\"57\",\"58\",\"59\",\"60\",\"61\",\"65\",\"67\",\"71\",\"72\",\"73\",\"74\",\"75\",\"78\",\"79\",\"82\",\"84\",\"88\",\"90\",\"91\",\"95\",\"98\",\"100\",\"101\",\"104\",\"106\",\"107\",\"112\",\"113\",\"115\",\"122\",\"123\",\"143\",\"144\",\"146\",\"147\",\"148\",\"153\",\"157\",\"158\",\"159\",\"179\",\"180\",\"181\",\"182\",\"184\",\"185\",\"216\",\"217\",\"218\",\"219\",\"232\",\"237\",\"262\",\"263\",\"267\",\"269\",\"270\",\"272\",\"274\",\"278\",\"282\",\"283\",\"292\"]",
        "20": "nks_active_email",
        "24": "om campaign",
        "25": "om campaign id",
        "26": "[\"True\"]",
        "28": "Two times a month",
        "36": ""
      },
      "already_exists": true,
      "task_localized": [],
      "was_unsubscribed": false,
      "unsubscribe_date": null,
      "assigned_tags": [],
      "assigned_lists": [],
      "removed_tags": [],
      "removed_lists": []
    },
    "limit": 0,
    "offset": 0
  }
}
```

## Update Eamil

This endpoint update the email of the contact

```php
<?php

$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/contact/update-email/{contact_id}';
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
  "code": "success",
  "data": {
    "contact": {
      "contact": {
        "db_operations": {
          "wp_db": {
            "show_errors": false,
            "suppress_errors": false,
            "last_error": "",
            "num_queries": 248,
            "num_rows": 0,
            "rows_affected": 0,
            "insert_id": 135180,
            "last_query": "",
            "last_result": [],
            "queries": null,
            "prefix": "wp_",
            "base_prefix": "wp_",
            "ready": true,
            "blogid": 0,
            "siteid": 0,
            "tables": [
              "posts",
              "comments",
              "links",
              "options",
            ],
            "old_tables": [
              "categories",
              "post2cat",
              "link2cat"
            ],
            "global_tables": [
              "users",
              "usermeta"
            ],
            "ms_global_tables": [
              "blogs",
              "blogmeta",
              "signups"
            ],
            "comments": "wp_comments",
            "commentmeta": "wp_commentmeta",
            "links": "wp_links",
            "options": "wp_options",
            "postmeta": "wp_postmeta",
            "posts": "wp_posts",
            "terms": "wp_terms",
            "term_relationships": "wp_term_relationships",
            "term_taxonomy": "wp_term_taxonomy",
            "termmeta": "wp_termmeta",
            "usermeta": "wp_usermeta",
            "users": "wp_users",
            "blogs": null,
            "blogmeta": null,
            "registration_log": null,
            "signups": null,
            "site": null,
            "sitecategories": null,
            "sitemeta": null,
            "field_types": {
              "post_author": "%d",
              "post_parent": "%d",
              "menu_order": "%d",
              "term_id": "%d",
              "term_group": "%d",
              "term_taxonomy_id": "%d",
              "parent": "%d",
              "count": "%d",
              "object_id": "%d",
              "term_order": "%d",
              "ID": "%d",
              "comment_ID": "%d",
              "comment_post_ID": "%d",
              "comment_parent": "%d",
              "user_id": "%d",
              "link_id": "%d",
              "link_owner": "%d",
              "link_rating": "%d",
              "option_id": "%d",
              "blog_id": "%d",
              "meta_id": "%d",
              "post_id": "%d",
              "user_status": "%d",
              "umeta_id": "%d",
              "comment_karma": "%d",
              "comment_count": "%d",
              "active": "%d",
              "cat_id": "%d",
              "deleted": "%d",
              "lang_id": "%d",
              "mature": "%d",
              "public": "%d",
              "site_id": "%d",
              "spam": "%d"
            },
            "charset": "utf8mb4",
            "collate": "utf8mb4_unicode_520_ci",
            "func_call": "",
            "is_mysql": true,
            "time_start": null,
            "error": null,
            "categories": "wp_categories",
            "post2cat": "wp_post2cat",
            "link2cat": "wp_link2cat",
            "snippets": "wp_snippets",
            "ms_snippets": "wp_ms_snippets",
            "pmpro_membership_levels": "wp_pmpro_membership_levels",
            "pmpro_memberships_users": "wp_pmpro_memberships_users",
            "pmpro_memberships_categories": "wp_pmpro_memberships_categories",
            "pmpro_memberships_pages": "wp_pmpro_memberships_pages",
            "pmpro_membership_orders": "wp_pmpro_membership_orders",
            "pmpro_discount_codes": "wp_pmpro_discount_codes",
            "pmpro_discount_codes_levels": "wp_pmpro_discount_codes_levels",
            "pmpro_discount_codes_uses": "wp_pmpro_discount_codes_uses",
            "pmpro_membership_levelmeta": "wp_pmpro_membership_levelmeta",
            "pmpro_membership_ordermeta": "wp_pmpro_membership_ordermeta",
            "payment_tokenmeta": "wp_woocommerce_payment_tokenmeta",
            "order_itemmeta": "wp_woocommerce_order_itemmeta",
            "wc_product_meta_lookup": "wp_wc_product_meta_lookup",
            "wc_tax_rate_classes": "wp_wc_tax_rate_classes",
            "wc_reserved_stock": "wp_wc_reserved_stock",
            "bwfan_abandonedcarts": "wp_bwfan_abandonedcarts",
            "bwfan_automations": "wp_bwfan_automations",
            "bwfan_automationmeta": "wp_bwfan_automationmeta",
            "bwfan_tasks": "wp_bwfan_tasks",
            "bwfan_taskmeta": "wp_bwfan_taskmeta",
            "bwfan_task_claim": "wp_bwfan_task_claim",
            "bwfan_logs": "wp_bwfan_logs",
            "bwfan_logmeta": "wp_bwfan_logmeta",
            "bwfan_message_unsubscribe": "wp_bwfan_message_unsubscribe",
            "bwfan_contact_automations": "wp_bwfan_contact_automations",
            "bwfan_automation_contact": "wp_bwfan_automation_contact",
            "bwfan_automation_contact_claim": "wp_bwfan_automation_contact_claim",
            "bwfan_automation_contact_trail": "wp_bwfan_automation_contact_trail",
            "bwfan_automation_complete_contact": "wp_bwfan_automation_complete_contact",
            "bwfan_automation_step": "wp_bwfan_automation_step",
            "bwfan_broadcast": "wp_bwfan_broadcast",
            "bwfan_bulk_action": "wp_bwfan_bulk_action",
            "bwfan_contact_note": "wp_bwfan_contact_note",
            "bwfan_conversions": "wp_bwfan_conversions",
            "bwfan_engagement_tracking": "wp_bwfan_engagement_tracking",
            "bwfan_engagement_trackingmeta": "wp_bwfan_engagement_trackingmeta",
            "bwfan_fields": "wp_bwfan_fields",
            "bwfan_field_groups": "wp_bwfan_field_groups",
            "bwfan_form_feeds": "wp_bwfan_form_feeds",
            "bwfan_import_export": "wp_bwfan_import_export",
            "bwfan_link_triggers": "wp_bwfan_link_triggers",
            "bwfan_message": "wp_bwfan_message",
            "bwfan_templates": "wp_bwfan_templates",
            "bwfan_terms": "wp_bwfan_terms",
            "bwf_contact_fields": "wp_bwf_contact_fields",
            "bwf_contact_lms_fields": "wp_bwf_contact_lms_fields",
            "bwf_contact_wlm_fields": "wp_bwf_contact_wlm_fields",
            "wfacp_stats": "wp_wfacp_stats",
            "affiliatemeta": "wp_affiliate_wp_affiliatemeta",
            "referralmeta": "wp_affiliate_wp_referralmeta",
            "affwp_customermeta": "wp_affiliate_wp_customermeta",
            "actionscheduler_actions": "wp_actionscheduler_actions",
            "actionscheduler_claims": "wp_actionscheduler_claims",
            "actionscheduler_groups": "wp_actionscheduler_groups",
            "actionscheduler_logs": "wp_actionscheduler_logs",
            "wc_category_lookup": "wp_wc_category_lookup"
          },
          "contact_tbl": "wp_bwf_contact",
          "customer_tbl": "wp_bwf_wc_customers",
          "contact_meta_tbl": "wp_bwf_contact_meta"
        },
        "id": "9",
        "uid": null,
        "email": "abc@gmail.com",
        "wp_id": "3",
        "meta": {},
        "children": {},
        "db_contact": {
          "id": "9",
          "wpid": "3",
          "uid": "9f20c97f3dcba190c31c7f811f11c730",
          "email": "abc@gmail.com",
          "f_name": "Rahul",
          "l_name": "Kumar",
          "contact_no": "1234567890",
          "country": "IN",
          "state": "Delhi",
          "timezone": "Asia/Kolkata",
          "type": "customer",
          "source": "wc_order",
          "points": "0",
          "tags": "[\"16\",\"24\",\"1\"]",
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
        "1": "Vasant Vihar",
        "2": "New Delhi",
        "3": "Delhi",
        "4": "110057",
        "5": "abc",
        "6": "Male",
        "7": "2022-06-27",
        "8": "2022-07-12",
        "9": "2022-08-03",
        "10": "2022-08-03",
        "11": null,
        "12": "[4,6,14]",
        "13": null,
        "14": null,
        "15": "2022-08-10",
        "16": "{\"0\":\"47\",\"1\":\"52\",\"2\":\"53\",\"3\":\"54\",\"4\":\"55\",\"5\":\"56\",\"6\":\"57\",\"7\":\"58\",\"8\":\"59\",\"9\":\"60\",\"10\":\"61\",\"11\":\"65\",\"12\":\"67\",\"13\":\"71\",\"14\":\"73\",\"15\":\"74\",\"16\":\"75\",\"17\":\"78\",\"18\":\"79\",\"19\":\"82\",\"20\":\"84\",\"21\":\"88\",\"22\":\"90\",\"23\":\"91\",\"24\":\"95\",\"25\":\"98\",\"26\":\"99\",\"27\":\"100\",\"28\":\"101\",\"29\":\"104\",\"30\":\"106\",\"31\":\"107\",\"32\":\"112\",\"33\":\"113\",\"34\":\"115\",\"35\":\"122\",\"36\":\"123\",\"37\":\"143\",\"38\":\"144\",\"39\":\"146\",\"40\":\"147\",\"41\":\"148\",\"42\":\"153\",\"43\":\"157\",\"44\":\"158\",\"45\":\"159\",\"46\":\"179\",\"47\":\"180\",\"48\":\"181\",\"49\":\"182\",\"50\":\"184\",\"51\":\"185\",\"52\":\"216\",\"53\":\"217\",\"54\":\"218\",\"55\":\"219\",\"56\":\"232\",\"57\":\"233\",\"58\":\"237\",\"59\":\"239\",\"60\":\"241\",\"61\":\"243\",\"62\":\"244\",\"63\":\"246\",\"64\":\"262\",\"65\":\"263\",\"66\":\"267\",\"67\":\"269\",\"68\":\"270\",\"69\":\"272\",\"70\":\"274\",\"71\":\"278\",\"73\":\"282\",\"74\":\"283\",\"75\":\"292\"}",
        "17": "[\"53\",\"99\",\"144\",\"184\",\"185\",\"233\",\"239\",\"241\",\"243\",\"244\",\"246\",\"269\",\"274\",\"278\"]",
        "18": "[\"47\",\"52\",\"53\",\"54\",\"55\",\"56\",\"57\",\"58\",\"59\",\"60\",\"61\",\"65\",\"67\",\"71\",\"72\",\"73\",\"74\",\"75\",\"78\",\"79\",\"82\",\"84\",\"88\",\"90\",\"91\",\"95\",\"98\",\"100\",\"101\",\"104\",\"106\",\"107\",\"112\",\"113\",\"115\",\"122\",\"123\",\"143\",\"144\",\"146\",\"147\",\"148\",\"153\",\"157\",\"158\",\"159\",\"179\",\"180\",\"181\",\"182\",\"184\",\"185\",\"216\",\"217\",\"218\",\"219\",\"232\",\"237\",\"262\",\"263\",\"267\",\"269\",\"270\",\"272\",\"274\",\"278\",\"282\",\"283\",\"292\"]",
        "20": "nks_active_email",
        "24": "om campaign",
        "25": "om campaign id",
        "26": "[\"True\"]",
        "28": "Two times a month",
        "36": ""
      },
      "already_exists": true,
      "task_localized": [],
      "was_unsubscribed": false,
      "unsubscribe_date": null,
      "assigned_tags": [],
      "assigned_lists": [],
      "removed_tags": [],
      "removed_lists": []
    },
    "limit": 0,
    "offset": 0
  }
}
```

## Change Status

This endpoint change the status of the contact

```php
<?php

$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/contact/change-status/{contact_id}';
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

`POST http://example.com/wp-json/autonami/contact/change-status/{contact_id}`

Parameter | Type | Description                                                                           | Mandatory
----- |---------|---------------------------------------------------------------------------------------|--------- 
status | string | Status for the contact<code>unverified, </br>subscribed, bounced, unsubscribed</code> | YES

> JSON response example:

```json
{
  "code": "success",
  "data": {
    "contact": {
      "contact": {
        "db_operations": {
          "wp_db": {
            "show_errors": false,
            "suppress_errors": false,
            "last_error": "",
            "num_queries": 256,
            "num_rows": 0,
            "rows_affected": 0,
            "insert_id": 41,
            "last_query": "",
            "last_result": [],
            "queries": null,
            "prefix": "wp_",
            "base_prefix": "wp_",
            "ready": true,
            "blogid": 0,
            "siteid": 0,
            "tables": [
              "posts",
              "comments",
              "links",
            ],
            "old_tables": [
              "categories",
              "post2cat",
              "link2cat"
            ],
            "global_tables": [
              "users",
              "usermeta"
            ],
            "ms_global_tables": [
              "blogs",
              "blogmeta",
              "signups"
            ],
            "comments": "wp_comments",
            "commentmeta": "wp_commentmeta",
            "links": "wp_links",
            "options": "wp_options",
            "postmeta": "wp_postmeta",
            "posts": "wp_posts",
            "terms": "wp_terms",
            "term_relationships": "wp_term_relationships",
            "term_taxonomy": "wp_term_taxonomy",
            "termmeta": "wp_termmeta",
            "usermeta": "wp_usermeta",
            "users": "wp_users",
            "blogs": null,
            "blogmeta": null,
            "registration_log": null,
            "signups": null,
            "site": null,
            "sitecategories": null,
            "sitemeta": null,
            "field_types": {
              "post_author": "%d",
              "post_parent": "%d",
              "menu_order": "%d",
              "term_id": "%d",
              "term_group": "%d",
              "term_taxonomy_id": "%d",
              "parent": "%d",
              "count": "%d",
              "object_id": "%d",
              "term_order": "%d",
              "ID": "%d",
              "comment_ID": "%d",
              "comment_post_ID": "%d",
              "comment_parent": "%d",
              "user_id": "%d",
              "link_id": "%d",
              "link_owner": "%d",
              "link_rating": "%d",
              "option_id": "%d",
              "blog_id": "%d",
              "meta_id": "%d",
              "post_id": "%d",
              "user_status": "%d",
              "umeta_id": "%d",
              "comment_karma": "%d",
              "comment_count": "%d",
              "active": "%d",
              "cat_id": "%d",
              "deleted": "%d",
              "lang_id": "%d",
              "mature": "%d",
              "public": "%d",
              "site_id": "%d",
              "spam": "%d"
            },
            "charset": "utf8mb4",
            "collate": "utf8mb4_unicode_520_ci",
            "func_call": "",
            "is_mysql": true,
            "time_start": null,
            "error": null,
            "categories": "wp_categories",
            "post2cat": "wp_post2cat",
            "link2cat": "wp_link2cat",
            "snippets": "wp_snippets",
            "ms_snippets": "wp_ms_snippets",
            "pmpro_membership_levels": "wp_pmpro_membership_levels",
            "pmpro_memberships_users": "wp_pmpro_memberships_users",
            "pmpro_memberships_categories": "wp_pmpro_memberships_categories",
            "pmpro_memberships_pages": "wp_pmpro_memberships_pages",
            "pmpro_membership_orders": "wp_pmpro_membership_orders",
            "pmpro_discount_codes": "wp_pmpro_discount_codes",
            "pmpro_discount_codes_levels": "wp_pmpro_discount_codes_levels",
            "pmpro_discount_codes_uses": "wp_pmpro_discount_codes_uses",
            "pmpro_membership_levelmeta": "wp_pmpro_membership_levelmeta",
            "pmpro_membership_ordermeta": "wp_pmpro_membership_ordermeta",
            "payment_tokenmeta": "wp_woocommerce_payment_tokenmeta",
            "order_itemmeta": "wp_woocommerce_order_itemmeta",
            "wc_product_meta_lookup": "wp_wc_product_meta_lookup",
            "wc_tax_rate_classes": "wp_wc_tax_rate_classes",
            "wc_reserved_stock": "wp_wc_reserved_stock",
            "bwfan_abandonedcarts": "wp_bwfan_abandonedcarts",
            "bwfan_automations": "wp_bwfan_automations",
            "bwfan_automationmeta": "wp_bwfan_automationmeta",
            "bwfan_tasks": "wp_bwfan_tasks",
            "bwfan_taskmeta": "wp_bwfan_taskmeta",
            "bwfan_task_claim": "wp_bwfan_task_claim",
            "bwfan_logs": "wp_bwfan_logs",
            "bwfan_logmeta": "wp_bwfan_logmeta",
            "bwfan_message_unsubscribe": "wp_bwfan_message_unsubscribe",
            "bwfan_contact_automations": "wp_bwfan_contact_automations",
            "bwfan_automation_contact": "wp_bwfan_automation_contact",
            "bwfan_automation_contact_claim": "wp_bwfan_automation_contact_claim",
            "bwfan_automation_contact_trail": "wp_bwfan_automation_contact_trail",
            "bwfan_automation_complete_contact": "wp_bwfan_automation_complete_contact",
            "bwfan_automation_step": "wp_bwfan_automation_step",
            "bwfan_broadcast": "wp_bwfan_broadcast",
            "bwfan_bulk_action": "wp_bwfan_bulk_action",
            "bwfan_contact_note": "wp_bwfan_contact_note",
            "bwfan_conversions": "wp_bwfan_conversions",
            "bwfan_engagement_tracking": "wp_bwfan_engagement_tracking",
            "bwfan_engagement_trackingmeta": "wp_bwfan_engagement_trackingmeta",
            "bwfan_fields": "wp_bwfan_fields",
            "bwfan_field_groups": "wp_bwfan_field_groups",
            "bwfan_form_feeds": "wp_bwfan_form_feeds",
            "bwfan_import_export": "wp_bwfan_import_export",
            "bwfan_link_triggers": "wp_bwfan_link_triggers",
            "bwfan_message": "wp_bwfan_message",
            "bwfan_templates": "wp_bwfan_templates",
            "bwfan_terms": "wp_bwfan_terms",
            "bwf_contact_fields": "wp_bwf_contact_fields",
            "bwf_contact_lms_fields": "wp_bwf_contact_lms_fields",
            "bwf_contact_wlm_fields": "wp_bwf_contact_wlm_fields",
            "wfacp_stats": "wp_wfacp_stats",
            "affiliatemeta": "wp_affiliate_wp_affiliatemeta",
            "referralmeta": "wp_affiliate_wp_referralmeta",
            "affwp_customermeta": "wp_affiliate_wp_customermeta",
            "actionscheduler_actions": "wp_actionscheduler_actions",
            "actionscheduler_claims": "wp_actionscheduler_claims",
            "actionscheduler_groups": "wp_actionscheduler_groups",
            "actionscheduler_logs": "wp_actionscheduler_logs",
            "wc_category_lookup": "wp_wc_category_lookup"
          },
          "contact_tbl": "wp_bwf_contact",
          "customer_tbl": "wp_bwf_wc_customers",
          "contact_meta_tbl": "wp_bwf_contact_meta"
        },
        "id": "9",
        "uid": null,
        "email": "abc@gmail.com",
        "wp_id": "3",
        "meta": {},
        "children": {},
        "db_contact": {
          "id": "9",
          "wpid": "3",
          "uid": "9f20c97f3dcba190c31c7f811f11c730",
          "email": "abc@gmail.com",
          "f_name": "Rahul",
          "l_name": "Kumar",
          "contact_no": "1234567890",
          "country": "IN",
          "state": "Delhi",
          "timezone": "Asia/Kolkata",
          "type": "customer",
          "source": "wc_order",
          "points": "0",
          "tags": "[\"16\",\"24\",\"1\"]",
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
        "1": "Vasant Vihar",
        "2": "New Delhi",
        "3": "Delhi",
        "4": "110057",
        "5": "abc",
        "6": "Male",
        "7": "2022-06-27",
        "8": "2022-07-12",
        "9": "2022-08-03",
        "10": "2022-08-03",
        "11": null,
        "12": "[4,6,14]",
        "13": null,
        "14": null,
        "15": "2022-08-10",
        "16": "{\"0\":\"47\",\"1\":\"52\",\"2\":\"53\",\"3\":\"54\",\"4\":\"55\",\"5\":\"56\",\"6\":\"57\",\"7\":\"58\",\"8\":\"59\",\"9\":\"60\",\"10\":\"61\",\"11\":\"65\",\"12\":\"67\",\"13\":\"71\",\"14\":\"73\",\"15\":\"74\",\"16\":\"75\",\"17\":\"78\",\"18\":\"79\",\"19\":\"82\",\"20\":\"84\",\"21\":\"88\",\"22\":\"90\",\"23\":\"91\",\"24\":\"95\",\"25\":\"98\",\"26\":\"99\",\"27\":\"100\",\"28\":\"101\",\"29\":\"104\",\"30\":\"106\",\"31\":\"107\",\"32\":\"112\",\"33\":\"113\",\"34\":\"115\",\"35\":\"122\",\"36\":\"123\",\"37\":\"143\",\"38\":\"144\",\"39\":\"146\",\"40\":\"147\",\"41\":\"148\",\"42\":\"153\",\"43\":\"157\",\"44\":\"158\",\"45\":\"159\",\"46\":\"179\",\"47\":\"180\",\"48\":\"181\",\"49\":\"182\",\"50\":\"184\",\"51\":\"185\",\"52\":\"216\",\"53\":\"217\",\"54\":\"218\",\"55\":\"219\",\"56\":\"232\",\"57\":\"233\",\"58\":\"237\",\"59\":\"239\",\"60\":\"241\",\"61\":\"243\",\"62\":\"244\",\"63\":\"246\",\"64\":\"262\",\"65\":\"263\",\"66\":\"267\",\"67\":\"269\",\"68\":\"270\",\"69\":\"272\",\"70\":\"274\",\"71\":\"278\",\"73\":\"282\",\"74\":\"283\",\"75\":\"292\"}",
        "17": "[\"53\",\"99\",\"144\",\"184\",\"185\",\"233\",\"239\",\"241\",\"243\",\"244\",\"246\",\"269\",\"274\",\"278\"]",
        "18": "[\"47\",\"52\",\"53\",\"54\",\"55\",\"56\",\"57\",\"58\",\"59\",\"60\",\"61\",\"65\",\"67\",\"71\",\"72\",\"73\",\"74\",\"75\",\"78\",\"79\",\"82\",\"84\",\"88\",\"90\",\"91\",\"95\",\"98\",\"100\",\"101\",\"104\",\"106\",\"107\",\"112\",\"113\",\"115\",\"122\",\"123\",\"143\",\"144\",\"146\",\"147\",\"148\",\"153\",\"157\",\"158\",\"159\",\"179\",\"180\",\"181\",\"182\",\"184\",\"185\",\"216\",\"217\",\"218\",\"219\",\"232\",\"237\",\"262\",\"263\",\"267\",\"269\",\"270\",\"272\",\"274\",\"278\",\"282\",\"283\",\"292\"]",
        "20": "nks_active_email",
        "24": "om campaign",
        "25": "om campaign id",
        "26": "[\"True\"]",
        "28": "Two times a month",
        "36": ""
      },
      "already_exists": true,
      "task_localized": [],
      "was_unsubscribed": false,
      "unsubscribe_date": "",
      "assigned_tags": [],
      "assigned_lists": [],
      "removed_tags": [],
      "removed_lists": []
    },
    "limit": 0,
    "offset": 0
  }
}
```

## Assign Tags

This endpoint assign the tags to the contact.

```php
<?php

$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/contact/tag-assign/{contact_id}';
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

`POST http://example.com/wp-json/autonami/contact/tag-assign/{contact_id}`

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
        "id": "16",
        "value": "broadcast"
      },
      {
        "id": "24",
        "value": "nks_brodcast"
      },
      {
        "id": "1",
        "value": "nks"
      }
    ],
    "limit": 0,
    "offset": 0
  }
}
```

## Unassign Tags

This endpoint unassign the tags from the contact.

```php
<?php

$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/contact/tag-unassign/{contact_id}';
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

`POST http://example.com/wp-json/autonami/contact/tag-unassign/{contact_id}`

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
        "id": "16",
        "value": "broadcast"
      },
      {
        "id": "24",
        "value": "nks_brodcast"
      }
    ],
    "limit": 0,
    "offset": 0
  }
}
```

## Assign Lists

This endpoint assign the lists to the contact.

```php
<?php

$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/contact/list-assign/{contact_id}';
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
  "code": "success",
  "data": {
    "lists": [
      {
        "id": "4",
        "value": "list"
      }
    ],
    "limit": 0,
    "offset": 0
  }
}
```

## Unassign Lists

This endpoint unassign the lists from the contact.

```php
<?php

$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/contact/list-unassign/{contact_id}';
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
  "code": "success",
  "data": {
    "lists": [
      {
        "id": "6",
        "value": "finale list"
      }
    ],
    "limit": 0,
    "offset": 0
  }
}
```

## Delete a contact

This endpoint delete a contact.

```php
<?php

$site_url = 'http://example.com';
$endpoint = '/wp-json/autonami/contact/{contact_id}';
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

`DELETE http://example.com/wp-json/autonami/contact/{contact_id}`

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
