Tips
====

Keys
----

Key on registering instances
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Keys are used to identify a single instance of your objects. As you can register versions from many subsets of instances, you should send the name of instance subset as a part of key, to avoid keys conflicts. This subset can be the table or package name. 
For example, if you have a subset of users and another subset of products, the correct way to send this entities, through API, is:

.. list-table::
    :widths: 50 50
    :width: 100
    :header-rows: 1

    * - User 1
      - User 2

    * - ..  code-block:: javascript
            :emphasize-lines: 3,4

            {
              keys: [
                { subset: 'user' },
                { id: 1 }
              ],
              object: {
                name: 'User Name',
                ...
              }
            }
    
      - ..  code-block:: javascript
            :emphasize-lines: 3,4

            {
              keys: [
                { subset: 'user' },
                { id: 2 }
              ],
              object: {
                name: 'User Name',
                ...
              }
            }

.. list-table::
    :widths: 50 50
    :width: 100
    :header-rows: 1

    * - Product 1
      - Product 2

    * - ..  code-block:: javascript
            :emphasize-lines: 3,4

            {
              keys: [
                { subset: 'product' },
                { id: 1 }
              ],
              object: {
                name: 'Product Name',
                ...
              }
            }
    
      - ..  code-block:: javascript
            :emphasize-lines: 3,4

            {
              keys: [
                { subset: 'product' },
                { id: 2 }
              ],
              object: {
                name: 'Product Name',
                ...
              }
            }

Key on querying instances
^^^^^^^^^^^^^^^^^^^^^^^^^

You can query by keys using only a subset of keys registered with your instances. In the same example used above, if you need ti query all changes made in the 'user' subset, you can use the following json to get that:

.. code-block:: javascript
  :emphasize-lines: 3

  {
    keys: [
      { subset: 'user' }
    ]
  }

Labels
------

Labels are useful to add some data that you want to query for. For example, if you want to register the user who made those changes, you can use labels, allowing you to search for all change made by a user.