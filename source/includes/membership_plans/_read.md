## Get All Membership Plans

```php
<?php 

$woocommerce->get( 'memberships/plans' ); 

?>
```

> JSON response example for the above command, containing an array of membership plans data structured as follows:

```json
[
  {
    "id": 55,
    "name": "Gold Membership Plan",
    "slug": "gold-membership-plan",
    "status": "publish",
    "access_method": "purchase",
    "has_subscription": false,
    "has_subscription_installment": false,
    "access_product_ids": [
      84,
      86
    ],
    "access_length_type": "specific",
    "subscription_access_length_type": "subscription",
    "access_length": 1209600,
    "access_start_date": null,
    "access_start_date_gmt": null,
    "access_end_date": null,
    "access_end_date_gmt": null,
    "subscription_access_start_date": null,
    "subscription_access_start_date_gmt": null,
    "subscription_access_end_date": null,
    "subscription_access_end_date_gmt": null,
    "date_created": "2018-05-17T13:06:36+00:00",
    "date_created_gmt": "2018-05-17T05:06:36+00:00",
    "date_modified": "2018-08-24T16:15:26+00:00",
    "date_modified_gmt": "2018-08-24T08:15:26+00:00",
    "meta_data": [],
    "_links": {
      "self": [
        {
          "href": "http://example.com/wp-json/wc/v3/memberships/plans/55"
        }
      ],
      "collection": [
        {
          "href": "http://example.com/wp-json/wc/v3/memberships/plans"
        }
      ],
      "products": [
        {
          "href": "http://example.com/wp-json/wc/v3/products/84"  
        },
        {
          "href": "http://example.com/wp-json/wc/v3/products/86"
        }
      ]
    }
  }
]
```

**`/memberships/plans`**

This endpoint retrieves all membership plans.

### HTTP Request

`GET http://example.com/api/wc/v3/memberships/plans`

### Query Parameters

Parameter      | Value                                   | Default   | Description
-------------- | ----------------------------------------| --------- | ------------
`status`       | <code>string</code>                     | `publish` | List membership plans with a specific post status. By default only membership plans that have been publicly published are listed.

### Pagination Parameters

Parameter      | Value                                   | Default   | Description
-------------- | ----------------------------------------| --------- | ------------
`page`         | <code>int</code>                        | `1`       | Main pagination parameter (integer). Only a given number of membership plans will be listed at any time, per page, according to the site settings.
`per_page`     | <code>int</code>                        | _`null`_  | The default number of results to return per page. The default value is normally set by WordPress own settings.
`offset`       | <code>int</code>                        | `0`       | Optional pagination parameter. If set will offset the results by the given number of membership plans specified (integer).
`exclude`      | <code>int&#124;int[]</code>             | _`null`_  | Ensure that the specified membership plans with given ID (integer) or IDs (array of integers) will be excluded from the results, if found.
`include`      | <code>int&#124;int[]</code>             | _`null`_  | Ensure that the specified membership plans with given ID (integer) or IDs (array of integers) will be included in the results, if found.

## Get One Membership Plan

```php
<?php 

// replace <id> with the requested plan ID
$woocommerce->get( 'memberships/plans/<id>' ); 

?>
```

> JSON response example for the request:

```json
{
  "id": 55,
  "name": "Gold Membership Plan",
  "slug": "gold-membership-plan",
  "status": "publish",
  "access_method": "purchase",
  "has_subscription": false,
  "has_subscription_installment": false,
  "access_product_ids": [
    84,
    86
  ],
  "access_length_type": "specific",
  "subscription_access_length_type": "subscription",
  "access_length": 1209600,
  "access_start_date": null,
  "access_start_date_gmt": null,
  "access_end_date": null,
  "access_end_date_gmt": null,
  "subscription_access_start_date": null,
  "subscription_access_start_date_gmt": null,
  "subscription_access_end_date": null,
  "subscription_access_end_date_gmt": null,
  "date_created": "2018-05-17T13:06:36+00:00",
  "date_created_gmt": "2018-05-17T05:06:36+00:00",
  "date_modified": "2018-08-24T16:15:26+00:00",
  "date_modified_gmt": "2018-08-24T08:15:26+00:00",
  "meta_data": [],
  "_links": {
    "self": [
      {
        "href": "http://example.com/wp-json/wc/v3/memberships/plans/55"
      }
    ],
    "collection": [
      {
        "href": "http://example.com/wp-json/wc/v3/memberships/plans"
      }
    ],
    "products": [
      {
        "href": "http://example.com/wp-json/wc/v3/products/84"  
      },
      {
        "href": "http://example.com/wp-json/wc/v3/products/86"
      }
    ]
  }
}
```

**`/memberships/plans/<id>`**

This endpoint retrieves a specific membership plan.

### HTTP Request

`GET http://example.com/api/wc/v3/memberships/plans/<id>`

### Available Parameters

Parameter | Value             | Description
--------- | ----------------- | ------------
`id`      | <code>int</code>  | Integer matching the requested membership plan ID.
