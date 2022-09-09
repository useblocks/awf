Needuml Extras
--------------
There is more...



needuml - save
~~~~~~~~~~~~~~
Store the final PlantUML code in a file.

.. code-block::

   .. needuml::
      :save: /arch/system_x.puml

      {{ flow("COMP_A") }}
      {{ flow("COMP_B") }}

      comp_a --> comp_b

`Docs: needuml - save <https://sphinx-needs.readthedocs.io/en/latest/directives/needuml.html#save>`__

needuml - debug
~~~~~~~~~~~~~~~


.. needuml::
   :debug:

   {{ flow("REQ_01") }}

   card "charlie" as ch
   REQ_01 --> ch

`Docs: needuml - debug <https://sphinx-needs.readthedocs.io/en/latest/directives/needuml.html#debug>`__


needuml - filter
~~~~~~~~~~~~~~~~
Filter by filter-strings.

.. code-block::

   .. arch_comp:: My Component
      :id: COMP_MY

      .. needuml::

         {% for need in filter("type=='interface' and status!='open'") %}
            {{flow(need.id)}}
         {% endfor %}

`Docs: needuml - filter <https://sphinx-needs.readthedocs.io/en/latest/directives/needuml.html#filter-filter-string>`__

