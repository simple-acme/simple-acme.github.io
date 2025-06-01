{% assign plugins = site.data.plugins | where_exp: "plugin", "plugin.type contains include.type" | sort_natural: "name" %}
{% for plugin in plugins %}
    {
        {% if plugin.schema %}
            "properties": {
                "Plugin": {
                    "const": "{{ plugin.id }}",
                    "$comment": "{{ plugin.name }}"
                }
            },
            "$ref": "/schema/{{ plugin.type }}/{{ plugin.trigger }}.json"
        {% else %}
            "additionalProperties": false,
            "properties": {
                "Plugin": {
                    "const": "{{ plugin.id }}",
                    "$comment": "{{ plugin.name }}"
                }
                {% for setting in plugin.options %}
                    {% assign name = setting[0] | trim %}
                    {% if name == 'Plugin' %}
                        {% continue %}
                    {% endif %}
                    ,{% break %}
                {% endfor %}
                {% include setting-schema.md object=plugin.options %}
            }
        {% endif %}
    }{% unless forloop.last %},{% endunless %}
{% endfor %}