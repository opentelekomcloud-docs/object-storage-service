:original_name: obs_03_0008.html

.. _obs_03_0008:

Request Methods
===============

A request sent to OBS (compatible with OpenStack Swift) must comply with HTTP 1.1. In addition, the headers of a request must contain parameters defined in IAM, for example, the authentication fields.

HTTP supports several HTTP request methods, such as GET, PUT, POST, DELETE, HEAD, and COPY. A request method indicates how to access specific resources. :ref:`Table 1 <obs_03_0008__table55931017>` describes the request methods supported by REST APIs that are provided by OBS (compatible with OpenStack Swift).

.. _obs_03_0008__table55931017:

.. table:: **Table 1** REST request methods supported by OBS (compatible with OpenStack Swift)

   +--------+--------------------------------------------------------------------------------------------------------------+
   | Method | Description                                                                                                  |
   +========+==============================================================================================================+
   | GET    | Requests the server to return a specific resource, such as a container or object list or downloaded objects. |
   +--------+--------------------------------------------------------------------------------------------------------------+
   | PUT    | Requests the server store a specific resource, such as a newly created container or uploaded objects.        |
   +--------+--------------------------------------------------------------------------------------------------------------+
   | POST   | Requests the server to modify a specific resource, such as a container or object metadata.                   |
   +--------+--------------------------------------------------------------------------------------------------------------+
   | DELETE | Requests the server to delete a specific resource, for example, an object.                                   |
   +--------+--------------------------------------------------------------------------------------------------------------+
   | HEAD   | Requests the server to return the digest of a specific resource, for example, the object metadata.           |
   +--------+--------------------------------------------------------------------------------------------------------------+
   | COPY   | Requests the server to copy a specific resource, for example, an object.                                     |
   +--------+--------------------------------------------------------------------------------------------------------------+

Request Headers
---------------

When sending a REST request to OBS (compatible with OpenStack Swift), you need to add parameters in request headers. For details about request headers, see the descriptions of the specific operations.

HTTP Request Rules
------------------

-  There can be no more than 90 HTTP headers. If the token header is included, there can only be 91.
-  All HTTP headers cannot exceed 4,096 bytes.
-  An HTTP request line cannot exceed 8,192 bytes.
-  An HTTP request cannot exceed 5 GB.

   .. note::

      When sending a REST request to OBS (compatible with OpenStack Swift), you must comply with the preceding HTTP request rules. If any upper limit is exceeded, the error response may be different from that defined by OpenStack Swift. The request rules for the original OpenStack Swift APIs do not strictly check requests based on the preceding rules, but require users to comply with the preceding standard HTTP request rules.

      When the parameter length (request headers and content) of a request exceeds the buffer size of the server, OBS (compatible with OpenStack Swift) returns a 413 Request Entity Too Large: head, whereas OpenStack Swift returns a 400 Bad Request.
