Integrate elements
------------------

Upper Arch elements
~~~~~~~~~~~~~~~~~~~

.. code-block::

   .. arch_sys:: System X
      :id: SYS_X
      :status: open
      :tags: system, x

      {{COMP_USER}}
      {{COMP_SHOP}}

      Order::user --> User::id

Result
~~~~~~

.. arch_sys:: System X
   :id: SYS_X
   :status: open
   :tags: system, x

    .. uml::

       @startuml

           '' code from COMP_USER
           !include plantuml/comp_a.puml

           '' code from COMP_ORDER
           !include plantuml/comp_b.puml

           '' code from need_arch
           Order::user o-- User::id
          @enduml

Integrate by filter
~~~~~~~~~~~~~~~~~~~

.. code-block::

   .. arch_sys:: System X
      :id: SYS_X
      :status: open
      :tags: system, x

      {{filter("my_shop" in tags)}}

      Order::user o-- User::id

Integrate by links
~~~~~~~~~~~~~~~~~~

.. code-block::

   .. arch_sys:: System X
      :id: SYS_X
      :status: open
      :tags: system, x
      :links: COMP_USER, COMP_ORDER

      {{integrate_links("links")}}

      Order::user o-- User::id

Idea: Automatically integrate based on specific link-type. No ``{{integrate_links()}}`` needed.