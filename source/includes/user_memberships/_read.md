## Get User Memberships

```php
<?php 

$woocommerce->get( 'memberships/members' ); 

?>
```

> JSON response example for the above command, containing an array of memberships data structured as follows:

```json
[
  {
    "id": 19,
    "customer_id": 80,
    "plan_id": 10,
    "status": "active",
    "order_id": 47,
    "product_id": 55,
    "subscription_id": null,
    "date_created": "2018-07-07T00:10:40+00:00",
    "date_created_gmt": "2018-07-06T16:10:40+00:00",
    "start_date": "2018-07-06T00:00:00+00:00",
    "start_date_gmt": "2018-07-05T16:00:00+00:00",
    "end_date": null,
    "end_date_gmt": null,
    "paused_date": null,
    "paused_date_gmt": null,
    "cancelled_date": null,
    "cancelled_date_gmt": null,
    "view_url": "http://skyverge.test/my-account/members-area/10/my-membership-content/",
    "profile_fields": [],
    "meta_data": [],
    "_links": {
      "self": [
        {
          "href": "http://example.com/wp-json/wc/v3/memberships/members/19"
        }
      ],
      "collection": [
        {
          "href": "http://example.com/wp-json/wc/v3/memberships/members"
        }
      ],
      "customer": [
        {
          "href": "http://example.com/wp-json/wc/v3/customers/80"
        }
      ]
    }
  }
]
```

**`memberships/members`**

This endpoint retrieves all user memberships.

### HTTP Request

`GET http://example.com/api/wc/v3/memberships/members`

### Query Parameters

Parameter      | Type                                     | Default   | Description
-------------- | -----------------------------------------| --------- | ------------
`customer`     | <code>int&#124;string</code>             | _`null`_  | List user memberships belonging to a specific user, specified by ID (integer), email address or login name (string).
`order`        | <code>int</code>                         | _`null`_  | List user memberships created from a specific order, given by its ID (integer).
`plan`         | <code>int&#124;int[]&#124;string</code>  | _`null`_  | List user memberships belonging to specific plan or plans. The passed value can be an integer (the plan ID), a string (the plan slug) or an array of IDs to specify different plans at once.
`product`      | <code>int</code>                         | _`null`_  | List user memberships created from the purchase of a specific product, given by its ID (integer).
`status`       | <code>string</code>                      | `any`     | List user memberships with a specific status.  By default all memberships of any status are listed.
`subscription` | <code>int</code>                         | _`null`_  | List user memberships associated with a specific subscription, given by its ID (integer).

### Pagination Parameters

Parameter      | Type                                    | Default   | Description
-------------- | ----------------------------------------| --------- | ------------
`page`         | <code>int</code>                        | `1`       | Main pagination parameter (integer). Only a given number of user memberships will be listed at any time, per page, according to the site settings.
`per_page`     | <code>int</code>                        | _`null`_  | The default number of results to return per page. The default value is normally set by WordPress own settings.
`offset`       | <code>int</code>                        | `0`       | Optional pagination parameter. If set will offset the results by the given number of user memberships specified (integer).
`exclude`      | <code>int&#124;int[]</code>             | _`null`_  | Ensure that the specified user memberships with given ID (integer) or IDs (array of integers) will be excluded from the results, if found.
`include`      | <code>int&#124;int[]</code>             | _`null`_  | Ensure that the specified user memberships with given ID (integer) or IDs (array of integers) will be included in the results, if found.


## Get a User Membership


```php
<?php 

// replace <id> with the requested member ID
$woocommerce->get( 'memberships/members/<id>' ); 

?>
```

> JSON response example for the request:

```json
{
  "id": 19,
  "customer_id": 80,
  "plan_id": 10,
  "status": "active",
  "order_id": 47,
  "product_id": 55,
  "subscription_id": null,
  "date_created": "2018-07-07T00:10:40+00:00",
  "date_created_gmt": "2018-07-06T16:10:40+00:00",
  "start_date": "2018-07-06T00:00:00+00:00",
  "start_date_gmt": "2018-07-05T16:00:00+00:00",
  "end_date": null,
  "end_date_gmt": null,
  "paused_date": null,
  "paused_date_gmt": null,
  "cancelled_date": null,
  "cancelled_date_gmt": null,
  "view_url": "http://skyverge.test/my-account/members-area/10/my-membership-content/",
  "profile_fields": [],
  "meta_data": [],
  "_links": {
    "self": [
      {
        "href": "http://example.com/wp-json/wc/v3/memberships/members/19"
      }
    ],
    "collection": [
      {
        "href": "http://example.com/wp-json/wc/v3/memberships/members"
      }
    ],
    "customer": [
      {
        "href": "http://example.com/wp-json/wc/v3/customers/80"
      }
    ]
  }
}
```

**`memberships/members/<id>`**

This endpoint retrieves a specific user membership.

### HTTP Request

`GET http://example.com/api/wc/v3/memberships/members/<id>`

### Available Parameters

Parameter | Type              | Description
--------- | ----------------- | ------------
`id`      | <code>int</code>  | Integer matching the requested user membership ID.
