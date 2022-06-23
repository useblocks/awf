needuml
-------
Like ``uml``-directive, but on steroid

Basic behavior
~~~~~~~~~~~~~~

Behaves like PlantUML directive.

.. code-block:: rst

   .. needuml::

      card "Basic element"

.. needuml::

      card "Basic element"

Programmable
~~~~~~~~~~~~
Thanks to Jinja


.. code-block:: rst

   .. needuml::

      {% for title in ["Req A", "Spec B"]%}
      card "{{title}}"
      {% endfor %}

.. needuml::

      {% for title in ["Req A", "Spec B"]%}
      card "{{title}}"
      {% endfor %}



Data access
~~~~~~~~~~~
Has access to all Need data

.. req:: My requirement
   :id: REQ_01

.. code-block:: rst

   .. needuml::

      card "{{needs['REQ_01'].title }}"

.. needuml::

      card "{{needs['REQ_01'].title }}"

Big brother
~~~~~~~~~~~
Like ``needflow``, but full control

.. code-block:: rst

   .. needuml::

      {{need('REQ_01')}}

.. needuml::

      {{need('REQ_01')}}

.. code-block:: rst

   .. needuml::

      {% for need in needs %}
        {% if need.type == "req" %}
            {{need(need.id)}}
        {% endif %}
      {% endfor %}

Freedom
~~~~~~~
Combine manual and automatic data

.. code-block:: rst

   .. needuml::

      card "Component X" as comp_x

      node "Awesome package" {
      {% for need in needs.values() %}
        {% if need.type == "req" %}
            card "{{need.title}}" as {{need.id}}
            {{need.id}} --> comp_x
        {% endif %}
      {% endfor %}
      }

.. needuml::

   card "Component X" as comp_x

   node "Awesome package" {
   {% for obj in needs.values() %}
     {% if obj.type == "req" %}
         {{need(obj.id)}}
         {{obj.id}} -> comp_x
     {% endif %}
   {% endfor %}
   }


