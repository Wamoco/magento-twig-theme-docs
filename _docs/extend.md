---
title: Adding own Functions and Filters
permalink: /docs/extend/
---

## Defining custom filters and functions

Example `di.xml`:

    <type name="Wamoco\TwigTheme\Engine\Twig">
        <arguments>
            <argument name="filters" xsi:type="array">
                <item name="price" xsi:type="string">Wamoco\TwigTheme\View\Filters\Price</item>
            </argument>
            <argument name="functions" xsi:type="array">
                <item name="renderElement" xsi:type="string">Wamoco\TwigTheme\View\Functions\RenderElement</item>
            </argument>
        </arguments>
    </type>


Example `Price.php`:


    <?php
    namespace Wamoco\TwigTheme\View\Filters;

    class Price extends \Twig\TwigFilter
    {
        /**
         * @var \Magento\Framework\Pricing\PriceCurrencyInterface
         */
        protected $priceCurrency;

        /**
         * __construct
         *
         * @param \Magento\Framework\Pricing\PriceCurrencyInterface $priceCurrency
         * @param mixed $name
         */
        public function __construct (
            \Magento\Framework\Pricing\PriceCurrencyInterface $priceCurrency,
            $name
        ) {
            parent::__construct($name);
            $this->priceCurrency = $priceCurrency;
        }

        public function getCallable()
        {
            return function($string) {
                return $this->priceCurrency->convertAndFormat($string, false);
            };
        }
    }

