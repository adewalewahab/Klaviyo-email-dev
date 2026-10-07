{# =========================================================
   KLAVIYO CUSTOMER PROFILE PERSONALIZATION
   ========================================================= #}

{% set first_name = person.first_name|default:"there" %}
{% set email = person.email|default:"" %}
{% set city = person|lookup:'City'|default:"" %}
{% set customer_type = person|lookup:'Customer Type'|default:"customer" %}
{% set loyalty_tier = person|lookup:'Loyalty Tier'|default:"Member" %}

{% if first_name != "there" %}

  Hi {{ first_name }},

{% else %}

  Hello,

{% endif %}


{% if customer_type == "VIP" %}

  As one of our VIP customers, we have something special
  selected specifically for you.

{% elsif loyalty_tier == "Gold" %}

  As a Gold member, you have access to exclusive benefits.

{% else %}

  We have something new we think you'll love.

{% endif %}


{% if city != "" %}

  We're bringing some exciting offers to customers in
  {{ city }}.

{% endif %}