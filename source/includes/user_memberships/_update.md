## Update a User Membership

```php
<?php 

$user_membership_data = [
  'status' => 'paused',
];

$woocommerce->put( 'memberships/members', $user_membership_data ); 

?>
```

> JSON response example:

```json
{
    "id": 1203,
    "customer_id": 1,
    "plan_id": 222,
    "status": "paused",
    "order_id": null,
    "product_id": null,
    "subscription_id": null,
    "date_created": "2019-04-17T17:51:02",
    "date_created_gmt": "2019-04-17T09:51:02",
    "start_date": "2019-04-17T17:51:02",
    "start_date_gmt": "2019-04-17T09:51:02",
    "end_date": null,
    "end_date_gmt": null,
    "paused_date": "2019-04-17T18:05:18",
    "paused_date_gmt": "2019-04-17T10:05:18",
    "cancelled_date": null,
    "cancelled_date_gmt": null,
    "view_url": "http://skyverge.test/my-account/members-area/222/my-membership-content/",
    "profile_fields": [],
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

**`memberships/members/<id>`**

Issue a **PUT** request to this endpoint to update an existing user membership. You can pass the same properties as when creating a user membership, to update them.

### HTTP Request

`PUT http://example.com/wp-json/wc/v3/memberships/members/<id>`
