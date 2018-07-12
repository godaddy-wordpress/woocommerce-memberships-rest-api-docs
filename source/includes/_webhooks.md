# WebHooks

WooCommerce Memberships extends WooCommerce with custom webhooks that are triggered when changes occur to User Memberships or Membership Plan objects.

## Membership Plan WebHooks

Each of the following webhooks will send a corresponding [user membership object](/woocommerce-memberships-rest-api-docs#the-user-membership) as payload.

Name                          | Description
----------------------------- | ---------------------------------
`user_membership.created`     | Triggered when a user membership is created, via any means.
`user_membership.updated`     | Triggered when a user membership is changed or modified (e.g. status change, update in admin, etc.).
`user_membership.transferred` | Triggered when a user membership is transferred from a user to another (the user owner of the membership has changed).
`user_membership.created`     | Triggered when a user membership has been permanently deleted.

## Membership Plan WebHooks

Each of the following webhooks will send a corresponding [membership plan object](/woocommerce-memberships-rest-api-docs#the-membership-plan) as payload.

Name                          | Description
----------------------------- | ---------------------------------
`membership_plan.created`     | Triggered when a membership plan has been created.
`membership_plan.updated`     | Triggered when a membership plan has been updated (with one of its properties modified or just saved without data change).
`membership_plan.deleted`     | Triggered when a membership plan has been moved to the trash (not permanently deleted, but assumed so unless restored).
`membership_plan.restored`    | Triggered when a membership plan is moved back from the trash (not necessarily as published, could be in draft status or other status).
