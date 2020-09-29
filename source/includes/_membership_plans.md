# Membership Plans

## The Membership Plan

A membership plan is a collection of settings and conditions according to which customers can get access to restricted content, products, get member only discounts and so on.  

### Data Structure

A membership plan has the following data structure in the REST API:

Property                             | Type                                    | Description
------------------------------------ | ----------------------------------------| ------------
`id`                                 | <code>int</code>                        | The unique identifier (integer) of the membership plan.
`name`                               | <code>string</code>                     | The membership plan name.
`slug`                               | <code>string</code>                     | The membership plan slug (a unique string identifier).
`status`                             | <code>string</code>                     | The membership plan status (this usually matches standard WordPress post statuses, with _`publish`_ or _`draft`_ being the most common for plans).
`access_method`                      | <code>string</code>                     | The method that membership plan prescribes for users to gain access.
`has_subscription`                   | <code>bool</code>                       | Whether the plan has at least one subscription among the products that can grant access.<sup><a href="#membership-plan-data-subscriptions-inactive">1</a></sup> 
`has_subscription_installment`       | <code>bool</code>                       | Whether the plan uses the subscription for managing installment plans (the membership plan length is not directly tied to the subscription length).<sup><a href="#membership-plan-data-subscriptions-inactive">1</a></sup>
`access_product_ids`                 | <code>int[]</code>                      | An optional array of product IDs (integers) to products that will grant access to the membership plan upon purchase. If no products grant access to the membership plan, the value will be an empty array.
`access_length_type`                 | <code>string</code>                     | The access length type: specific (relative dates), fixed (fixed dates) or unlimited.
`subscription_access_length_type`    | <code>string</code>                     | The access length type when the product that granted access to the plan is a subscription: subscription (access lasts as long as the subscription does), specific (relative dates), fixed (fixed dates) or unlimited.<sup><a href="#membership-plan-data-subscriptions-inactive">1</a></sup>
`access_length`                      | <code>int&#124;null</code>              | The length in seconds that a user membership created for this plan will have, by default. This could be null for unlimited memberships that have no set end (or may be tied to a subscription).
`subcription_access_length`          | <code>int&#124;null</code>              | When access to the plan is tied to a subscription, the length in seconds that a corresponding user membership will have. This could be null if it lasts as long as the subscription is active or the plan does not have a subscription product that can grant access.<sup><a href="#membership-plan-data-subscriptions-inactive">1</a></sup>
`access_start_date`                  | <code>datetime&#124;null</code>         | If the plan length type is based on fixed dates, this will be the date when any user membership will start, otherwise it will be _`null`_. 
`access_start_date_gmt`              | <code>datetime&#124;null</code>         | If the plan length type is based on fixed dates, this will be the date when any user membership will start, otherwise it will be _`null`_.<sup><a href="#membership-plan-data-subscriptions-inactive">1</a></sup>
`access_end_date`                    | <code>datetime&#124;null</code>         | If the plan length type is fixed this will be a fixed date when any membership will end, otherwise it will be _`null`_. 
`access_end_date_gmt`                | <code>datetime&#124;null</code>         | If the plan length type is fixed this will be a fixed date when any membership will end, otherwise it will be _`null`_.
`subscription_access_start_date`     | <code>datetime&#124;null</code>         | When access to the plan is tied to a subscription and the plan length type is based on fixed dates, this will be the date when any user membership will start, otherwise it will be _`null`_.<sup><a href="#membership-plan-data-subscriptions-inactive">1</a></sup> 
`subscription_access_start_date_gmt` | <code>datetime&#124;null</code>         | When access to the plan is tied to a subscription and the plan length type is based on fixed dates, this will be the date when any user membership will start, otherwise it will be _`null`_.<sup><a href="#membership-plan-data-subscriptions-inactive">1</a></sup>
`subscription_access_end_date`       | <code>datetime&#124;null</code>         | When access to the plan is tied to a subscription and the plan length type is fixed this will be a fixed date when any membership will end, otherwise it will be _`null`_.<sup><a href="#membership-plan-data-subscriptions-inactive">1</a></sup>
`subscription_access_end_date_gmt`   | <code>datetime&#124;null</code>         | When access to the plan is tied to a subscription and the plan length type is fixed this will be a fixed date when any membership will end, otherwise it will be _`null`_.<sup><a href="#membership-plan-data-subscriptions-inactive">1</a></sup>
`date_created`                       | <code>datetime</code>                   | The date (in Atom format) when the membership plan object was created, in the local timezone. 
`date_created_gmt`                   | <code>datetime</code>                   | The date (in Atom format) when the membership plan object was created, in UTC.
`date_modified`                      | <code>datetime</code>                   | The date (in Atom format) when the membership plan object was last modified, in the local timezone.
`date_modified_gmt`                  | <code>datetime</code>                   | The date (in Atom format) when the membership plan object was last modified, in UTC.
`meta_data`                          | <code>array</code>                      | Holds any WordPress meta data set on the plan. Each array item has an "id" _`(integer)`_, a "key" _`(string)`_ and a "value" (either a _`boolean`_, an _`integer`_, or _`string`_, which could also represent serialized data).
`_links`                             | <code>array</code>                      | An array of items linking to related objects accessible through the REST API.   


**Notes:**

 <sup id="membership-plan-data-subscriptions-inactive">1</sup> If WooCommerce Subscriptions is inactive this field will not exist.
