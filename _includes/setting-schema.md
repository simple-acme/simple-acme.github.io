{% for setting in include.object %}
    {% assign name = setting[0] | trim %}
    {% assign value = setting[1] %}
    {% if name == 'Plugin' %}
        {% continue %}
    {% endif %}
    {% unless forloop.first %},{% endunless %}
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
            {%if value.type == "string[]" %}
                "type": "array",
                "items": {
                    "type": "string"
                },
            {%elsif value.type == "number[]" %}
                "type": "array",
                "items": {
                    "type": "number"
                },
            {% else %}
                "type": ["{{ value.type }}", "null"],
            {% endif %}
            "$comment": "{{ value.description | replace: '"', '\"' | strip_newlines }}"
        {% endif %}
    }
{% endfor %}