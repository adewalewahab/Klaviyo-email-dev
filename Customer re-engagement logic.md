{% set engagement_score =
  person|lookup:'Engagement Score'|default:0
%}

{% set first_name =
  person.first_name|default:"there"
%}


{% if engagement_score >= 80 %}

  {% set message_type = "active" %}

{% elif engagement_score >= 50 %}

  {% set message_type = "moderate" %}

{% elif engagement_score >= 20 %}

  {% set message_type = "low" %}

{% else %}

  {% set message_type = "inactive" %}

{% endif %}


{% if message_type == "active" %}

  Hi {{ first_name }},

  You're one of our most engaged customers.
  Here's what's new.

{% elif message_type == "moderate" %}

  Hi {{ first_name }},

  We thought you might be interested in what's
  happening right now.

{% elif message_type == "low" %}

  Hi {{ first_name }},

  It's been a little while.

  Here's something we think you'll enjoy.

{% else %}

  Hi {{ first_name }},

  We miss you.

  Here's a special reason to come back.

{% endif %}