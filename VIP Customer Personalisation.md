{% set lifetime_value =
  person|lookup:'Lifetime Value'|default:0
%}

{% set loyalty_tier =
  person|lookup:'Loyalty Tier'|default:"Standard"
%}

{% set first_name =
  person.first_name|default:"there"
%}


{% if lifetime_value >= 1000000 %}

  {% set segment = "VIP" %}
  {% set discount = 30 %}

{% elif lifetime_value >= 500000 %}

  {% set segment = "Premium" %}
  {% set discount = 20 %}

{% elif lifetime_value >= 100000 %}

  {% set segment = "Valued" %}
  {% set discount = 15 %}

{% else %}

  {% set segment = "Standard" %}
  {% set discount = 10 %}

{% endif %}


Hi {{ first_name }},

{% if segment == "VIP" %}

  As a VIP customer, you've unlocked an exclusive
  {{ discount }}% offer.

{% elsif segment == "Premium" %}

  Thanks for being one of our premium customers.

  Enjoy {{ discount }}% off your next purchase.

{% else %}

  Here's {{ discount }}% off your next purchase.

{% endif %}