:original_name: en-us_topic_0000001684063985.html

.. _en-us_topic_0000001684063985:

DELETE Bucket Replication
=========================

This operation deletes the bucket replication configuration. Only users have the **s3:DeleteReplicationConfiguration** permission can perform this operation.

Request Syntax
--------------

.. code-block:: text

   DELETE /?replication HTTP/1.1
   Host: bucketname.obs.region.example.com
   Date: date
   Authorization: authorization string

Request Parameters
------------------

This request contains no parameter.

Request Headers
---------------

This request uses common headers. For details about common request headers, see the section :ref:`Common Request Headers <en-us_topic_0125560462>`.

Request Elements
----------------

This request involves no elements.

Response Syntax
---------------

.. code-block::

   HTTP/1.1 204 No Content
   Server: OBS
   x-amz-id-2:id
   x-amz-request-id:id
   Date: date
   Connection: keep-alive

Response Headers
----------------

This response uses common headers. For details about common response headers, see the section :ref:`Common Response Headers <en-us_topic_0125560484>`.

Response Elements
-----------------

This response involves no elements.

Error Responses
---------------

No special error responses are returned. For details about error responses, see :ref:`Table 1 <en-us_topic_0125560440__table30733758>`.

Sample Request
--------------

.. code-block:: text

   DELETE /?replication HTTP/1.1
   Host: examplebucket.obs.region.example.com
   Date: Wed, 11 Feb 2015 05:37:16 GMT
   Authorization: signatureValue

Sample Response
---------------

.. code-block::

   HTTP/1.1 204 No Content
   Server: OBS
   x-amz-id-2: Uuag1LuByRx9e6j5OnimrSAMPLEtRPfTaOAa==
   x-amz-request-id: 656c76696e672example
   Date: Wed, 11 Feb 2015 05:37:16 GMT
