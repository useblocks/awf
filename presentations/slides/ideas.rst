Further ideas
-------------

Automatic Connectors
~~~~~~~~~~~~~~~~~~~~

Connect PlantUML objects by there names. E.g comp_a_1.3 --> comb_b_1.3.


"Normal" objects 1/2
~~~~~~~~~~~~~~~~~~~~

.. code-block::

   .. arch_sys:: System X
      :id: SYS_X
      :status: open
      :tags: system, x

      {{COMP_USER}}
      {{COMP_SHOP}}
      {{REQ_001}}

      Order::user o-- User::id
      REQ_001 ..> User

"Normal" objects 2/2
~~~~~~~~~~~~~~~~~~~~

.. arch_sys:: System Y
  :id: SYS_Y
  :status: open
  :tags: system, y

  .. uml::

       @startuml
           allow_mixing

           '' code from COMP_USER
           !include plantuml/comp_a.puml

           '' code from COMP_ORDER
           !include plantuml/comp_b.puml

           node "My Requirement" as REQ_001 #DCB239

           '' code from need_arch
           Order::user o-- User::id
           REQ_001 ..> User

          @enduml

Container
~~~~~~~~~

.. arch_sys:: System Z
  :id: SYS_Z

  .. uml::

       @startuml
           allow_mixing

           '' code from COMP_USER

           package COMP_USER <<Rectangle>> {

               !include plantuml/comp_a.puml
           }

           '' code from COMP_ORDER

           package COMP_ORDER <<Rectangle>> {
               !include plantuml/comp_b.puml
           }

           '' code from need_arch
           Order::user o-left- User::id

          @enduml

.. container:: small

   | Activated by setting need-option ``show_container``.
   | Maybe also with selected meta-data.


Variant Management
~~~~~~~~~~~~~~~~~~

.. code-block::

   .. arch_sys:: System X
      :id: SYS_X
      :status: open
      :tags: system, x

      {% if "variant_b" in sphinx.tags %}

        {{COMP_USER_B}}

      {% else %}

        {{COMP_USER_COMMON}}

      {% endif %}

      {{COMP_SHOP}}

      Order::user --> User::id

Supported via `Jinja <https://jinja.palletsprojects.com/en>`_.
Can control integration but also PlantUML diagram content

Spinoff: needs-uml combination
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block::

   .. needsuml::

        card "{{ needs["REQ_001"].title}}" as parent

        {% for need in needs["REQ_001"].links %}

            card {{ need.title}} as child_{{ loop.index }}
            parent --> child_{{ loop.index }}

        {% endfor %}

Adds `Jinja <https://jinja.palletsprojects.com/en>`_ support around PlantUML-directive.