:original_name: obs_04_0048.html

.. _obs_04_0048:

Deleting the Cross-Region Replication Configuration of a Bucket
===============================================================

Functions
---------

You can perform this operation to delete the bucket replication configuration. To perform this operation, you must have the **DeleteReplicationConfiguration** permission.

Request Syntax
--------------

.. code-block:: text

   DELETE /?replication HTTP/1.1
   Host: bucketname.obs.region.example.com
   Date: date
   Authorization: authorization string

Request Parameters
------------------

This request contains no message parameters.

Request Headers
---------------

This request uses common headers. For details, see :ref:`Table 3 <obs_04_0007__table25197309>`.

Request Elements
----------------

This request involves no elements.

Response Syntax
---------------

::

   HTTP/1.1 204 No Content
   Server: OBS
   Date: date
   Connection: keep-alive

Response Headers
----------------

The response to the request uses common headers. For details, see :ref:`Table 1 <obs_04_0013__d0e686>`.

Response Elements
-----------------

This response contains no elements.

Error Responses
---------------

No special error responses are returned for this request.

Sample Request
--------------

.. code-block:: text

   DELETE /?replication HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: Wed, 27 Jun 2018 13:45:50 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:3ycNYD0CfMf0gOmmXzdGJ58KjHU=

Sample Response
---------------

::

   HTTP/1.1 204 No Content
   Server: OBS
   x-obs-request-id: 900B000001643FE6BBCC9C9F54FA7A7E
   x-obs-id-2: 32AAAQAAEAABSAAgAAEAABAAAQAAEAABCS8Exs52zCf9duxPLnBircmGa/JOCjec
   Date: Wed, 27 Jun 2018 13:45:50 GMT
