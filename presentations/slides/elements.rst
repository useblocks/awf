Architecture elements
=====================

Note
----

This is just a concept!!
Nothing from the following slides got yet implemented.

Recap Sphinx-Needs
------------------

Need object
~~~~~~~~~~~

.. story:: Example
   :id: STORY_001
   :status: open
   :tags: example; prio_1
   :links: SPEC_001

   This is a story

   .. uml::

      card A
      card B
      A -> B: links

.. spec:: Example
   :id: SPEC_001
   :hide:


Used to give "content" an unique ID, meta data and linking possibilities.


.. container:: small

   Sphinx-Needs: `Homepage <https://sphinx-needs.com/>`_ |
   `Docs <https://sphinxcontrib-needs.readthedocs.io/en/latest/>`_ |
   `DWF <https://useblocks.com/dwf>`_

Code
~~~~

.. code-block:: rst

   .. story:: Example
      :id: STORY_001
      :status: open
      :tags: example; prio_1
      :links: SPEC_001

      This is a story

      .. uml::

         card A
         card B
         A -> B: links

Filtering
~~~~~~~~~

.. code-block:: rst

   .. needtable::
      :filter: id.endswith("001") and type in ("story", "arch_sys")
      :columns: id,title, status, tags


.. needtable::
   :filter: id.endswith("001") and type in ("story", "arch_sys")
   :columns: id,title, status, tags
   :style: table

Flowcharts
~~~~~~~~~~

.. code-block:: rst

   .. needflow::
      :filter: status in ("open", "done")


.. needflow::
   :filter: status in ("open", "done") or not status


Idea
----

Sphinx-Needs objects contain a single PlantUML diagram only.

.. code-block:: rst

   .. arch_sys:: System X
      :id: SYS_001
      :status: done
      :tags: system_x
      :links: COMP_001

      card "Component A" as A
      card "Component B" as B
      A -> B: links


.. revealjs-break::
   :notitle:

.. arch_sys:: System X
   :id: SYS_001
   :status: done
   :tags: system_x
   :links: COMP_001

   .. uml::

      card "Component A" as A
      card "Component B" as B
      A -> B: links

.. arch_comp:: Example
   :id: COMP_001
   :hide:

With a more focused layout
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. arch_sys:: System Y
   :id: SYS_002
   :status: done
   :tags: system_x
   :links: COMP_001
   :layout: focus_l
   :style: discreet, discreet_border

   .. uml::

      card "Component A" as A
      card "Component B" as B
      A -> B: links

.. code-block:: rst

   .. arch_sys:: System Y
      :layout: focus_l
      :style: discreet


Configuration
-------------

Configure need type to be an "Architecture" type.

.. code-block:: python

   needs_types = [
       dict(directive="arch",
            title="Architecture",
            content= "plantuml"  # <- New option, default "sphinx"
            prefix="AR_",
            color="#BFD8D2",
            style="node"),
       ... ]

Example data
------------

.. arch_comp:: User Management
   :id: COMP_USER
   :tags: my_shop
   :layout: arch

   .. uml:: /plantuml/comp_a.puml


.. arch_comp:: Order System
   :id: COMP_ORDER
   :tags: my_shop
   :layout: arch

   .. uml:: /plantuml/comp_b.puml






