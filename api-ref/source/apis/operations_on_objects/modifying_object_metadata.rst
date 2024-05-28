:original_name: obs_04_0091.html

.. _obs_04_0091:

Modifying Object Metadata
=========================

Functions
---------

This operation modifies, deletes, or adds metadata to uploaded objects in a bucket.

Request Syntax
--------------

.. code-block:: text

   PUT /ObjectName?metadata HTTP/1.1
   Host: bucketname.obs.region.example.com
   Content-Type: application/xml
   Content-Length: length
   Authorization: authorization
   Date: date
   <Optional Additional Header>
   <object Content>

Request Parameters
------------------

.. table:: **Table 1** Request parameters

   +-----------------------+-----------------------+-----------------------+
   | Parameter             | Description           | Mandatory             |
   +=======================+=======================+=======================+
   | versionId             | Object version ID     | No                    |
   |                       |                       |                       |
   |                       | Type: string          |                       |
   +-----------------------+-----------------------+-----------------------+

Request Headers
---------------

.. note::

   OBS supports the six HTTP request headers: Cache-Control, Expires, Content-Encoding, Content-Disposition, Content-Type, and Content-Language. It saves these header values in the metadata of the object. When the object is downloaded or queried, the saved values are set for corresponding HTTP headers and returned to the client.

.. table:: **Table 2** Request headers

   +---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Header                          | Description                                                                                                                                                                                                                                    | Mandatory             |
   +=================================+================================================================================================================================================================================================================================================+=======================+
   | x-obs-metadata-directive        | Metadata operation indicator.                                                                                                                                                                                                                  | Yes                   |
   |                                 |                                                                                                                                                                                                                                                |                       |
   |                                 | The value can be **REPLACE_NEW** or **REPLACE**.                                                                                                                                                                                               |                       |
   |                                 |                                                                                                                                                                                                                                                |                       |
   |                                 | **REPLACE_NEW**: The metadata that has an existing value is replaced. A value is assigned to the metadata that does not have a value. The metadata that is not specified remains unchanged. (Note: a header with custom metadata is replaced.) |                       |
   |                                 |                                                                                                                                                                                                                                                |                       |
   |                                 | **REPLACE**: Use the header field carried in the current request to replace the original metadata. The metadata that is not specified (except **x-obs-storage-class**) will be deleted.                                                        |                       |
   |                                 |                                                                                                                                                                                                                                                |                       |
   |                                 | Type: string                                                                                                                                                                                                                                   |                       |
   +---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Cache-Control                   | Specifies the cache behavior of the web page when the object is downloaded.                                                                                                                                                                    | No                    |
   |                                 |                                                                                                                                                                                                                                                |                       |
   |                                 | Type: string                                                                                                                                                                                                                                   |                       |
   +---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Content-Disposition             | Specifies the name of the object when it is downloaded.                                                                                                                                                                                        | No                    |
   |                                 |                                                                                                                                                                                                                                                |                       |
   |                                 | Type: string                                                                                                                                                                                                                                   |                       |
   +---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Content-Encoding                | Specifies the content encoding format when an object is being downloaded.                                                                                                                                                                      | No                    |
   |                                 |                                                                                                                                                                                                                                                |                       |
   |                                 | Type: string                                                                                                                                                                                                                                   |                       |
   +---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Content-Language                | Specifies the content language format when an object is downloaded.                                                                                                                                                                            | No                    |
   |                                 |                                                                                                                                                                                                                                                |                       |
   |                                 | Type: string                                                                                                                                                                                                                                   |                       |
   +---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Content-Type                    | Object file type.                                                                                                                                                                                                                              | No                    |
   |                                 |                                                                                                                                                                                                                                                |                       |
   |                                 | Type: string                                                                                                                                                                                                                                   |                       |
   +---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Expires                         | Specifies the cache expiration time of the web page when the object is downloaded.                                                                                                                                                             | No                    |
   |                                 |                                                                                                                                                                                                                                                |                       |
   |                                 | Type: string                                                                                                                                                                                                                                   |                       |
   +---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | x-obs-website-redirect-location | When the bucket is configured with the website redirection, the request for obtaining the object can be redirected to another object or an external URL in the bucket.                                                                         | No                    |
   |                                 |                                                                                                                                                                                                                                                |                       |
   |                                 | In the following example, the request header sets the redirection to an object (**anotherPage.html**) in the same bucket:                                                                                                                      |                       |
   |                                 |                                                                                                                                                                                                                                                |                       |
   |                                 | x-obs-website-redirect-location:/anotherPage.html                                                                                                                                                                                              |                       |
   |                                 |                                                                                                                                                                                                                                                |                       |
   |                                 | In the following example, the request header sets the object redirection to an external URL:                                                                                                                                                   |                       |
   |                                 |                                                                                                                                                                                                                                                |                       |
   |                                 | x-obs-website-redirect-location:http://www.example.com/                                                                                                                                                                                        |                       |
   |                                 |                                                                                                                                                                                                                                                |                       |
   |                                 | Type: string                                                                                                                                                                                                                                   |                       |
   |                                 |                                                                                                                                                                                                                                                |                       |
   |                                 | Constraint: The value must be prefixed by a slash (/), **http://**, or **https://**. The length of the value cannot exceed 2 KB.                                                                                                               |                       |
   +---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | x-obs-storage-class             | Specifies the storage class of an object.                                                                                                                                                                                                      | No                    |
   |                                 |                                                                                                                                                                                                                                                |                       |
   |                                 | Type: string                                                                                                                                                                                                                                   |                       |
   |                                 |                                                                                                                                                                                                                                                |                       |
   |                                 | Storage class options: **STANDARD** (Standard), **WARM** (Warm), **COLD** (Cold). These values are case sensitive.                                                                                                                             |                       |
   |                                 |                                                                                                                                                                                                                                                |                       |
   |                                 | Example: **x-obs-storage-class: STANDARD**                                                                                                                                                                                                     |                       |
   +---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | x-obs-meta-\*                   | A message header starting with **x-obs-meta-** can be added to a request to add custom metadata for object management. Custom metadata will be returned in the response header when you retrieve or query the metadata of the object.          | No                    |
   |                                 |                                                                                                                                                                                                                                                |                       |
   |                                 | Type: string                                                                                                                                                                                                                                   |                       |
   |                                 |                                                                                                                                                                                                                                                |                       |
   |                                 | Example: **x-obs-meta-test: test metadata**                                                                                                                                                                                                    |                       |
   +---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

Request Elements
----------------

This request involves no elements.

Response Syntax
---------------

::

   HTTP/1.1 status_code
   Date: date
   Content-Length: length
   Etag: etag
   Last-Modified: time

Response Headers
----------------

.. table:: **Table 3** Additional response headers

   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Header                            | Description                                                                                                                                                                                                                                                         |
   +===================================+=====================================================================================================================================================================================================================================================================+
   | x-obs-metadata-directive          | Metadata operation indicator.                                                                                                                                                                                                                                       |
   |                                   |                                                                                                                                                                                                                                                                     |
   |                                   | The value can be **REPLACE_NEW** or **REPLACE**.                                                                                                                                                                                                                    |
   |                                   |                                                                                                                                                                                                                                                                     |
   |                                   | Type: string                                                                                                                                                                                                                                                        |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cache-Control                     | Specifies the cache behavior of the web page when the object is downloaded. If a request carries this header field, the response message must contain this header field.                                                                                            |
   |                                   |                                                                                                                                                                                                                                                                     |
   |                                   | Type: string                                                                                                                                                                                                                                                        |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Disposition               | Specifies the name of the object when it is downloaded. If a request carries this header field, the response message must contain this header field.                                                                                                                |
   |                                   |                                                                                                                                                                                                                                                                     |
   |                                   | Type: string                                                                                                                                                                                                                                                        |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Encoding                  | Specifies the content encoding format when an object is being downloaded. If a request carries this header field, the response message must contain this header field.                                                                                              |
   |                                   |                                                                                                                                                                                                                                                                     |
   |                                   | Type: string                                                                                                                                                                                                                                                        |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Language                  | Specifies the content language format when an object is downloaded. If a request carries this header field, the response message must contain this header field.                                                                                                    |
   |                                   |                                                                                                                                                                                                                                                                     |
   |                                   | Type: string                                                                                                                                                                                                                                                        |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Expires                           | Specifies the cache expiration time of the web page when the object is downloaded. If a request carries this header field, the response message must contain this header field.                                                                                     |
   |                                   |                                                                                                                                                                                                                                                                     |
   |                                   | Type: string                                                                                                                                                                                                                                                        |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-website-redirect-location   | When the bucket is configured with the website redirection, the request for obtaining the object can be redirected to another object or an external URL in the bucket. If a request carries this header field, the response message must contain this header field. |
   |                                   |                                                                                                                                                                                                                                                                     |
   |                                   | Type: string                                                                                                                                                                                                                                                        |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-storage-class               | Specifies the storage class of an object. If a request carries this header field, the response message must contain this header field.                                                                                                                              |
   |                                   |                                                                                                                                                                                                                                                                     |
   |                                   | Type: string                                                                                                                                                                                                                                                        |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-meta-\*                     | Custom metadata is used to manage objects in a customized manner. If a request carries this header field, the response message must contain this header field.                                                                                                      |
   |                                   |                                                                                                                                                                                                                                                                     |
   |                                   | Type: string                                                                                                                                                                                                                                                        |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Elements
-----------------

This response contains no elements.

Error Responses
---------------

No special error responses are returned. For details about error responses, see :ref:`Table 2 <obs_04_0115__d0e843>`.

Sample Request: Adding Metadata for an Object
---------------------------------------------

Add the following metadata to the object: **Content-Type:application/zip** and **x-obs-meta-test:meta**.

.. code-block:: text

   PUT /object?metadata HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: WED, 01 Jul 2015 14:24:33 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:NxtSMS0jaVxlLnxlO9awaMTn47s=
   x-obs-metadata-directive:REPLACE_NEW
   Content-Type:application/zip
   x-obs-meta-test:meta

Sample Response: Adding Metadata for an Object
----------------------------------------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: 8DF400000163D3E4BB5905C41B6E65B6
   Accept-Ranges: bytes
   x-obs-id-2: 32AAAQAAEAABAAAQAAEAABAAAQAAEAABCSD3nAiTaBoeyt9oHp9vTYtXnLDmwV6D
   Date: WED, 01 Jul 2015 04:19:21 GMT
   Content-Length: 0
   x-obs-metadata-directive:REPLACE_NEW
   x-obs-meta-test:meta

Sample Request: Editing Metadata of an Object
---------------------------------------------

If metadata **x-obs-meta-test:testmeta** exists in the object and the value of **x-obs-storage-class** is **WARM**, change the metadata **x-obs-meta-test** of the object to **newmeta** and change **x-obs-storage-class** to **COLD**.

.. code-block:: text

   PUT /object?metadata HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: WED, 01 Jul 2015 14:24:33 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:NxtSMS0jaVxlLnxlO9awaMTn47s=
   x-obs-metadata-directive:REPLACE_NEW
   x-obs-meta-test:newmeta
   x-obs-storage-class:COLD

Sample Response: Editing Metadata of an Object
----------------------------------------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: 8DF400000163D3E4BB5905C41B6E65B6
   Accept-Ranges: bytes
   x-obs-id-2: 32AAAQAAEAABAAAQAAEAABAAAQAAEAABCSD3nAiTaBoeyt9oHp9vTYtXnLDmwV6D
   Date: WED, 01 Jul 2015 04:19:21 GMT
   Content-Length: 0
   x-obs-metadata-directive:REPLACE_NEW
   x-obs-meta-test:newmeta
   x-obs-storage-class:COLD

Sample Request: Deleting Metadata of an Object
----------------------------------------------

Metadata **x-obs-meta-test:newmeta** and **Content-Type:application/zip** exist in the object, and delete **x-obs-meta-test**.

.. code-block:: text

   PUT /object?metadata HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: WED, 01 Jul 2015 14:24:33 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:NxtSMS0jaVxlLnxlO9awaMTn47s=
   x-obs-metadata-directive:REPLACE
   Content-Type:application/zip

Sample Response: Deleting Metadata of an Object
-----------------------------------------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: 8DF400000163D3E4BB5905C41B6E65B6
   Accept-Ranges: bytes
   x-obs-id-2: 32AAAQAAEAABAAAQAAEAABAAAQAAEAABCSD3nAiTaBoeyt9oHp9vTYtXnLDmwV6D
   Date: WED, 01 Jul 2015 04:19:21 GMT
   Content-Length: 0
   x-obs-metadata-directive:REPLACE
