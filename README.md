# WooCommerce Memberships REST API documentation

Official repository for the documentation of the [WooCommerce Memberships](https://woocommerce.com/products/woocommerce-memberships/) REST API.

> If you are looking for the general **plugin documentation**, [please follow this link](https://docs.woocommerce.com/document/woocommerce-memberships/).

## Contributing

You can contribute to this documentation by:

* [Opening an issue](https://github.com/skyverge/woocommerce-memberships-rest-api-docs/issues/new) to report a problem or information missing, etc.
* Opening a pull request to extend the documentation.

> Please **do not submit feature requests or support requests for the REST API** here. You can use the [WooIdeas board](http://ideas.woocommerce.com/forums/133476-woocommerce?category_id=125014) or [Contact SkyVerge support](https://www.skyverge.com/support/).

## Updating pages

This project uses [Slate](https://github.com/lord/slate) for building the documentation pages.

Follow [Slate readme](https://github.com/lord/slate/blob/master/README.md) and [wiki](https://github.com/lord/slate/wiki) for instructions on how to edit files and make changes.

## Deploying an update 

To install locally use:

```shell
bundle install
```

> **Important note:** if you run into `bundle install` errors, you may need to install `ruby-devel` and install the related gems again to build native extensions.  

Then, to test changes locally run:

```shell
bundle exec middleman server
```

Finally, after pushing changes and you are ready to deploy use the script:

```shell
bash deploy.sh
```
