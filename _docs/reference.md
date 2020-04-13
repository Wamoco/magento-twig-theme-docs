---
title: Functions and Filters Reference
permalink: /docs/reference/
---

This list provides an overview of provided functions and filters that are available inside twig templates.

## Functions

### blockExists

**Usage Example**

Checks if a block exists in the current layout.

{% raw %}
    {% if blockExists('page.main.title') %}
      {{ include('partials/page-title.html.twig', {pageTitle: getBlock('page.main.title').getPageHeading }) }}
    {% endif %}
{% endraw %}

### customerData

**Usage Example**

Fetches data from CustomerData like. Data like customer, wishlist or cart can be received there. Compare [Magento Dev Docs](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html).

{% raw %}
    {{ customerData('customer').fullname }}
{% endraw %}

### getActiveFilters

Only useful on category pages. It receives the currently active filters.

**Usage Example**

{% raw %}
    {% if getActiveFilters()|length > 0 %}
      <div class="widget brands {%if filter.getData('swatchData')%}color{%endif%} mb-50">
          <!-- Widget Title 2 -->
          <p class="widget-title2 mb-30">{{'Now Shopping by'|trans}}</p>
          <div class="widget-desc">
            {% for activeFilter in getActiveFilters() %}
              <p>{{ activeFilter.filter.name }}: {{ activeFilter.label}} <a href="{{activeFilter.getRemoveUrl}}">[{{'Remove'|trans}}]</a></p>
            {% endfor %}
          </div>
      </div>
    {% endif %}

{% endraw %}

### getAsset

This is a shortcut for `$this->template->getViewFileUrl("Wamoco_TwigTheme")`, which gives the URL web assets are placed.

**Usage Example**

{% raw %}
    <link rel="stylesheet" href="{{ getAsset('/css/simple-grid.css') }}" async defer>
{% endraw %}

### getBaseUrl

Gets the baseUrl for the current store view. This value needs also be present in JS to make some of the UI components work.

**Usage Example**

{% raw %}
    window.BASE_URL = "{{ getBaseUrl() }}";
{% endraw %}

### getBlock

Receives a block which is defined in the current layout handles. All provided methods can be accessed.

**Usage Example**

{% raw %}
    {{ getBlock('product_list_toolbar').getFirstNum() }}

    {{ getBlock('product.info').getProduct.price|price|raw }}
{% endraw %}

### getCart

Receives cart data of current customer. Make sure to use this only on non-cachable pages.

**Usage Example**

{% raw %}
    {% for item in getCart().items %}
        {{ item.product.name }}
    {% endfor %}
{% endraw %}

### getCustomer

Gets information about the current customer. Make sure to use this only on non-cachable pages.

**Usage Example**

{% raw %}
    <p>{{ getCustomer().firstname }} {{ getCustomer().lastname }}</p>
    <p>{{ getCustomer().email }}</p>
{% endraw %}

### getFilters

Only useful on category pages. Gets a list of available filters including their swatch data.

**Usage Example**

{% raw %}
    {% for filter in getFilters() %}
      <p>{{filter.name}}</p>
      <ul>
        {% for filterItem in filter.items %}
          <li><a href="{{ filterItem.url }}">{{ filterItem.label|raw }}({ {filterItem.count }})</a></li>
        {% endfor %}
      </ul>
    {% endfor %}

{% endraw %}

### getFormKey

Gets the formKey. Usually you would rather render the form block like this: {% raw %}`{{ renderBlock('formkey') }}`{% endraw %}.

**Usage Example**

{% raw %}
    <input type="hidden" name="form_key" value="{{ getFormKey }}">
{% endraw %}

### getHelper

Receives any Helper by its class name.

**Usage Example**

{% raw %}
    <input name="name" id="name" title="{{'Name'|trans}}" value="{{ getHelper('Wamoco\\Theme\\View\\Helper\\Contact').getName }}" class="input-text form-control" type="text" data-validate="{required:true}"/>
{% endraw %}

### getJs

Accessing Magento 2 Assets e.g. JavaScripts. This is equivalent for `getViewFileUrl` in Magento.

**Usage Example**

{% raw %}
    <script type="text/javascript" src="{{getJs('requirejs/require.js')}}"></script>
{% endraw %}

### getProduct

Receives a product object by SKU or ID. If no argument is provided, the current product is returned, e.g. on product detail pages.

**Usage Example**

{% raw %}
    {{ getProduct('24-MB01') }}
{% endraw %}

### getRequest

Gets the current request object.

**Usage Example**

{% raw %}
    {{ getRequestParam().getParam('token') }}
{% endraw %}

### getRequestParam

Gets a request parameter by its name.

**Usage Example**

{% raw %}
    <input type="search" name="q" id="headerSearch" placeholder="{{'Search entire store here...'|trans}}" value="{{ getRequestParam('q')|escape }}">
{% endraw %}

### getUrl

Uses the UrlBuilder of Magento to generate URLs.

**Usage Example**

{% raw %}
    <form method="POST" action="{{ getUrl('contact/index/post') }}">
{% endraw %}

### getViewFileUrl

Accessing Magento 2 Assets e.g. JavaScripts. This is equivalent for `getViewFileUrl` in Magento.

**Usage Example**

{% raw %}
    <script type="text/javascript" src="{{getViewFileUrl('requirejs/require.js')}}"></script>
{% endraw %}

### renderBlock

Render any block in the current layout by its name.

**Usage Example**

{% raw %}
    {{ renderBlock('customer.customer.data') }}
{% endraw %}

### renderCmsBlock

Fetches a CMS block by its name from backend and renders it.

**Usage Example**

{% raw %}
    {{ renderCmsBlock('home-page-block') }}
{% endraw %}

### renderElement

Renderes a layout element within Magento and returns the html. This is useful to render entire parts and place them somewhere.

**Usage Example**

{% raw %}
    {{ renderElement('sidebar.main') }}
{% endraw %}

### Include a partial

Actually this is a built-in twig feature, but helpful for reference.

**Usage Example**

{% raw %}
    {% include 'pages/cms/shop/product.html.twig' with {'product': getProduct('24-MB01')} %}
{% endraw %}


## Filters

### formatDate

**Usage Example**

Formats a date according to the locale settings.

{% raw %}
    <td>{{order.getCreatedAt|formatDate}}</td>
{% endraw %}

### escapeHtmlAttr

**Usage Example**

{% raw %}

{% endraw %}

### escapeUrl

**Usage Example**

{% raw %}

{% endraw %}

### price

Formats a price according to the currency settings of the current store view.

**Usage Example**

{% raw %}
    {{ getBlock('product.info').getProduct.price|price|raw }}
{% endraw %}

### trans

Uses the built-in translation function to translate strings.

**Usage Example**

{% raw %}
    {{ 'Country'|trans }}
{% endraw %}

