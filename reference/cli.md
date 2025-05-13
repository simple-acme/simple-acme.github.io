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

# Main
These are the main arguments used to control the programs unattended operation.
{% assign main = site.data.arguments | where: "name", "Main" | first %}
{% include arguments-group.html arguments = main.arguments %}

# Account
These arguments are used to create a new account for the ACME client during an initial automated run.
{% assign account = site.data.arguments | where: "name", "Account" | first %}
{% include arguments-group.html arguments = account.arguments %}


{% for pt in site.data.types %}
  {% assign arguments = site.data.arguments | where: "plugintype", pt.type | sort_natural: "name" %}
  {% if arguments.size == 0 %}
    {% continue %}
  {% endif %}
  <h2>{{ pt.title }} </h2>
  {% for argument in arguments %}
  <h3>➡️ {{ argument.name }} </h3>
    {% assign plugin = site.data.plugins | where: "id", argument.pluginid | first %}
    {% if plugin.external %}
 <div class="callout-block callout-block-warning pb-1 mt-3">
    <div class="content">
        <p>These arguments are for a plugin that requires an additional {% include plugin-link.html plugin=plugin title='download' %}.</p>
    </div>
 </div>
    {% endif %}
<p>
    {% unless argument.condition == nil %}
<code>[{{ argument.condition }}]</code>
    {% endunless %}
    ({% include plugin-link.html plugin=plugin title='documentation' %})
</p>
 {% include arguments-group.html arguments = argument.arguments %}
  {% endfor %}
{% endfor %}