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
           class User {
             int id
             str name
             str email
             address
             int age
             activate()
             notify()
           }

           class Address {
             int id
             str street
             str city
             str country
           }

           User::address -> Address::id

           '' code from COMP_ORDER
           class Order {
             int id
             products
             user
             delete()
             accept()
           }

           class Product {
             int id
             str name
             float price
           }

           Order::product -> Product::id : n:n

           '' code from need_arch
           Order::user --> User::id
          @enduml

Integrate by filter
~~~~~~~~~~~~~~~~~~~

.. code-block::

   .. arch_sys:: System X
      :id: SYS_X
      :status: open
      :tags: system, x

      {{filter("my_shop" in tags)}}

      Order::user --> User::id

Integrate by links
~~~~~~~~~~~~~~~~~~

.. code-block::

   .. arch_sys:: System X
      :id: SYS_X
      :status: open
      :tags: system, x
      :links: COMP_USER, COMP_ORDER

      {{integrate_links("links")}}

      Order::user --> User::id

Idea: Automatically integrate based on specific link-type. No ``{{integrate_links()}}`` needed.