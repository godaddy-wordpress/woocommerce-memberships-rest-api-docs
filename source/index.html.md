---
title: WooCommerce Memberships REST API Documentation

language_tabs: # must be one of https://git.io/vQNgJ
  - php
  - ruby

toc_footers:
  - <a href='https://woocommerce.com/products/woocommerce-memberships/'>Get WooCommerce Memberships</a>
  - <a href='https://docs.woocommerce.com/document/woocommerce-memberships/'>WooCommerce Memberships Documentation</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the [WooCommerce Memberships](https://woocommerce.com/products/woocommerce-memberships/) REST API documentation! 

Memberships extends [WooCommerce](https://woocommerce.com/) and builds upon the [WordPress REST API](http://v2.wp-api.org/) to handle user memberships and memberships plans data through robust REST API endpoints.

Memberships currently supports v2 of the WooCommerce REST API extension for WordPress, therefore all its endpoints will be added to the `/wc/v2/` route.

This documentation showcases the available HTTP API methods and endpoints to perform valid requests, along with examples in PHP and Ruby.

If you spot a typo, an error, have a question, want to provide feedback or extend the documentation, please refer to the [GitHub repository of this documentation](https://github.com/skyverge/woocommerce-memberships-rest-api-docs).

# Authentication

Since Memberships REST API is built on top of the WordPress REST API and requires WooCommerce to function, authorization for performing HTTP requests successfully is handled by WooCommerce and WordPress.  

WooCommerce includes two ways to authenticate with the WP REST API. It is also possible to authenticate using any [WP REST API authentication plugin](http://v2.wp-api.org/guide/authentication/) or method.

Follow instructions from the [WooCommerce core REST API Authentication chapter](https://woocommerce.github.io/woocommerce-rest-api-docs/#authentication) for authentication guidelines.

# Discovery

## Available Routes

This endpoint lists all routes, along with supported HTTP methods for each, made available by WooCommerce Memberships.

### HTTP REQUEST

`GET http://example.com/wp-json/wc/v2/memberships`

# User Memberships

## Get User Memberships

```php
// TODO
```

```ruby
## TODO
```

> The above command returns JSON data with an array of user memberships structured like this:

```json
[
    {
        "id": 19,
        "customer_id": 80,
        "plan_id": 10,
        "status": "active",
        "order_id": 47,
        "product_id": 55,
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
        "meta_data": [],
        "_links": {
            "self": [
                {
                    "href": "http://example.com/wp-json/wc/v2/memberships/members/19"
                }
            ],
            "collection": [
                {
                    "href": "http://example.com/wp-json/wc/v2/memberships/members"
                }
            ],
            "customer": [
                {
                    "href": "http://example.com/wp-json/wc/v2/customers/80"
                }
            ]
        }
    }
]
```

This endpoint retrieves all user memberships.

### HTTP Request

`GET http://example.com/api/wc/v2/memberships/members`

### Query Parameters

Parameter      | Value                                    | Default   | Description
-------------- | -----------------------------------------| --------- | ------------
`customer`     | <code>int&#124;string</code>             | _`null`_  | List user memberships belonging to a specific user, specified by ID (integer), email address or login name (string).
`order`        | <code>int</code>                         | _`null`_  | List user memberships created from a specific order, given by its ID (integer).
`plan`         | <code>int&#124;int[]&#124;string</code>  | _`null`_  | List user memberships belonging to specific plan or plans. The passed value can be an integer (the plan ID), a string (the plan slug) or an array of IDs to specify different plans at once.
`product`      | <code>int</code>                         | _`null`_  | List user memberships created from the purchase of a specific product, given by its ID (integer).
`status`       | <code>string</code>                      | `any`     | List user memberships with a specific status.  By default all memberships of any status are listed.
`subscription` | <code>int</code>                         | _`null`_  | List user memberships associated with a specific subscription, given by its ID (integer).

### Pagination Parameters

Parameter      | Value                                   | Default   | Description
-------------- | ----------------------------------------| --------- | ------------
`page`         | <code>int</code>                        | `1`       | Main pagination parameter (integer). Only a given number of user memberships will be listed at any time, per page, according to the site settings.
`per_page`     | <code>int</code>                        | _`null`_  | The default number of results to return per page. The default value is normally set by WordPress own settings.
`offset`       | <code>int</code>                        | `0`       | Optional pagination parameter. If set will offset the results by the given number of user memberships specified (integer).
`exclude`      | <code>int&#124;int[]</code>             | _`null`_  | Ensure that the specified user memberships with given ID (integer) or IDs (array of integers) will be excluded from the results, if found.
`include`      | <code>int&#124;int[]</code>             | _`null`_  | Ensure that the specified user memberships with given ID (integer) or IDs (array of integers) will be included in the results, if found.


## Get User Membership


```php
// TODO
```

```ruby
## TODO
```

> The above command returns JSON data with a user membership structured like this:

```json
{
  "id": 19,
  "customer_id": 80,
  "plan_id": 10,
  "status": "active",
  "order_id": 47,
  "product_id": 55,
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
  "meta_data": [],
  "_links": {
      "self": [
          {
              "href": "http://example.com/wp-json/wc/v2/memberships/members/19"
          }
      ],
      "collection": [
          {
              "href": "http://example.com/wp-json/wc/v2/memberships/members"
          }
      ],
      "customer": [
          {
              "href": "http://example.com/wp-json/wc/v2/customers/80"
          }
      ]
  }
}
```

This endpoint retrieves a specific user membership.

### HTTP Request

`GET http://example.com/api/wc/v2/memberships/members/<id>`

### URL Parameters

Parameter | Value             | Description
--------- | ----------------- | ------------
`id`      | <code>int</code>  | Integer matching the requested user membership ID.


# Membership Plans

## Get Membership Plans

```php
// TODO
```

```ruby
## TODO
```

> The above command returns JSON data with an array of membership plans structured like this:

```json
[
    {
        "id": 55,
        "name": "Gold Membership Plan",
        "slug": "gold-membership-plan",
        "status": "publish",
        "access_method": "purchase",
        "access_length": "",
        "access_length_seconds": null,
        "access_length_seconds_gmt": null,
        "access_product_ids": [
            84,
            86
        ],
        "access_start_date": "2018-07-10T08:00:00+00:00",
        "access_start_date_gmt": "2018-07-10T00:00:00+00:00",
        "access_end_date": "",
        "access_end_date_gmt": "",
        "date_created": "2018-05-08T14:24:11+00:00",
        "date_created_gmt": "2018-05-08T06:24:11+00:00",
        "date_modified": "2018-06-06T11:40:11+00:00",
        "date_modified_gmt": "2018-06-06T03:40:11+00:00",
        "meta_data": [],
        "_links": {
            "self": [
                {
                    "href": "http://example.com/wp-json/wc/v2/memberships/plans/55"
                }
            ],
            "collection": [
                {
                    "href": "http://example.com/wp-json/wc/v2/memberships/plans"
                }
            ],
            "products": [
                {
                    "href": "http://example.com/wp-json/wc/v2/products/84"
                    
                },
                {
                    "href": "http://example.com/wp-json/wc/v2/products/86"
                }
            ]
        }
    }
]
```

This endpoint retrieves all membership plans.

### HTTP Request

`GET http://example.com/api/wc/v2/memberships/plans`

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


## Get Membership Plan


```php
// TODO
```

```ruby
## TODO
```

> The above command returns JSON data with a membership plan structured like this:

```json
{
    "id": 55,
    "name": "Gold Membership Plan",
    "slug": "gold-membership-plan",
    "status": "publish",
    "access_method": "purchase",
    "access_length": "",
    "access_length_seconds": null,
    "access_length_seconds_gmt": null,
    "access_product_ids": [
        84,
        86
    ],
    "access_start_date": "2018-07-10T08:00:00+00:00",
    "access_start_date_gmt": "2018-07-10T00:00:00+00:00",
    "access_end_date": "",
    "access_end_date_gmt": "",
    "date_created": "2018-05-08T14:24:11+00:00",
    "date_created_gmt": "2018-05-08T06:24:11+00:00",
    "date_modified": "2018-06-06T11:40:11+00:00",
    "date_modified_gmt": "2018-06-06T03:40:11+00:00",
    "meta_data": [],
    "_links": {
        "self": [
            {
                "href": "http://example.com/wp-json/wc/v2/memberships/plans/55"
            }
        ],
        "collection": [
            {
                "href": "http://example.com/wp-json/wc/v2/memberships/plans"
            }
        ],
        "products": [
            {
                "href": "http://example.com/wp-json/wc/v2/products/84"
                
            },
            {
                "href": "http://example.com/wp-json/wc/v2/products/86"
            }
        ]
    }
}
```

This endpoint retrieves a specific membership plan.

### HTTP Request

`GET http://example.com/api/wc/v2/memberships/plans/<id>`

### URL Parameters

Parameter | Value             | Description
--------- | ----------------- | ------------
`id`      | <code>int</code>  | Integer matching the requested membership plan ID.
