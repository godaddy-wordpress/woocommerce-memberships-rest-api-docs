---
title: WooCommerce Memberships REST API Documentation

language_tabs: # must be one of https://git.io/vQNgJ
  - php
  - ruby

toc_footers:
  - <a href='https://woocommerce.com/products/woocommerce-memberships/'>Get WooCommerce Memberships</a>
  - <a href='https://docs.woocommerce.com/document/woocommerce-memberships/'>Plugin Documentation</a>

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

**`/memberships`**

The memberships root endpoint lists all routes, along with supported HTTP methods for each, made available by WooCommerce Memberships.

### HTTP REQUEST

`GET http://example.com/wp-json/wc/v2/memberships`

# User Memberships

## The User Membership

A user membership is created when a customer gets access to a membership plan, therefore all user memberships are linked to one user and one membership plan only. Also, a membership has a status and a start date.  

### Data Structure

A user membership has the following data structure in the REST API:

Property             | Type                            | Description
-------------------- | --------------------------------| ------------
`id`                 | <code>int</code>                | The unique identifier (integer) of the user membership.
`customer_id`        | <code>int</code>                | The unique identifier (integer) of the customer that owns the membership.
`plan_id`            | <code>int</code>                | The unique identifier (integer) of the membership plan the membership is for.
`status`             | <code>string</code>             | The current status (string) of the user membership.
`order_id`           | <code>int&#124;null</code>      | The unique identifier (integer) of the order that may have granted access to the matching membership plan. If the user membership is not linked to an order, it will return _`null`_.
`subcription_id`     | <code>int&#124;null</code>      | The unique identifier (integer) of a subscription that may be linked to the user membership. This property will exist only if the site is running WooCommerce Subscriptions alongside with Memberships. If there is no link to a subscription, the value will be _`null`_.
`product_id`         | <code>int&#124;null</code>      | The unique identifier (integer) of a product that may have granted access to the matching membership plan. If the user membership is not linked to a product, it will return _`null`_.
`date_created`       | <code>datetime</code>           | The date (in Atom format) when the user membership object was created, in the local timezone. This does not necessarily match with the start date.
`date_created_gmt`   | <code>datetime</code>           | The date (in Atom format) when the user membership object was created, in UTC. This does not necessarily match with the start date.
`start_date`         | <code>datetime</code>           | The date (in Atom format) when the membership starts, in the local timezone.
`start_date_gmt`     | <code>datetime</code>           | The date (in Atom format) when the membership starts, in UTC.
`end_date`           | <code>datetime&#124;null</code> | The date (in Atom format) when the ends, in the local timezone. This is `null` if the membership doesn't have an end date.
`end_date_gmt`       | <code>datetime&#124;null</code> | The date (in Atom format) when the ends, in UTC. This is `null` if the membership doesn't have an end date.
`paused_date`        | <code>datetime&#124;null</code> | The date (in Atom format) when the membership was last paused, in the local timezone. This is `null` if the membership was never paused. The value is not removed if the membership changes status.
`paused_date_gmt`    | <code>datetime&#124;null</code> | The date (in Atom format) when the membership was last paused, in UTC. This is `null` if the membership was never paused. The value is not removed if the membership changes status.
`cancelled_date`     | <code>datetime&#124;null</code> | The date (in Atom format) when the membership was cancelled, in the local timezone. This is `null` if the membership was not cancelled. 
`cancelled_date_gmt` | <code>datetime&#124;null</code> | The date (in Atom format) when the membership was cancelled, in UTC. This is `null` if the membership was not cancelled. 
`meta_data`          | <code>array</code>              | Holds any WordPress meta data set on the membership. Each array item has an `id` (integer), a `key` (string) and a `value` (either a boolean, an integer, or string, or serialized data).
`links`              | <code>array</code>              | An array of items linking to related objects accessible through the REST API.   

## Get All User Memberships

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

**`memberships/members`**

This endpoint retrieves all user memberships.

### HTTP Request

`GET http://example.com/api/wc/v2/memberships/members`

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


## Get One User Membership


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

**`memberships/members/<id>`**

This endpoint retrieves a specific user membership.

### HTTP Request

`GET http://example.com/api/wc/v2/memberships/members/<id>`

### URL Parameters

Parameter | Type              | Description
--------- | ----------------- | ------------
`id`      | <code>int</code>  | Integer matching the requested user membership ID.

# Membership Plans

## The Membership Plan

A membership plan is a collection of settings and conditions according to which customers can get access to restricted content, products, get member only discounts and so on.  

### Data Structure

A membership plan has the following data structure in the REST API:

Property                           | Type                          | Description
---------------------------------- | ------------------------------| ------------
`id`                               | <code>int</code>              | The unique identifier (integer) of the membership plan.
`name`                             | <code>string</code>           | The membership plan name.
`slug`                             | <code>string</code>           | The membership plan slug (a unique string identifier).
`status`                           | <code>string</code>           | The membership plan status (this usually matches standard WordPress post statuses, with `publish` or `draft` being the most common for plans).
`access_method`                    | <code>string</code>           | The method that membership plan prescribes for users to gain access.
`access_length_type`               | <code>string</code>           | The access length type: specific (relative dates), fixed (fixed dates) or unlimited.
`access_length`                    | <code>string</code>           | The length in a human readable format (e.g. 2 weeks or 3 months, 1 year, etc.) that a user membership created for this plan will have, by default. This could be an empty string for unlimited memberships that have no set end (or may be tied to a subscription).
`access_length_seconds`            | <code>int&#124;null</code>    | The equivalent in seconds of the access length, calculated by approximation in the site timezone. If the access length is nto set this will return _`null`_.
`access_length_seconds_gmt`        | <code>int&#124;null</code>    | The equivalent in seconds of the access length, calculated by approximation in UTC. If the access length is nto set this will return _`null`_.
`access_product_ids`               | <code>int[]</code>            | An optional array of product IDs (integers) to products that will grant access to the membership plan upon purchase. If no products grant access to the membership plan, the value will be an empty array.
`is_subscription_plan`             | <code>bool</code>             | Whether the plan has at least one subscription among the products that can grant access. If Subscriptions is inactive this field will not exist. 
`is_subscription_installment_plan` | <code>bool</code>             | Whether the plan uses the subscription for managing installment plans (the membership plan length is not directly tied to the subscription length). If Subscription is inactive this field will not exist.
`access_start_date`                | <code>datetime</code>         | If the plan length type is based on fixed dates, this will be the date when any user membership will start, otherwise it will default to now, in the local timezone and in Atom format. 
`access_start_date_gmt`            | <code>datetime</code>         | If the plan length type is based on fixed dates, this will be the date when any user membership will start, otherwise it will default to now, in the UTC and in Atom format.
`access_end_date`                  | <code>datetime</code>         | If the plan length type is fixed this will be a fixed date when any membership will end, otherwise it will be a date calculated relatively to now, in the local timezone and in Atom format. 
`access_end_date_gmt`              | <code>datetime</code>         | If the plan length type is fixed this will be a fixed date when any membership will end, otherwise it will be a date calculated relatively to now, in UTC and in Atom format.
`date_created`                     | <code>datetime</code>         | The date (in Atom format) when the membership plan object was created, in the local timezone. 
`date_created_gmt`                 | <code>datetime</code>         | The date (in Atom format) when the membership plan object was created, in UTC.
`date_modified`                    | <code>datetime</code>         | The date (in Atom format) when the membership plan object was last modified, in the local timezone.
`date_modified_gmt`                | <code>datetime</code>         | The date (in Atom format) when the membership plan object was last modified, in UTC.
`meta_data`                        | <code>array</code>            | Holds any WordPress meta data set on the plan. Each array item has an `id` (integer), a `key` (string) and a `value` (either a boolean, an integer, or string, or serialized data).
`links`                            | <code>array</code>            | An array of items linking to related objects accessible through the REST API.   

## Get All Membership Plans

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

**`/memberships/plans`**

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

## Get One Membership Plan

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

**`/memberships/plans/<id>`**

This endpoint retrieves a specific membership plan.

### HTTP Request

`GET http://example.com/api/wc/v2/memberships/plans/<id>`

### URL Parameters

Parameter | Value             | Description
--------- | ----------------- | ------------
`id`      | <code>int</code>  | Integer matching the requested membership plan ID.
