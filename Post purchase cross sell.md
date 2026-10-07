{% set purchased_category =
  person|lookup:'Last Purchased Category'|default:""
%}

{% set first_name =
  person.first_name|default:"there"
%}


Hi {{ first_name }},

Thank you for your recent purchase.


{% if purchased_category == "Shoes" %}

  Since you purchased shoes, you might also like
  our latest accessories collection.

{% elif purchased_category == "Skincare" %}

  Complete your skincare routine with our recommended
  complementary products.

{% elif purchased_category == "Electronics" %}

  Protect your new purchase with our range of
  compatible accessories.

{% else %}

  We found some products we think you'll love.

{% endif %}