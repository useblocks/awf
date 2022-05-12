Merging elements
----------------

New directive: need_arch
~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block::

   .. need_arch::
      :filter: "my_shop" in tags

      Order::user --> User::id

Result
~~~~~~

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

Used PlantUML code
~~~~~~~~~~~~~~~~~~

.. code-block:: text

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
