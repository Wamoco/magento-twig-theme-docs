---
title: Scenario Development
permalink: /docs/scenarios/
---

## Develop a custom scenario

Some more insights on how to develop a scenario.

```ruby
title "Add to cart"
description "Added items should appear on cart"

define_option 'product_path', :string, default: '/', description: "Path to product which should be put into cart", required: true
define_option 'add_to_cart_button_label', :string, default: 'In den Warenkorb', description: "Label of the add to cart button", required: true
define_option 'cart_path', :string, default: '/checkout/cart', description: "Path for cart", required: true
define_option 'product_name', :string, description: "Expected product name", required: true
define_option 'product_sku', :string, description: "Expected product sku", required: true
define_option 'cookies', :string, description: "Cookie value, e.g. to bypass GDPR protection if required"

define_interval '0 */4 * * *', :limited
define_option 'severity', :string, default: 'critical', description: "Severity for issues generated by this scenario", required: true

scenario %{
  Given I am on "%product_path%"
  And I click on "%add_to_cart_button_label%"
  When I am on "%cart_path%"
  Then I should see text "%product_name%"
  And I should see text "%product_sku%"
}
```