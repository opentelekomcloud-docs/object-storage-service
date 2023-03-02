:original_name: obs_04_0094.html

.. _obs_04_0094:

Renaming an Object
==================

Functions
---------

This operation can rename an object.

.. note::

   This API is supported only by parallel file systems. For details about how to create a parallel file system, see :ref:`Sample Request 4 <obs_04_0021__section4293341135610>`. Renaming an object is a non-idempotent operation.

Request Syntax
--------------

.. code-block:: text

   POST /ObjectName?name=Name&rename HTTP/1.1
   Host: bucketname.obs.region.example.com
   Authorization: authorization
   Date: date

Request Parameters
------------------

The request needs to specify parameters in the message, indicating that this is a renaming operation, specifying the new name. :ref:`Table 1 <obs_04_0094__table925513139324>` describes the parameters.

.. _obs_04_0094__table925513139324:

.. table:: **Table 1** Request parameters

   +-----------------------+-------------------------------------------------+-----------------------+
   | Parameter             | Description                                     | Mandatory             |
   +=======================+=================================================+=======================+
   | name                  | New name for the object. Use the absolute path. | Yes                   |
   |                       |                                                 |                       |
   |                       | Type: string                                    |                       |
   +-----------------------+-------------------------------------------------+-----------------------+
   | rename                | Indicates that this is a renaming operation.    | Yes                   |
   |                       |                                                 |                       |
   |                       | Type: string                                    |                       |
   +-----------------------+-------------------------------------------------+-----------------------+

Request Headers
---------------

This request uses common request headers. For details, see :ref:`Table 3 <obs_04_0007__table25197309>`.

Request Elements
----------------

This request involves no elements.

Response Syntax
---------------

::

   HTTP/1.1 204 status_code
   Server: OBS
   x-obs-request-id: request-id
   x-obs-id-2: id
   Date: Date

Response Headers
----------------

The response to the request uses common headers. For details, see :ref:`Table 1 <obs_04_0013__d0e686>`.

Response Elements
-----------------

This response involves no elements.

Error Responses
---------------

No special error responses are returned. For details about error responses, see :ref:`Table 2 <obs_04_0115__d0e843>`.

Sample Request
--------------

.. code-block:: text

   POST /ObjectName?name=file2&rename HTTP/1.1
   Host: examplebucket.obs.region.example.com
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:75/Y4Ng1izvzc1nTGxpMXTE6ynw=
   Date: WED, 01 Jul 2015 04:19:20 GMT

Sample Response
---------------

::

   HTTP/1.1 204 No Content
   Server: OBS
   x-obs-request-id: 8DF400000163D3F51DEA05AC9CA066F1
   x-obs-id-2: 32AAAUgAIAABAAAQAAEAABAAAQAAEAABCSgkM4Dij80gAeFY8pAZIwx72QhDeBZ5
   Date: WED, 01 Jul 2015 04:19:21 GMT
