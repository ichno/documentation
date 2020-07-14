Aggregations
------------
Aggregations helps provide aggregated data based on a search query. It is based on simple building blocks called aggregations, that can be composed in order to build complex summaries of the data.

An aggregation can be seen as a unit-of-work that builds analytic information over a set of versions. The context of the execution defines what this document set is (e.g. a top-level aggregation executes within the context of the executed query/filters of the search request).

Structuring Aggregations
^^^^^^^^^^^^^^^^^^^^^^^^
The following snippet captures the basic structure of aggregations:

.. code-block:: javascript

    "aggregations" : {
        "<aggregation_name>" : {
            "aggregationTarget": "<aggregation_target>",
            "aggregationType: "<aggregation_type>"
            [,"parameters" : {
                ["<parameter_1>" : { ... } ]*
            } ]?
            [,"aggregations" : { [<sub_aggregation>]+ } ]?
        }
        [,"<aggregation_name_2>" : { ... } ]*
    }


Aggregations Types
^^^^^^^^^^^^^^^^^^

There are many different types of aggregations, each with its own purpose and output. 

.. toctree::
   :maxdepth: 1

   version-date-histogram.rst