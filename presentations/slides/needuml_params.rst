Model parameters
----------------
One definition for custom use cases.


Model parameters 1/4
~~~~~~~~~~~~~~~~~~~~

.. code-block:: rst

    .. arch_comp:: Component ???
       :id: COMP_VAR

       .. needarch::

          {% if variant == "A" %}
          card "Interface A" as int
          {% elif variant == "B" %}
          card "Interface B" as int
          {% else %}
          card "Interface X" as int
          {% endif %}

          card "Function {{name}}" as func

          int --> func

Model parameters 2/4
~~~~~~~~~~~~~~~~~~~~

.. arch_comp:: Component ???
   :id: COMP_VAR

   .. needarch::

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

       .. needarch::

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

   .. needarch::

      node "System B" as sys_b {
        {{uml("COMP_VAR", variant="B", name="SYS_B")}}
      }

      circle "Interface Y" as int_y
      int_y -> int

Documenting Model parameters 1/2
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: rst

    .. arch_comp:: Component ???
       :id: COMP_VAR2

       .. needarch::

          card "Function {{name}}" as func

          {% if variant == "A" %}
          card "Interface A.1" as int
          card "Interface A.2" as int_2
          int_2 --> func
          {% elif variant == "B" %}
          card "Interface B" as int
          {% else %}
          card "Interface X" as int
          {% endif %}

          int -> func

        **For Variant A**:

       .. needuml::

          {{uml('COMP_VAR', variant="A", name="Customer_A")}}


       **For Variant B**:

       .. needuml::

          {{uml('COMP_VAR', variant="B", name="Customer_B")}}

Documenting Model parameters 2/2
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. arch_comp:: Component ???
   :id: COMP_VAR2

   .. needarch::

      card "Function {{name}}" as func

      {% if variant == "A" %}
      card "Interface A.1" as int
      card "Interface A.2" as int_2
      int_2 --> func
      {% elif variant == "B" %}
      card "Interface B" as int
      {% else %}
      card "Interface X" as int
      {% endif %}

      int -> func

   **For Variant A**:

   .. needuml::

      {{uml('COMP_VAR2', variant="A", name="Customer_A")}}


   **For Variant B**:

   .. needuml::

      {{uml('COMP_VAR2', variant="B", name="Customer_B")}}