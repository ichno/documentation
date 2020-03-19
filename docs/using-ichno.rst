General View
============

.. image:: images/architecture-view.png
  :align: center


API
===

Ichno provides an API to be used to integrate easily with. The swagger definition can be accessed `here <https://api.ichno.io/swagger/index.html>`_. 
Remember that you need an API Key to communicate, even using the Swagger Interface.

API Key
-------

To post and query versions, you need to send your api-key through the header, in the ``X-API-KEY`` entry. You can see how to manage your keys at `Api Keys <admin.html#api-keys>`__. 

Posting Versions
----------------

Two endpoints to register instance versions is provided:

| 1. **Asynchronous Post** ``POST /api/v1/version/async``
| Using this endpoint, the api will response almost instantly, and the version will be processed asynchronously, and will be ready to be queried in few seconds.

| 2. **Synchronous Post** ``POST /api/v1/version``
| Using this endpoint, the version will be processed synchronously with a bigger response time. Use this endpoint if you need this versions ready to be queried right after the register post response.

Post Struct
^^^^^^^^^^^

More than only your object instance, you can send other fields to help


Quering Changes
---------------




