---
---
# Command line arguments
Here are all the command line arguments the program accepts.

#### Notes
- Make sure that you are familiar with the basics of [renewal management](/manual/renewal-management) 
  before proceeding with unattended use.
- Arguments documented as such: `‑‑foo [‑‑bar baz|qux]` mean that `‑‑foo` is only 
applicable when `‑‑bar` is set to `baz` or `qux`.
- Arguments that start with a `-` should be **double** escaped to be properly parsed. 
For example if your literal value for `‑‑key` needs to be `-foo` then typing `‑‑key "-foo"` 
will fail. Instead you need to type `‑‑key "\"-foo\""`.

{% for argument_group in site.data.arguments %}
    {% assign groupname = argument_group[0] | strip %}
<h2>{{ groupname }} </h2>
        {% for argument_subgroup in site.data.arguments[groupname] %}
            {% assign subgroupname = argument_subgroup[0] | strip %}
{% unless groupname == subgroupname %}<h3>{{ subgroupname }}</h3>{% endunless %}
{% unless argument_subgroup[1].plugin == nil %}
  {% assign type = argument_subgroup[1].plugin.type | strip %}
  {% assign subtype = argument_subgroup[1].plugin.subtype | strip %}
  {% if type == 'validation' %}
    {% assign plugins = site.data.plugins[type][subtype] %}
  {% else %}
    {% assign plugins = site.data.plugins[type] %}
  {% endif %}
  {% assign plugin = plugins | where: "id", argument_subgroup[1].plugin.id | first %}
  {% if plugin.external %}
  <div class="callout-block callout-block-warning pb-1 mt-3">
      <div class="content">
          <p>These arguments are for a plugin that requires an additional download.</p>
      </div>
  </div>
  {% endif %}
  <p></p>
{% endunless %}
<p>
{% unless argument_subgroup[1].condition == nil %}
  <code>[{{ argument_subgroup[1].condition }}]</code>
{% endunless %}
{% unless plugin == nil %}
  ({% include plugin-link.html plugin=plugin type=type subtype=subtype title='documentation' %})
{% endunless %}
</p>
<div class="table-responsive my-4 me-5 pe-5">
  <table class="table table-striped">
    {% for argument in argument_subgroup[1].arguments %}
      {% include arguments-detail.html argument=argument %}
    {% endfor %}
  </table>
</div>
        {% endfor %}
{% endfor %}