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

‑‑‑‑

{% for argument_group in site.data.arguments %}
    {% assign groupname = argument_group[0] | strip %}
<h2>{{ groupname }} </h2>
        {% for argument_subgroup in site.data.arguments[groupname] %}
            {% assign subgroupname = argument_subgroup[0] | strip %}
{% unless groupname == subgroupname %}<h3>{{ subgroupname }}</h3>{% endunless %}
{% unless argument_subgroup[1].condition == "" %}
<p><code>[{{ argument_subgroup[1].condition }}]</code></p>
{% endunless %}
<div class="table-responsive my-4 me-5 pe-5">
  <table class="table table-striped">
    {% for argument in argument_subgroup[1].arguments %}
      {% include arguments-detail.html argument=argument %}
    {% endfor %}
  </table>
</div>
        {% endfor %}
{% endfor %}