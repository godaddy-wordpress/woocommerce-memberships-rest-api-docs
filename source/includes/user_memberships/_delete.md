## Delete a User Membership

```php
<?php 

// replace <id> with the member ID to delete
$woocommerce->delete( 'memberships/members/<id>', [ 'force' => true ] ); 

?>
```

> JSON response example for the request, containing a flag to confirm deletion and user membership data pertaining to the deleted user membership before the deletion was executed:

```json
{
    "deleted": true,
    "previous": {
        "id": 13,
        "customer_id": 1,
        "plan_id": 8,
        "status": "active",
        "order_id": 1200,
        "product_id": 848,
        "subscription_id": 1191,
        "date_created": "2019-04-17T15:29:34+00:00",
        "date_created_gmt": "2019-04-17T07:29:34+00:00",
        "start_date": "2019-04-17T15:29:34+00:00",
        "start_date_gmt": "2019-04-17T07:29:34+00:00",
        "end_date": null,
        "end_date_gmt": null,
        "paused_date": null,
        "paused_date_gmt": null,
        "cancelled_date": null,
        "cancelled_date_gmt": null,
        "view_url": "http://skyverge.test/my-account/members-area/13/my-membership-content/",
        "meta_data": []
    }
}
```

**`memberships/members/<id>`**

Issue a **DELETE** request to this endpoint to permanently delete a user membership.

### HTTP Request

`DELETE http://example.com/api/wc/v3/memberships/members/<id>`

### Available Parameters

Parameter | Type              | Description
--------- | ----------------- | ------------
`id`      | <code>int</code>  | Integer matching the user membership ID to delete.
