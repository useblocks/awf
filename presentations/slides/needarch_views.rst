Needarch views
--------------
Different views for the same need


Needarch view 1/5
~~~~~~~~~~~~~~~~~


.. code-block:: rst

    .. arch_comp:: Component X
       :id: COMP_X

       Sequence diagram

       .. needarch::
          :key: sequence

          Foo --> Bar: Hello

       Flow chart

       .. needarch::

          card Foo


Needarch view 2/5
~~~~~~~~~~~~~~~~~

.. arch_comp:: Component X
   :id: COMP_X

   Sequence diagram

   .. needarch::
      :key: sequence

      Foo --> Bar: Hello

   Flow chart

   .. needarch::

      card Foo
      database Bar
      Foo --> Bar: Hello


Needarch view 3/5
~~~~~~~~~~~~~~~~~

.. code-block:: rst

   .. arch_sys:: System X
      :id: SYS_X

      Sequence diagram

      .. needarch::

         {{uml('COMP_X', 'sequence')}}

         Bar --> Foo: Hello again


Needarch view 4/5
~~~~~~~~~~~~~~~~~

.. arch_sys:: System X
   :id: SYS_X

   Sequence diagram

   .. needarch::

      {{uml('COMP_X', 'sequence')}}

      Bar --> Foo: Hello again


Needarch view 5/5
~~~~~~~~~~~~~~~~~

.. code-block:: rst

   {{uml('COMP_X')}}

.. arch_sys:: System X-2
   :id: SYS_X-2

   Sequence diagram

   .. needarch::

      {{uml('COMP_X')}}

      Bar --> Foo: Hello again