{%- set max_exp_items_to_show = 3 -%}

# {{ full_name }}

{% for key, value in contact_details.items() %}
{{- key }}: [{{ value }}]({{ value }}){% if not loop.last %} \{% endif %}
{% endfor %}

## Summary

{{ summary }}

## Key Skills
{% for bullet_point in key_skills %}
 * {{ bullet_point -}}
{% endfor %}

## Experience

{% for item in experience %}
{%- if loop.index > max_exp_items_to_show %}
{%- if loop.index == max_exp_items_to_show + 1 %}
### Earlier Experience
_Various locations_
{% endif %}
 * {{ item.title }}, [{{ item.company_name }}]({{ item.company_url }}) _({{ item.dates }})_
{%- else %}
### {{ item.title }}, [{{ item.company_name }}]({{ item.company_url }})
_{{ item.dates }}, {{ item.location }}_
{% for bullet_point in item.bullet_points %}
 * {{ bullet_point -}}
{% endfor %}
  
_{{ item.used_technologies|join(", ") }}_
{% endif -%}
{% endfor %}

## Qualifications and Training
{% for item in qualifications %}
{%- if item.url is defined and item.url|length %}
 * [{{ item.title }}]({{ item.url }})
{%- else %}
 * {{ item.title }}
{%- endif -%}
{% endfor %}
{%- for item in certificates -%}
{% if item.url is defined and item.url|length %}
 * [{{ item.title }}]({{ item.url }})
{%- else %}
 * {{ item.title }}
{%- endif -%}
{% endfor %}
{%- for item in internal_training -%}
{% if item.url is defined and item.url|length %}
 * [{{ item.title }}]({{ item.url }})
{%- else %}
 * {{ item.title }}
{%- endif -%}
{% endfor %}
