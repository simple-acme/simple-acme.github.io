{% assign plugins = site.data.plugins | where_exp: "plugin", "plugin.type contains include.type" | sort_natural: "name" %}
{% assign plugins = plugins | where: "schema", true %}
{% if plugins.size > 0 %}
, "allOf": [			
{% for plugin in plugins %}
    {
        "if": {
            "properties": {
                "Plugin": {
                    "const": "{{ plugin.id }}"
                }
            }
        },
        "then": {
            "$ref": "./{{ plugin.type }}/{{ plugin.trigger }}.json"
        }
    }
    {% unless forloop.last %},{% endunless %}
{% endfor %}
]
{% endif %}