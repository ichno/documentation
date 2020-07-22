============
Label Values
============

Aggregates label values.

Parameters
==========

.. list-table::
   :widths: 15 15 15 55
   :header-rows: 1

   * - Name
     - Type
     - Required
     - Description
   * - name
     - ``string``
     - **No**
     - Label name. Will include only values with this label name.
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
      "labels_aggregations": {
        "aggregationType": "LabelValue",
        "parameters": {
          "name": "userName",
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
      "labels_aggregations": {
        "count": 2920,
        "results": [
          {
            "key": "Adriano Queiroz",
            "count": 810
          },
          {
            "key": "Mayara Caldeira",
            "count": 743
          },
          {
            "key": "Priscila Batista",
            "count": 603
          },
          {
            "key": "Maria Eduarda",
            "count": 397
          },
          {
            "key": "Bryan Santos",
            "count": 367
          }
        ]
      }
    }
  }

