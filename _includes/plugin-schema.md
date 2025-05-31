{% assign plugins = site.data.plugins | where_exp: "plugin", "plugin.type contains include.type" | sort_natural: "name" %}
{% if plugins.size > 0 %}
, "allOf": [			
{% for plugin in plugins %}
    {
        "if": {
            "properties": {
                "Plugin": {
                    "const": "{{ plugin.id }}",
                    "$comment": "{{ plugin.name }}"
                }
            }
        },
        "then": {
            {% if plugin.schema %}
                "$ref": "./{{ plugin.type }}/{{ plugin.trigger }}.json"
            {% else %}
                "additionalProperties": false,
                "properties": {
                    {% include setting-schema.md object=plugin.options %}
                }
            {% endif %}
        }
    }{% unless forloop.last %},{% endunless %}
{% endfor %}
]
{% endif %}