:original_name: obs_04_0092.html

.. _obs_04_0092:

Modifying an Object
===================

Functions
---------

This operation can modify an object from a specified position.

.. note::

   This API is supported only by parallel file systems. For details about how to create a parallel file system, see :ref:`Sample Request: Creating a Parallel File System <obs_04_0021__section4293341135610>`.

Request Syntax
--------------

.. code-block:: text

   PUT /ObjectName?modify&position=Position HTTP/1.1
   Host: bucketname.obs.region.example.com
   Content-Type: type
   Content-Length: length
   Authorization: authorization
   Date: date
   <object Content>

Request Parameters
------------------

The request needs to specify parameters in the message, indicating that the upload is for modification, and specifying the position in the object to be modified. :ref:`Table 1 <obs_04_0092__table925513139324>` describes the parameters.

.. _obs_04_0092__table925513139324:

.. table:: **Table 1** Request parameters

   +-----------------------+-------------------------------------------------------+-----------------------+
   | Parameter             | Description                                           | Mandatory             |
   +=======================+=======================================================+=======================+
   | modify                | Indicates that the file is uploaded for modification. | Yes                   |
   |                       |                                                       |                       |
   |                       | Type: string                                          |                       |
   +-----------------------+-------------------------------------------------------+-----------------------+
   | position              | Position in the object where the modification starts  | Yes                   |
   |                       |                                                       |                       |
   |                       | Type: integer                                         |                       |
   +-----------------------+-------------------------------------------------------+-----------------------+

Request headers
---------------

This request uses common request headers. For details, see :ref:`Table 3 <obs_04_0007__table25197309>`.

Request Elements
----------------

This request involves no elements.

Response Syntax
---------------

::

   HTTP/1.1 status_code
   Date: Date
   ETag: etag
   Content-Length: length
   Server: OBS
   x-obs-request-id: request-id
   x-obs-id-2: id

Response Headers
----------------

The response to the request uses common headers. For details, see :ref:`Table 1 <obs_04_0013__d0e686>`.

Response Elements
-----------------

This response contains no elements.

Error Responses
---------------

No special error responses are returned. For details about error responses, see :ref:`Table 2 <obs_04_0115__d0e843>`.

Sample Request
--------------

.. code-block:: text

   PUT /ObjectName?modify&position=Position HTTP/1.1
   Host: examplebucket.obs.region.example.com
   Date: Wed, 08 Jul 2015 06:57:01 GMT
   Content-Type: image/jpg
   Content-Length: 1458
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:kZoYNv66bsmc10+dcGKw5x2PRrk=

   [1458 bytes of object data]

Sample Response
---------------

::

   HTTP/1.1 200
   Date: Wed, 08 Jul 2015 06:57:02 GMT
   ETag: "d41d8cd98f00b204e9800998ecf8427e"
   Content-Length: 0
   Server: OBS
   x-obs-request-id: 8DF400000163D3F0FD2A03D2D30B0542
   x-obs-id-2: 32AAAUgAIAABAAAQAAEAABAAAQAAEAABCTjCqTmsA1XRpIrmrJdvcEWvZyjbztd
