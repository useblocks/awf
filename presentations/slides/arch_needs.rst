Architecture Needs
------------------
Need objects representing architecture elements

An Arch Need 1/2
~~~~~~~~~~~~~~~~
Normal need, with ``needuml``

.. arch_comp:: Component Blue
   :id: COMP_BLUE
   :status: open

   This is component Blue!

   .. needuml::

      card "Interface A" as int_a
      card "Function X" as func_x

      int_a --> func_x

   For sure it's awesome.

An Arch Need 2/2
~~~~~~~~~~~~~~~~

.. code-block:: rst

    .. arch_comp:: Component Blue
       :id: COMP_BLUE
       :status: open

       This is component Blue!

       .. needuml::

          card "Interface A" as int_a
          card "Function X" as func_x

          int_a --> func_x

       For sure it's awesome.

First ``needuml`` is used as "uml-like" representation

Reusing Arch needs
~~~~~~~~~~~~~~~~~~

.. code-block:: rst

   .. needuml::

      {{need('COMP_BLUE')}}
      {{uml('COMP_BLUE')}}

.. needuml::

   {{need('COMP_BLUE')}}
   {{uml('COMP_BLUE')}}

Chaining Arch needs 1/4
~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: rst


   .. arch_sys:: System Foo
      :id: SYS_FOO
      :status: open

      This is system **Foo**

      .. needuml::

         node "System FOO" as foo {
          {{uml("COMP_BLUE")}}
         }

         circle "Interface Y" as int_y

         int_y -> int_a

Chaining Arch needs 2/4
~~~~~~~~~~~~~~~~~~~~~~~

.. arch_sys:: System Foo
   :id: SYS_FOO
   :status: open

   This is system **Foo**

   .. needuml::

      node "System FOO" as foo {
        {{uml("COMP_BLUE")}}
      }

      circle "Interface Y" as int_y

      int_y -> int_a

Chaining Arch needs 3/4
~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: rst

    .. arch_sys:: Product 42
       :id: PROD_42
       :status: open

       .. needuml::

          {{uml("SYS_FOO")}}
          node "System Bar" as bar

          foo --> bar

Chaining Arch needs 3/4
~~~~~~~~~~~~~~~~~~~~~~~

.. arch_sys:: Product 42
   :id: PROD_42
   :status: open

   .. needuml::

      {{uml("SYS_FOO")}}
      node "System Bar" as bar

      foo --> bar