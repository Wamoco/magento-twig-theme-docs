---
title: Variables and Functions Reference
permalink: /docs/reference/
---

## Base variables

| Variable             | Description           | Example  |
| :------------------- | :------------------------------------------- | :----- |
| base.assetPath       | Url to assets                                | http://magento2.local/pub/static/version1585215959/frontend/Wamoco/karl/de_DE |
| base.baseViewUrl     | Url to Twig Module for accessing templates   | http://magento2.local/pub/static/version1585215959/frontend/Wamoco/karl/de_DE/Wamoco_TwigTheme |
| base.baseUrl         | Magento 2 Base Url                           | http://magento2.local/ |

**Usage Example**

{% raw %}
    {{ base.assetPath }}
{% endraw %}

## GetJs

Accessing Magento 2 Assets e.g. JavaScripts. This is equivalent for `getViewFileUrl` in Magento.

**Usage Example**

{% raw %}
    <script type="text/javascript" src="{{getJs('requirejs/require.js')}}"></script>
{% endraw %}

## GetProduct

Receives a product object by SKU or ID.

**Usage Example**

{% raw %}
    {{ getProduct('24-MB01') }}
{% endraw %}

## GetBlock

Receives a block which is defined in the current layout handles. All provided methods can be accessed.

**Usage Example**

{% raw %}
    {{ getBlock('product_list_toolbar').getFirstNum() }}

    {{ getBlock('product.info').getProduct.price|price|raw }}
{% endraw %}

## RenderElement

Renderes a layout element within Magento and returns the html. This is useful to render entire parts and place them somewhere.

**Usage Example**

{% raw %}
    {{ renderElement('sidebar.main') }}
{% endraw %}

## trans

Uses the built-in translation function to translate strings.

**Usage Example**

{% raw %}
    {{ 'Country'|trans }}
{% endraw %}

## Price

Formats a price according to the currency settings of the current store view.

**Usage Example**

{% raw %}
    {{ getBlock('product.info').getProduct.price|price|raw }}
{% endraw %}

## Include Partial

Actually this is a built-in twig feature, but helpful for reference.

**Usage Example**

{% raw %}
    {% include 'pages/cms/shop/product.html.twig' with {'product': getProduct('24-MB01')} %}
{% endraw %}

