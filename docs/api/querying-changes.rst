Quering Changes
---------------

All versions can be queried using the ``/version`` endpoint. This endpoint allows you to query changes made on instances registered in Ichno.

It is possible to query changes using the following parameters:

.. list-table::
   :widths: 20 20 60
   :header-rows: 1

   * - Parameter
     - Sample
     - Description
   * - type
     - ``[GET] /version?type=user`` 
     - | The type of the instance being registered. 
       | This helps to categorize different instance types (e.g., `user`, `product`) and prevents conflicts between instances with the same key in different types. You can send the table or model name, for example.
   * - key
     - ``[GET] /version?key=userId:12345&key=companyId:54321`` 
     - The key name and key value of the instance, separated by ":". Specify one or more keys to retrieve changes related to specific entities or records. More than one key can be informed, allowing composite keys.
   * - labels
     - ``[GET] /version?label=clusterId:9876&label=priority:high`` 
     - The label name and label value of the instance, separated by ":". More than one label can be informed.
   * - change
     - ``[GET] /version?change=$.status:inactive``
     - Filter changes by the property path. The propertyValue represents the new value of the property. Use this filter to retrieve changes where the property value was modified to the specified new value.
