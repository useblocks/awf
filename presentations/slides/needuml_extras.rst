Needuml Extras
--------------
There is one more thing...

Model parameters 1/4
~~~~~~~~~~~~~~~~~~~~

.. code-block:: rst

    .. arch_comp:: Component ???
       :id: COMP_VAR

       .. needuml::

          {% if variant == "A" %}
          card "Interface A" as int
          {% elif variant == "B" %}
          card "Interface B" as int
          {% else %}
          card "Interface X" as int
          {% endif %}

          card "Function {{name}}" as func

          int --> func

Model parameters 1/4
~~~~~~~~~~~~~~~~~~~~

.. arch_comp:: Component ???
   :id: COMP_VAR

   .. needuml::

      {% if variant == "A" %}
      card "Interface A" as int
      {% elif variant == "B" %}
      card "Interface B" as int
      {% else %}
      card "Interface X" as int
      {% endif %}

      card "Function {{name}}" as func

      int --> func

Model parameters 3/4
~~~~~~~~~~~~~~~~~~~~

.. code-block:: rst

    .. arch_sys:: System B
       :id: SYS_B

       This is system **B**

       .. needuml::

          node "System B" as sys_b {
            {{uml("COMP_VAR", variant="B", name="SYS_B")}}
          }

          circle "Interface Y" as int_y
          int_y -> int

Model parameters 4/4
~~~~~~~~~~~~~~~~~~~~

.. arch_sys:: System B
   :id: SYS_B

   This is system **B**

   .. needuml::

      node "System B" as sys_b {
        {{uml("COMP_VAR", variant="B", name="SYS_B")}}
      }

      circle "Interface Y" as int_y
      int_y -> int