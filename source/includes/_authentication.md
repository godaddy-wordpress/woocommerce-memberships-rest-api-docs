# Authentication

```php
HTTP Basic Auth example:

<?php

require __DIR__ . '/vendor/autoload.php';

use Automattic\WooCommerce\Client;

$woocommerce = new Client(
    'https://example.com',
    'consumer_key',
    'consumer_secret',
    [
        'wp_api' => true,
        'version' => 'wc/v2'
    ]
);

?>

Occasionally, some servers may not parse the Authorization header correctly.

If you see a "Consumer key is missing" error when authenticating over SSL, likely you have a server issue. 

In this case, you may provide the consumer key/secret as query string parameters instead.

Example for servers that not properly parse the Authorization header:

<?php

require __DIR__ . '/vendor/autoload.php';

use Automattic\WooCommerce\Client;

$woocommerce = new Client(
    'https://example.com',
    'consumer_key',
    'consumer_secret',
    [
        'wp_api' => true,
        'version' => 'wc/v2',
        // Force Basic Authentication as query string true and using under HTTPS
        'query_string_auth' => true 
    ]
);

?>
```

Since Memberships REST API is built on top of the WordPress REST API and requires WooCommerce to function, authorization for performing HTTP requests successfully is handled by WooCommerce and WordPress.  

WooCommerce includes two ways to authenticate with the WP REST API. It is also possible to authenticate using any [WP REST API authentication plugin](http://v2.wp-api.org/guide/authentication/) or method.

Follow instructions from the [WooCommerce core REST API Authentication chapter](https://woocommerce.github.io/woocommerce-rest-api-docs/#authentication) for authentication guidelines.
