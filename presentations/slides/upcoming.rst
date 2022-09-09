Upcoming
--------

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
