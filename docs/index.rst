.. Ichno documentation master file, created by
   sphinx-quickstart on Tue Dec  3 00:34:15 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to Ichno's documentation!
=================================

.. image:: images/logo_ichno-02.png
   :align: center
   :width: 20em

Ichno is a SaaS solution designed to simplify tracking changes and storing the history of object instances or database entries.

Simply send the instance of the object with its current state, and Ichno will automatically detect changes, making them available for future queries.

Key features include:

| **Easily track changes**
| Centralize your history logic and save time and resources by offloading change tracking and history implementation to Ichno.

| **Search for versions and changes**
| Use a simple interface or API to search for changes in object instances or database records efficiently.

.. toctree::
   :caption: GENERAL VIEW
   :hidden:
   :maxdepth: 2

   using-ichno/using-ichno

.. toctree::
   :caption: API
   :hidden:
   :maxdepth: 2

   api/open-api-specification
   api/api-key
   api/posting-versions
   api/querying-changes

.. toctree::
   :caption: ADMIN
   :hidden:
   :maxdepth: 2

   admin/admin
