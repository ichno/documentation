.. _json-path:

=========
JSON Path
=========

Json paths is used in Ichno to identify an property uniquelly. It's important to distinguish that the concept applied in Ichno is different from other libraries avaiable, which use json paths as a language to filter properties and objects inside an json object.

Examples
========

Given the json.

.. code-block:: javascript

  {
    "store": {
        "book": [
            {
                "category": "reference",
                "author": "Nigel Rees",
                "title": "Sayings of the Century",
                "price": 8.95
            },
            {
                "category": "fiction",
                "author": "Evelyn Waugh",
                "title": "Sword of Honour",
                "price": 12.99
            }
        ],
        "bicycle": {
            "color": "red",
            "price": 19.95
        }
    },
    "expensive": 10
  }

.. list-table::
    :widths: 50 50
    :header-rows: 1

    * - Json Path
      - Property Value
    * - ``$['expensive']``
      - 10
    * - ``$['store']['book'][0]['author']``
      - "Nigel Rees"
    * - ``$['store']['book'][1]['price']``
      - 12.99
    * - ``$['store']['book']['bicycle']['bicycle']``
      - "red"


JSON Path Regex
================

In some queries and aggregations, is possible to use regex in properties names to expand the possibilities of filter. 

Given the following sample:

.. code-block:: javascript

  {
    "store": {
        "book": [
            {
                "category": "reference",
                "sub-category": "reference",
                "author": "Nigel Rees",
                "title": "Sayings of the Century",
                "price": 8.95
            },
            {
                "category": "fiction",
                "sub-category": "fiction",
                "author": "Evelyn Waugh",
                "title": "Sword of Honour",
                "price": 12.99
            }
        ]
    },
    "expensive": 10
  }

If you use the regex ``$['store']['book'][.*]['.*category']`` your query will include all values of 'category' or 'sub-category' book properties in results.

For more information about regular expressions, see :ref:`regular-expression-syntax`.
