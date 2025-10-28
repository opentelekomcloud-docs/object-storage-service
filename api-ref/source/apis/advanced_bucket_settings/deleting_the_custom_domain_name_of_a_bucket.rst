:original_name: obs_04_0061.html

.. _obs_04_0061:

Deleting the Custom Domain Name of a Bucket
===========================================

Functions
---------

OBS uses the DELETE method to delete the custom domain name of a bucket.

To perform this operation, the user must be the bucket owner or the bucket owner's IAM user that has permissions required for deleting custom domain names.

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

   +-----------------------+-----------------------------------------------------------------------+-----------------------+
   | Parameter             | Description                                                           | Mandatory (Yes/No)    |
   +=======================+=======================================================================+=======================+
   | customdomain          | Specifies the custom domain name to be deleted.                       | Yes                   |
   |                       |                                                                       |                       |
   |                       | Type: string, which must meet the naming conventions of domain names. |                       |
   |                       |                                                                       |                       |
   |                       | Specifications: The value contains a maximum of 256 characters.       |                       |
   |                       |                                                                       |                       |
   |                       | No default value.                                                     |                       |
   +-----------------------+-----------------------------------------------------------------------+-----------------------+

Request Header
--------------

This request uses common headers. For details, see :ref:`Table 3 <obs_04_0007__table25197309>`.

Request Elements
----------------

This request involves no elements.

Response Syntax
---------------

::

   HTTP/1.1 204 No Content
   Server: OBS
   x-obs-request-id: request id
   x-obs-id-2: id
   Date: date

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

   DELETE /?customdomain=obs.ccc.com HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: Mon, 14 Jan 2019 08:27:50 +0000
   Authorization: OBS UDSIAMSTUBTEST000094:ACgHHA1z+dqZhqS7D2SbU8ugluw=

Sample Response
---------------

::

   HTTP/1.1 204 No Content
   Server: OBS
   x-obs-request-id: 000001697694073F80E9D3D43BB10B8F
   x-obs-id-2: 32AAAQAAEAABSAAgAAEAABAAAQAAEAABCSyjWyXNRPSnFymJW0AI59GKpW0Qm9UJ
   Date: Wed, 13 Mar 2019 10:23:26 GMT
