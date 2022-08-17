# Introduction

```php
The PHP examples in this documentation will assume you are using the WooCommerce client from Automattic to connect to the WooCommerce REST API, which you can require in your project via Composer:

$ composer require automattic/woocommerce

You will then need to configure and instantiate the client in your project, like so:

<?php

require __DIR__ . '/vendor/autoload.php';

use Automattic\WooCommerce\Client;

$woocommerce = new Client(
    'http://example.com',    // Your store URL
    'consumer_key',          // Your consumer key
    'consumer_secret',       // Your consumer secret
    [
        'wp_api'  => true,   // Enable the WP REST API integration
        'version' => 'wc/v3' // WooCommerce WP REST API version
    ]
);

?>
```

Welcome to the [WooCommerce Memberships](https://woocommerce.com/products/woocommerce-memberships/) REST API documentation! 

Since version 1.11.0, Memberships extends [WooCommerce](https://woocommerce.com/) and builds upon the [WordPress REST API](http://v2.wp-api.org/) to handle user memberships and memberships plans data through robust REST API endpoints.

Memberships currently supports v2 and v3 (added in 1.12.0) of the WooCommerce REST API extension for WordPress. All its endpoints will be added to the `/wc/v2/` and `/wc/v3/` routes.

This documentation showcases the available HTTP API methods and endpoints to perform valid requests, along with some examples in PHP.

If you spot a typo, an error, have a question, want to provide feedback or extend the documentation, please refer to the [GitHub repository of this documentation](https://github.com/godaddy-wordpress/woocommerce-memberships-rest-api-docs).

