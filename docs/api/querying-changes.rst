Quering Changes
---------------

After have your instance versions registered, it is possible to query changes using the following parameters:

.. list-table::
   :widths: 15 15 15 55
   :header-rows: 1

   * - Field
     - Type
     - Required
     - Description
   * - keys
     - | ``[string]: string | number | boolean``
       | (Key Value List)
     - **No**
     - | Unique identifier of the instance in the clients system. Use the same values used to register the instance. If you are using composite keys, its possible to send all keys or a subset of these keys.
   * - startDate
     - | ``date``
       | (yyyy-MM-ddThh:mm:ss)
     - **No**
     - | Start date for date range.
   * - endDate
     - | ``date``
       | (yyyy-MM-ddThh:mm:ss)
     - **No**
     - | End date for date range.
   * - labels
     - | ``[string]: string | number | boolean``
       | (Key Value List)
     - **No**
     - | Change labels.
   * - properties
     - | ``object``
     - **No**
     - Filter changes by properties
   * - start
     - | ``integer``
     - **No**
     - Number of register to skip on this query. Useful to pagination.
   * - length
     - | ``integer``
     - **No**
     - Number of register that must be returned. Useful to pagination.
     
Query by properties
^^^^^^^^^^^^^^^^^^^

Ichno also allow you to query by properties, allowing you to query changes made on specific property. Properties query parameters are send through an object in the property ``properties`` on change query endpoint:

.. list-table::
    :widths: 15 15 15 55
    :header-rows: 1

    * - Field
      - Type
      - Required
      - Description
    * - path
      - | ``[string | number | boolean]``
        | (array)
      - **No**
      - | Property path. 
        | For example, if you are registering version for the following object:
          
          ..  code-block:: javascript

              {
                name: 'John Hanson',
                address: {
                  street: 'The Great, Ave',
                  number: 153
                }
              }
          
        | You can query the name changes using the following array as parameter:
        | ``['name']``
        | Or this one to filter by street name changes:
        | ``['address', 'street']``
    * - newValue
      - | ``string | number | boolean``
      - **No**
      - | Filter properties by the new value.
    * - oldValue
      - | ``string | number | boolean``
      - **No**
      - | Filter properties by the old value.