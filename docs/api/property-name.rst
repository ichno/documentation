=========================
Property Name
=========================

Aggregates by properties.

Parameters
==========

.. list-table::
   :widths: 15 15 15 55
   :header-rows: 1

   * - Name
     - Type
     - Required
     - Description
   * - jsonPath
     - ``string``
     - **No**
     - Filter the properties that must be included in aggregation. Read about Json Paths in :ref:`json-path`.
   * - depth
     - ``integer``
     - **No**
     - If the object contains objects as properties, you can define how many levels should be included in the aggregation.
   * - size
     - ``integer``
     - **No**
     - Number of aggregation to be returned

Example
=======

Request
-------

.. code-block:: javascript

  {
    "length": 0,
    "aggregations": {
      "properties_names": {
        "aggregationType": "Property",
        "parameters": {
          "depth": 0,
          "jsonPath": "$['Documents']['[^('\\])]*']",
          "size": 5
        }
      }
    }
  }

Response
--------

.. code-block:: javascript

  {
    "total": 315025,
    "data": [],
    "aggregations": {
      "properties_names": {
        "count": 115814,
        "results": [
          {
            "key": "$['Documents']['edc17b99-d956-4300-8b0e-8aa60f9cdb94']",
            "count": 23818
          },
          {
            "key": "$['Documents']['8dfc2491-dab0-4d36-8f1a-bf96d4002e91']",
            "count": 23568
          },
          {
            "key": "$['Documents']['b93acc29-f93c-4968-903c-6fa961497969']",
            "count": 23545
          },
          {
            "key": "$['Documents']['ba86b58b-1899-4289-b191-b638586eddf9']",
            "count": 22459
          },
          {
            "key": "$['Documents']['7b526f64-413e-4dca-8120-22ab98b33ab8']",
            "count": 22424
          }
        ]
      }
    }
  }

