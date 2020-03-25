.. docs documentation master file, created by
   sphinx-quickstart on Wed Mar 25 15:12:22 2020.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to docs's documentation!
================================

.. toctree::
   :maxdepth: 2
   :caption: Contents:

   modules/one.rst



Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

.. uml:: modules/external.uml

.. uml::

   @startuml
      Class01 <|-- Class02
      Class03 *-- Class04
      Class05 o-- Class06
      Class07 .. Class08
      Class09 -- Class10
   @enduml