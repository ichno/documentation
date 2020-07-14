=========================
Date Histogram by Version
=========================

The date histogram by version shows the number of versions posted in a specific date value within you changes dataset. 

Parameters
==========

.. list-table::
   :widths: 15 15 15 55
   :header-rows: 1

   * - Field
     - Type
     - Required
     - Description
   * - format
     - ``string``
     - **No**
     - Se avaiable formats in :ref:`date-formar-pattern` 
   * - interval
     - ``string``
     - **No**
     - | Interval period for aggregation. Avaiable values are:
       | - Second
       | - Minute
       | - Hour
       | - Day
       | - Week
       | - Month
       | - Quarter
       | - Year

Example
=======

Request
-------

.. code-block:: javascript

  {
    "aggregations": {
      "versions_datehistogram": {
        "aggregationType": "VersionDateHistogram",
        "parameters": {
          "format": "yyyy",
          "interval": "Year"
        }
      }
    }
  }

Response
--------

.. code-block:: language

  {
    "aggregations": {
      "versions_datehistogram": {
        "key": null,
        "count": 307065,
        "results": [
          {
            "key": "2019",
            "count": 155095,
            "results": null,
            "aggregations": null
          },
          {
            "key": "2020",
            "count": 151970,
            "results": null,
            "aggregations": null
          }
        ],
        "aggregations": null
      }
    }
  }

