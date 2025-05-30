{% for setting in include.object %}
    {% assign name = setting[0] | trim %}
    {% assign value = setting[1] %}
    "{{ name }}": {
        {% assign object = 1 %}
        {% for sub in value %}
            {% if sub[0] == 'type' %}
                {% assign object = 0 %}
            {% endif %}
        {% endfor %}
        {% if object == 1 %}
        "type": "object",
        "additionalProperties": false,
        "properties": {
            {% include setting-schema.md object=value %}
        }
        {% else %}
            {%if value.type != "string[]" %}
                "type": ["{{ value.type }}", "null"],
            {% else %}
                "type": "array",
                "items": {
                    "type": "string"
                },
            {% endif %}
            {% assign double_quote = '"' %}
            {% assign escaped_double_quote = '\"' %}
            "$comment": "{{ value.description | replace: double_quote, escaped_double_quote }}"
        {% endif %}
    }{% unless forloop.last %},{% endunless %}
{% endfor %}