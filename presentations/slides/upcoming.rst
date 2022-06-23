Upcoming
--------

needuml - save
~~~~~~~~~~~~~~
Store the final PlantUML code in a file.

.. code-block::

   .. needuml::
      :save: /arch/system_x.puml

      {{ uml("COMP_A") }}
      {{ uml("COMP_B") }}

      comp_a --> comp_b


needuml - filter
~~~~~~~~~~~~~~~~
Filter by filter-strings.

.. code-block::

   .. arch_comp:: My Component
      :id: COMP_MY

      .. needuml::

         {% for need in filter("type=='interface' and status!='open'") %}
            {{uml(need.id)}}
         {% endfor %}


needuml - import
~~~~~~~~~~~~~~~~
Automatically use ``uml()`` for all links in given option.

.. code-block::

   .. arch_sys:: My System
      :id: SYS_MY
      :uses: COMP_A, COMP_B, COMP_X

      .. needuml::

         node "My System" as sys {
            {{import("uses")}}
         }
