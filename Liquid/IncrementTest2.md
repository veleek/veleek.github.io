---
layout: default
---

# Liquid Increment Variable Test - Page 2

This page is testing using [liquid `increment` variables](https://help.shopify.com/themes/liquid/tags/variable-tags#increment).

{% raw %}
    * Increment Variable Before: {{ incrementVariable }} 
    * {% increment incrementVariable %}
    * {% increment incrementVariable %}
    * Increment Variable After: {{ incrementVariable }}
{% endraw %}

* Increment Variable Before: {{ incrementVariable }} 
* {% increment incrementVariable %}
* {% increment incrementVariable %}
* Increment Variable After: {{ incrementVariable }}

See also the [IncrementTest1](IncrementTest1.md) page which uses the identical variable name.
