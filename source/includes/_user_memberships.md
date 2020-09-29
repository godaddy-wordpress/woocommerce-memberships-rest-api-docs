# User Memberships

## The User Membership

A user membership is created when a customer gets access to a membership plan, therefore all user memberships are linked to one user and one membership plan only. Also, a membership has a status and a start date.  

### Data Structure

A user membership has the following data structure in the REST API:

Property             | Type                            | Description
-------------------- | --------------------------------| -----------
`id`                 | <code>int</code>                | _`read-only`_<br><br>The unique identifier (integer) of the user membership.
`customer_id`        | <code>int</code>                | The unique identifier (integer) of the customer that owns the membership.
`plan_id`            | <code>int</code>                | The unique identifier (integer) of the membership plan the membership is for.
`status`             | <code>string</code>             | The current status (string) of the user membership.
`order_id`           | <code>int&#124;null</code>      | The unique identifier (integer) of the order that may have granted access to the matching membership plan. If the user membership is not linked to an order, it will return _`null`_. 
`product_id`         | <code>int&#124;null</code>      | The unique identifier (integer) of a product that may have granted access to the matching membership plan. If the user membership is not linked to a product, it will return _`null`_.
`subscription_id`    | <code>int&#124;null</code>      | The unique identifier (integer) of a subscription that may be linked to the user membership. This property will exist only if the site is running WooCommerce Subscriptions alongside with Memberships. If there is no link to a subscription, the value will be _`null`_.<sup><a href="#user-membership-data-subscriptions-inactive">1</a></sup>
`date_created`       | <code>datetime</code>           | _`read-only`_<br><br>The date (in Atom format) when the user membership object was created, in the local timezone. This does not necessarily match with the start date.
`date_created_gmt`   | <code>datetime</code>           | _`read-only`_<br><br>The date (in Atom format) when the user membership object was created, in UTC. This does not necessarily match with the start date.
`start_date`         | <code>datetime</code>           | _`read-only`_<br><br>The date (in Atom format) when the membership starts, in the local timezone.
`start_date_gmt`     | <code>datetime</code>           | The date (in Atom format) when the membership starts, in UTC.
`end_date`           | <code>datetime&#124;null</code> | _`read-only`_<br><br>The date (in Atom format) when the ends, in the local timezone. This is `null` if the membership doesn't have an end date.
`end_date_gmt`       | <code>datetime&#124;null</code> | The date (in Atom format) when the ends, in UTC. This is `null` if the membership doesn't have an end date.
`paused_date`        | <code>datetime&#124;null</code> | _`read-only`_<br><br>The date (in Atom format) when the membership was last paused, in the local timezone. This is `null` if the membership was never paused. The value is not removed if the membership changes status.
`paused_date_gmt`    | <code>datetime&#124;null</code> | _`read-only`_<br><br>The date (in Atom format) when the membership was last paused, in UTC. This is `null` if the membership was never paused. The value is not removed if the membership changes status.
`cancelled_date`     | <code>datetime&#124;null</code> | The date (in Atom format) when the membership was cancelled, in the local timezone. This is `null` if the membership was not cancelled. 
`cancelled_date_gmt` | <code>datetime&#124;null</code> | The date (in Atom format) when the membership was cancelled, in UTC. This is `null` if the membership was not cancelled.
`view_url`           | <code>string</code>             | _`read-only`_<br><br>URL pointing to the site's Members Area accessible to the membership's owner.    
`profile_fields`     | <code>array&#124;object</code>  | Holds any profile fields set on the membership. Each array item has a "slug" _`(string)`_ and a "value" (either a _`boolean`_, an _`integer`_, _`float`_, _`string`_, or _`array`_).
`meta_data`          | <code>array&#124;object</code>  | Holds any WordPress meta data set on the membership. Each array item has an "id" _`(integer)`_, a "key" _`(string)`_ and a "value" (either a _`boolean`_, an _`integer`_, or _`string`_, which could also represent serialized data).
`_links`             | <code>array</code>              | _`read-only`_<br><br>An array of items linking to related objects accessible through the REST API.   


**Notes:**

 <sup id="user-membership-data-subscriptions-inactive">1</sup> If WooCommerce Subscriptions is inactive this field will not exist.
