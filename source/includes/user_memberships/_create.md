## Create a User Membership

```php
<?php 

$user_membership_data = [
  'customer_id' => 1,
  'plan_id' => 222,
];

$woocommerce->post( 'memberships/members', $user_membership_data ); 

?>
```

> JSON response example for the above command containing user membership data for the newly created membership:

```json
{
    "id": 1203,
    "customer_id": 1,
    "plan_id": 222,
    "status": "active",
    "order_id": null,
    "product_id": null,
    "subscription_id": null,
    "date_created": "2019-04-17T17:51:02+00:00",
    "date_created_gmt": "2019-04-17T09:51:02+00:00",
    "start_date": "2019-04-17T17:51:02+00:00",
    "start_date_gmt": "2019-04-17T09:51:02+00:00",
    "end_date": null,
    "end_date_gmt": null,
    "paused_date": null,
    "paused_date_gmt": null,
    "cancelled_date": null,
    "cancelled_date_gmt": null,
    "view_url": "http://skyverge.test/my-account/members-area/222/my-membership-content/",
    "meta_data": [],
    "_links": {
        "self": [
            {
                "href": "http://skyverge.test/wp-json/wc/v3/memberships/members/1203"
            }
        ],
        "collection": [
            {
                "href": "http://skyverge.test/wp-json/wc/v3/memberships/members"
            }
        ],
        "customer": [
            {
                "href": "http://skyverge.test/wp-json/wc/v3/customers/1"
            }
        ]
    }
}
```

**`memberships/members`**

Issue a **POST** request to this endpoint to create a new user membership.

### HTTP Request

`POST http://example.com/api/wc/v3/memberships/members`

### User Membership properties

Attribute            | Type                            | Description
---------------------| --------------------------------| ------------
`customer_id`        | <code>int</code>                | **Required**. ID of the customer that will become the owner of the user membership.
`plan_id`            | <code>int</code>                | **Required**. ID of the membership plan to grant access to.
`status`             | <code>string</code>             | _Optional_. The initial status of the user membership to be created. Defaults to _`active`_.
`order_id`           | <code>int</code>                | _Optional_. The ID of the associated order that granted access.
`product_id`         | <code>int</code>                | _Optional_. The ID of the associated product that granted access.
`subscription_id`    | <code>int</code>                | _Optional_. The ID of the subscription the membership will be linked to.
`start_date_gmt`     | <code>datetime</code>           | _Optional_. The date when the membership has started, in UTC. Defaults to the present time when the request is issued.
`end_date_gmt`       | <code>datetime</code>           | _Optional_. The date when the membership will end, in UTC. If status is expired, defaults to the present time when the request is issued.
`paused_date_gmt`    | <code>datetime</code>           | _Optional_. The date when the membership has been paused since, in UTC. If status is paused, defaults to the present time when the request is issued.
`cancelled_date_gmt` | <code>datetime</code>           | _Optional_. The date when the membership has been cancelled, in UTC. If status is cancelled, defaults to the present time when the request is issued.
`meta_data`          | <code>array</code>              | _Optional_. Pass any WordPress post meta data to be set on the membership. Each array item has an "id" _`(integer)`_, a "key" _`(string)`_ and a "value" (either a _`boolean`_, an _`integer`_, or _`string`_, which could also represent serialized data).

