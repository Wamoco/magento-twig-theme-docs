---
title: Route Configuration
permalink: /docs/configuration/
---

Every route/page that should be rendered using Twig needs to be registered first. Therefore an entry in `config.xml` needs to be created. Currently three different kinds are available, which are described in the following.

## Controllers

Any Magento Controller can have a twig template attached. In this case the controller does not do the usual layout and template rendering. Instead it renders the given Twig template which is located in the base path `Wamoco_TwigTheme/web/templates` per convention.

    <item name="Magento\Catalog\Controller\Product\View">pages/catalog/product.html.twig</item>

## Routes

To fetch routes that do not hit a controller directly a route matching can be configured. This is especially helpful for prototyping or static content pages.

     <item name="/datenschutz">pages/custom/datenschutz.html.twig</item>

## Rewrites

There is also a rewrite mechanism included. Of course Magento features url rewrites out of the box, but for frontend porting and prototyping it can be very helpful to create static rewrites quick and easy like this:

      <item name="/kontakt">contact</item>


## Complete Example

Here we have a complete example of a working `config.xml`:

    <theme>
        <controllers>
            <item name="Magento\Catalog\Controller\Product\View">pages/catalog/product.html.twig</item>
            <item name="Magento\Catalog\Controller\Category\View">pages/catalog/category.html.twig</item>
            <item name="Magento\CatalogSearch\Controller\Result\Index">pages/catalog/search.html.twig</item>
            <item name="Magento\Checkout\Controller\Cart\Index">pages/checkout/cart.html.twig</item>
        </controllers>
        <routes>
            <item name="/datenschutz">pages/custom/datenschutz.html.twig</item>
        </routes>
        <rewrites>
            <item name="/kontakt">contact</item>
        </rewrites>
    </theme>

