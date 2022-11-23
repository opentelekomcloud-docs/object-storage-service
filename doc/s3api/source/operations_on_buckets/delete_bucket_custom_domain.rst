:original_name: en-us_topic_0000001121228134.html

.. _en-us_topic_0000001121228134:

DELETE Bucket Custom Domain
===========================

OBS uses the DELETE method to delete the custom domain name of a bucket.

Request Syntax
--------------

.. code-block:: text

   DELETE /?customdomain=domainname HTTP/1.1
   User-Agent: curl/7.29.0
   Host: bucketname.obs.region.example.com
   Accept: */*
   Date: date
   Authorization: authorization string

Request Parameters
------------------

.. table:: **Table 1** Request parameters

   +-----------------------+----------------------------------------------------------------------+-----------------------+
   | Parameter             | Description                                                          | Mandatory             |
   +=======================+======================================================================+=======================+
   | customdomain          | Specifies the custom domain name to be deleted.                      | Yes                   |
   |                       |                                                                      |                       |
   |                       | Type: string, which must meet the naming convention of domain names. |                       |
   |                       |                                                                      |                       |
   |                       | Specifications: The value contains a maximum of 256 characters.      |                       |
   |                       |                                                                      |                       |
   |                       | No default value.                                                    |                       |
   +-----------------------+----------------------------------------------------------------------+-----------------------+

Request Headers
---------------

This request uses common headers. For details about common request headers, see the section :ref:`Common Request Headers <en-us_topic_0125560462>`.

Request Elements
----------------

This request involves no elements.

Response Syntax
---------------

::

   HTTP/1.1 204 No Content
   Server: OBS
   x-amz-request-id: request id
   x-amz-id-2: id
   Date: date

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

   DELETE /?customdomain=obs.ccc.com HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: Mon, 14 Jan 2019 08:27:50 +0000
   Authorization: AWS UDSIAMSTUBTEST000094:ACgHHA1z+dqZhqS7D2SbU8ugluw=

Sample Response
---------------

::

   HTTP/1.1 204 No Content
   Server: OBS
   x-amz-request-id: 000001697694073F80E9D3D43BB10B8F
   x-amz-id-2: 32AAAQAAEAABSAAgAAEAABAAAQAAEAABCSyjWyXNRPSnFymJW0AI59GKpW0Qm9UJ
   Date: Wed, 13 Mar 2019 10:23:26 GMT
