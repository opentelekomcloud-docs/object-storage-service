:original_name: obs_04_0083.html

.. _obs_04_0083:

Downloading Objects
===================

Functions
---------

This operation downloads objects from OBS. Before using this GET operation, check that you have the read permission for the target object. If the object owner has granted anonymous users the read permission for the object, anonymous users can access this object without using the authentication header field.

Server-Side Encryption
----------------------

If the object uploaded to the server is encrypted on the server using the encryption key provided by the client, downloading the object requires including the encryption key in the message.

Versioning
----------

By default, the GET operation returns the current version of an object. If the current version of the object is a deletion marker, OBS returns a code meaning non-existence of the object. To obtain an object of a specified version, the **versionId** parameter can be used to specify the desired version.

OBS Cold Objects
----------------

If the object to be downloaded is a Cold object, restore it before downloading it. The response varies with the retrieval status of the object. If the object has been restored, the **x-obs-restore** header is returned indicating the expiry date of the object when it is successfully downloaded. If you request downloading Cold objects that are not restored or are being restored, a **403 Forbidden** error is returned.

Request Syntax
--------------

.. code-block:: text

   GET /ObjectName HTTP/1.1
   Host: bucketname.obs.region.example.com
   Date: date
   Authorization: authorization
   Range:bytes=byte_range
   <Optional Additional Header>

.. note::

   The field is optional. If it does not exist, you can obtain the whole content.

Request Parameters
------------------

In a **GET** request, you can override values for a set of message headers using the request parameters. Message headers that you can override are **Content-Type**, **Content-Language**, **Expires**, **Cache-Control**, **Content-Disposition**, and **Content-Encoding**. If the target object has multiple versions, use the **versionId** parameter to specify the version to be downloaded. For details, see :ref:`Table 1 <obs_04_0083__table33454552>`.

.. note::

   OBS does not process Accept-Encoding carried in a request or compress or decompress the uploaded data. The client determines whether to compress or decompress the data. Some HTTP clients may decompress data based on the Content-Encoding returned by the server. The client program needs to determine whether to decompress and how to decompress the data. To decompress the data, it can modify Content-Encoding (the object metadata stored in OBS) or rewrite Content-Encoding the object is downloaded. If an object download request specifies the rewrite header, the standard HTTP message header returned by OBS is subject to the rewrite content specified in the request.

.. _obs_04_0083__table33454552:

.. table:: **Table 1** Request parameters

   +------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter                    | Description                                                                                                                       | Mandatory             |
   +==============================+===================================================================================================================================+=======================+
   | response-content-type        | Rewrites the **Content-Type** header in the response.                                                                             | No                    |
   |                              |                                                                                                                                   |                       |
   |                              | Type: string                                                                                                                      |                       |
   +------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | response-content-language    | Rewrites the **Content-Language** header in the response.                                                                         | No                    |
   |                              |                                                                                                                                   |                       |
   |                              | Type: string                                                                                                                      |                       |
   +------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | response-expires             | Rewrites the **Expires** header in the response.                                                                                  | No                    |
   |                              |                                                                                                                                   |                       |
   |                              | Type: string                                                                                                                      |                       |
   +------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | response-cache-control       | Rewrites the **Cache-Control** header in the response.                                                                            | No                    |
   |                              |                                                                                                                                   |                       |
   |                              | Type: string                                                                                                                      |                       |
   +------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | response-content-disposition | Rewrites the **Content-Disposition** header in the response.                                                                      | No                    |
   |                              |                                                                                                                                   |                       |
   |                              | Type: string                                                                                                                      |                       |
   |                              |                                                                                                                                   |                       |
   |                              | Example:                                                                                                                          |                       |
   |                              |                                                                                                                                   |                       |
   |                              | response-content-disposition=attachment; filename*=utf-8''name1                                                                   |                       |
   |                              |                                                                                                                                   |                       |
   |                              | In this example, the downloaded object is renamed **name1**. If the new name contains Chinese characters, it must be URL-encoded. |                       |
   +------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | response-content-encoding    | Rewrites the **Content-Encoding** header in the response.                                                                         | No                    |
   |                              |                                                                                                                                   |                       |
   |                              | Type: string                                                                                                                      |                       |
   +------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | versionId                    | Indicates the version ID of the object whose content is obtained.                                                                 | No                    |
   |                              |                                                                                                                                   |                       |
   |                              | Type: string                                                                                                                      |                       |
   +------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | attname                      | Rewrites the **Content-Disposition** header in the response.                                                                      | No                    |
   |                              |                                                                                                                                   |                       |
   |                              | Type: string                                                                                                                      |                       |
   |                              |                                                                                                                                   |                       |
   |                              | Example:                                                                                                                          |                       |
   |                              |                                                                                                                                   |                       |
   |                              | attname=name1                                                                                                                     |                       |
   |                              |                                                                                                                                   |                       |
   |                              | Rename the downloaded object as **name1**.                                                                                        |                       |
   +------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------+

Request Headers
---------------

This request uses common headers. In addition, you can add additional headers to this request. :ref:`Table 2 <obs_04_0083__table14222149>` describes the additional headers.

.. _obs_04_0083__table14222149:

.. table:: **Table 2** Request headers

   +-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
   | Header                                          | Description                                                                                                                                                                                                                                                  | Mandatory                                       |
   +=================================================+==============================================================================================================================================================================================================================================================+=================================================+
   | Range                                           | Obtains the object content within the scope defined by **Range**. If the parameter value is invalid, the entire object is obtained.                                                                                                                          | No                                              |
   |                                                 |                                                                                                                                                                                                                                                              |                                                 |
   |                                                 | **Range** value starts from 0, and the maximum value equals the object length minus 1. The start value of **Range** is mandatory. If only the start value is specified, the system obtains the object content from the start value to default maximum value. |                                                 |
   |                                                 |                                                                                                                                                                                                                                                              |                                                 |
   |                                                 | After the **Range** header field is carried, the value of ETag in the response message is the ETag of the object instead of the ETag of the object in the **Range** field.                                                                                   |                                                 |
   |                                                 |                                                                                                                                                                                                                                                              |                                                 |
   |                                                 | Type: string                                                                                                                                                                                                                                                 |                                                 |
   |                                                 |                                                                                                                                                                                                                                                              |                                                 |
   |                                                 | bytes=byte_range                                                                                                                                                                                                                                             |                                                 |
   |                                                 |                                                                                                                                                                                                                                                              |                                                 |
   |                                                 | Example 1: **bytes=0-4**                                                                                                                                                                                                                                     |                                                 |
   |                                                 |                                                                                                                                                                                                                                                              |                                                 |
   |                                                 | Example 2: **bytes=1024**                                                                                                                                                                                                                                    |                                                 |
   |                                                 |                                                                                                                                                                                                                                                              |                                                 |
   |                                                 | Example 3: **bytes=10-20, 30-40** (multiple ranges)                                                                                                                                                                                                          |                                                 |
   +-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
   | If-Modified-Since                               | Returns the object only if it has been modified since the time specified by this header. Otherwise, **304 Not Modified** is returned.                                                                                                                        | No                                              |
   |                                                 |                                                                                                                                                                                                                                                              |                                                 |
   |                                                 | Type: HTTP time character string complying with the format specified at **http://www.ietf.org/rfc/rfc2616.txt**                                                                                                                                              |                                                 |
   +-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
   | If-Unmodified-Since                             | Returns the object only if it has not been modified since the time specified by this header. Otherwise, **412 Precondition Failed** is returned.                                                                                                             | No                                              |
   |                                                 |                                                                                                                                                                                                                                                              |                                                 |
   |                                                 | Type: HTTP time character string complying with the format specified at **http://www.ietf.org/rfc/rfc2616.txt**                                                                                                                                              |                                                 |
   +-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
   | If-Match                                        | Returns the object only if its ETag is the same as the one specified by this header. Otherwise, **412 Precondition Failed** is returned.                                                                                                                     | No                                              |
   |                                                 |                                                                                                                                                                                                                                                              |                                                 |
   |                                                 | Type: string                                                                                                                                                                                                                                                 |                                                 |
   |                                                 |                                                                                                                                                                                                                                                              |                                                 |
   |                                                 | (Example: 0f64741bf7cb1089e988e4585d0d3434)                                                                                                                                                                                                                  |                                                 |
   +-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
   | If-None-Match                                   | Returns the object only if its ETag is different from the one specified by this header. Otherwise, **304 Not Modified** is returned.                                                                                                                         | No                                              |
   |                                                 |                                                                                                                                                                                                                                                              |                                                 |
   |                                                 | Type: string                                                                                                                                                                                                                                                 |                                                 |
   |                                                 |                                                                                                                                                                                                                                                              |                                                 |
   |                                                 | (Example: 0f64741bf7cb1089e988e4585d0d3434)                                                                                                                                                                                                                  |                                                 |
   +-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
   | x-obs-server-side-encryption-customer-algorithm | Indicates an encryption algorithm. The header is used in SSE-C mode.                                                                                                                                                                                         | No. This header is required when SSE-C is used. |
   |                                                 |                                                                                                                                                                                                                                                              |                                                 |
   |                                                 | Type: string                                                                                                                                                                                                                                                 |                                                 |
   |                                                 |                                                                                                                                                                                                                                                              |                                                 |
   |                                                 | Example: x-obs-server-side-encryption-customer-algorithm:AES256                                                                                                                                                                                              |                                                 |
   |                                                 |                                                                                                                                                                                                                                                              |                                                 |
   |                                                 | Constraint: This header must be used together with **x-obs-server-side-encryption-customer-key** and **x-obs-server-side-encryption-customer-key-MD5**.                                                                                                      |                                                 |
   +-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
   | x-obs-server-side-encryption-customer-key       | Indicates a key used to encrypt objects. The header is used in SSE-C mode. This key is used to decrypt objects.                                                                                                                                              | No. This header is required when SSE-C is used. |
   |                                                 |                                                                                                                                                                                                                                                              |                                                 |
   |                                                 | Type: string                                                                                                                                                                                                                                                 |                                                 |
   |                                                 |                                                                                                                                                                                                                                                              |                                                 |
   |                                                 | Example: x-obs-server-side-encryption-customer-key:K7QkYpBkM5+hca27fsNkUnNVaobncnLht/rCB2o/9Cw=                                                                                                                                                              |                                                 |
   |                                                 |                                                                                                                                                                                                                                                              |                                                 |
   |                                                 | Constraint: This header is a Base64-encoded 256-bit key and must be used together with **x-obs-server-side-encryption-customer-algorithm** and **x-obs-server-side-encryption-customer-key-MD5**.                                                            |                                                 |
   +-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
   | x-obs-server-side-encryption-customer-key-MD5   | Indicates the MD5 value of a key used to encrypt objects. The header is used in SSE-C mode. The MD5 value is used to check whether any error occurs during the transmission of the key.                                                                      | No. This header is required when SSE-C is used. |
   |                                                 |                                                                                                                                                                                                                                                              |                                                 |
   |                                                 | Type: string                                                                                                                                                                                                                                                 |                                                 |
   |                                                 |                                                                                                                                                                                                                                                              |                                                 |
   |                                                 | Example: x-obs-server-side-encryption-customer-key-MD5:4XvB3tbNTN+tIEVa0/fGaQ==                                                                                                                                                                              |                                                 |
   |                                                 |                                                                                                                                                                                                                                                              |                                                 |
   |                                                 | Constraint: This header is a Base64-encoded 128-bit MD5 value and must be used together with **x-obs-server-side-encryption-customer-algorithm** and **x-obs-server-side-encryption-customer-key**.                                                          |                                                 |
   +-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------+

Request Elements
----------------

This request involves no elements.

Response Syntax
---------------

::

   HTTP/1.1 status_code
   Content-Type: type
   Date: date
   Content-Length: length
   Etag: etag
   Last-Modified: time

   <Object Content>

Response Headers
----------------

The response to the request uses common headers. For details, see :ref:`Table 1 <obs_04_0013__d0e686>`.

In addition to the common response headers, the following message headers may also be used. For details, see :ref:`Table 3 <obs_04_0083__table40465940>`.

.. _obs_04_0083__table40465940:

.. table:: **Table 3** Additional response header parameters

   +-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Header                                          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   +=================================================+================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | x-obs-expiration                                | When an object has its lifecycle rule, the object expiration time is subject to its lifecycle rule. This header field is use **expiry-date** to describe the object expiration date. If the lifecycle rule is configured only for the entire bucket not individual objects, the object expiration time is subject to the bucket lifecycle rule. This header field uses the **expiry-date** and **rule-id** to describe the detailed expiration information of objects. If no lifecycle rule is configured, this header field is not contained in the response. |
   |                                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   |                                                 | Type: string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
   +-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-website-redirect-location                 | Indicates the redirected-to location. If the bucket is configured with website information, this parameter can be set for the object metadata so that the website endpoint will evaluate the request for the object as a 301 redirect to another object in the same bucket or an external URL.                                                                                                                                                                                                                                                                 |
   |                                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   |                                                 | Type: string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
   +-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-delete-marker                             | Indicates whether an object is a deletion marker. If the object is not marked as deleted, the response does not contain this header.                                                                                                                                                                                                                                                                                                                                                                                                                           |
   |                                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   |                                                 | Type: boolean                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
   |                                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   |                                                 | Valid values: **true** or **false**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
   |                                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   |                                                 | The default value is **false**.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   +-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-version-id                                | Object version ID. If the object has no version number specified, the response does not contain this header.                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   |                                                 | Valid value: character string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
   |                                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   |                                                 | Default value: none                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
   +-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption                    | This header is included in a response if SSE-KMS is used.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   |                                                 | Type: string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   |                                                 | Example: x-obs-server-side-encryption:kms                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   +-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption-kms-key-id         | Indicates the master key ID. This header is included in a response if SSE-KMS is used.                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
   |                                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   |                                                 | Type: string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   |                                                 | Format: *regionID*\ **:**\ *domainID*\ **:key/**\ *key_id*                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
   |                                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   |                                                 | *regionID* is the ID of the region to which the key belongs. *domainID* is the account ID of the tenant to which the key belongs. *key_id* is the key ID used in this encryption.                                                                                                                                                                                                                                                                                                                                                                              |
   |                                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   |                                                 | Example: **x-obs-server-side-encryption-kms-key-id:region:domainiddomainiddomainiddoma0001:key/4f1cd4de-ab64-4807-920a-47fc42e7f0d0**                                                                                                                                                                                                                                                                                                                                                                                                                          |
   +-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption-customer-algorithm | Indicates a decryption algorithm. This header is included in a response if SSE-C is used.                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   |                                                 | Type: string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   |                                                 | Example: x-obs-server-side-encryption-customer-algorithm:AES256                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   +-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption-customer-key-MD5   | Indicates the MD5 value of a key used to decrypt objects. This header is included in a response if SSE-C is used.                                                                                                                                                                                                                                                                                                                                                                                                                                              |
   |                                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   |                                                 | Type: string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   |                                                 | Example: x-obs-server-side-encryption-customer-key-MD5:4XvB3tbNTN+tIEVa0/fGaQ==                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   +-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-object-type                               | If the object is not a normal one, this header field is returned. The value can be **Appendable**.                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
   |                                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   |                                                 | Type: string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
   +-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-next-append-position                      | This header field is returned when the object is an appendable object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
   |                                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   |                                                 | Type: integer                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
   +-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Elements
-----------------

This response involves no elements.

Error Responses
---------------

No special error responses are returned. For details about error responses, see :ref:`Table 2 <obs_04_0115__d0e843>`.

Sample Request 1
----------------

**Download the entire object.**

.. code-block:: text

   GET /object01 HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: WED, 01 Jul 2015 04:24:33 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:NxtSMS0jaVxlLnxlO9awaMTn47s=

Sample Response 1
-----------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: 8DF400000163D3F2A89604C49ABEE55E
   Accept-Ranges: bytes
   ETag: "3b46eaf02d3b6b1206078bb86a7b7013"
   Last-Modified: WED, 01 Jul 2015 01:20:29 GMT
   Content-Type: binary/octet-stream
   x-obs-id-2: 32AAAQAAEAABAAAQAAEAABAAAQAAEAABCSQwxJ2I1VvxD/Xgwuw2G2RQax30gdXU
   Date: WED, 01 Jul 2015 04:24:33 GMT
   Content-Length: 4572

   [4572 Bytes object content]

Sample Request 2
----------------

**Download the specified range of an object (download a range of an object)**.

.. code-block:: text

   GET /object01 HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: Mon, 14 Sep 2020 09:59:04 GMT
   Range:bytes=20-30
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:mNPLWQMDWg30PTkAWiqJaLl3ALg=

**Download the specified range of an object (download multiple ranges of an object)**.

.. code-block:: text

   GET /object01 HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: Mon, 14 Sep 2020 10:02:43 GMT
   Range:bytes=20-30,40-50
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:ZwM7Vk2d7sD9o8zRsRKehgKQDkk=

Sample Response 2
-----------------

**Download the specified range of an object (download a range of an object)**.

::

   HTTP/1.1 206 Partial Content
   Server: OBS
   x-obs-request-id: 000001748C0DBC35802E360C9E869F31
   Accept-Ranges: bytes
   ETag: "2200446c2082f27ed2a569601ca4e360"
   Last-Modified: Mon, 14 Sep 2020 01:16:20 GMT
   Content-Range: bytes 20-30/4583
   Content-Type: binary/octet-stream
   x-obs-id-2: 32AAAQAAEAABAAAQAAEAABAAAQAAEAABCSn2JHu4okx9NBRNZAvBGawa3lt3g31g
   Date: Mon, 14 Sep 2020 09:59:04 GMT
   Content-Length: 11

   [ 11 Bytes object content]

**Download the specified range of an object (download multiple ranges of an object)**.

::

   HTTP/1.1 206 Partial Content
   Server: OBS
   x-obs-request-id: 8DF400000163D3F2A89604C49ABEE55E
   Accept-Ranges: bytes
   ETag: "2200446c2082f27ed2a569601ca4e360"
   Last-Modified: Mon, 14 Sep 2020 01:16:20 GMT
   Content-Type: multipart/byteranges;boundary=35bcf444-e65f-4c76-9430-7e4a68dd3d26
   x-obs-id-2: 32AAAQAAEAABAAAQAAEAABAAAQAAEAABCSIBWFOVW8eeWujkqSnoIANC2mNR1cdF
   Date: Mon, 14 Sep 2020 10:02:43 GMT
   Content-Length: 288

   --35bcf444-e65f-4c76-9430-7e4a68dd3d26
   Content-type: binary/octet-stream
   Content-range: bytes 20-30/4583
   [ 11 Bytes object content]
   --35bcf444-e65f-4c76-9430-7e4a68dd3d26
   Content-type: binary/octet-stream
   Content-range: bytes 40-50/4583
   [ 11 Bytes object content]
   --35bcf444-e65f-4c76-9430-7e4a68dd3d26

Sample Request 4
----------------

**Download an object if its Etag value matches**.

.. code-block:: text

   GET /object01 HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: WED, 01 Jul 2015 04:24:33 GMT
   If-Match: 682e760adb130c60c120da3e333a8b09
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:NxtSMS0jaVxlLnxlO9awaMTn47s=

Sample Response 4-1 (Non-Matched Etag)
--------------------------------------

If the Etag value of the stored object is not **682e760adb130c60c120da3e333a8b09**, the system displays a message indicating that the download fails.

::

   HTTP/1.1 412 Precondition Failed
   Server: OBS
   x-obs-request-id: 8DF400000163D3F2A89604C49ABEE55E
   Content-Type: application/xml
   x-obs-id-2: 32AAAQAAEAABAAAQAAEAABAAAQAAEAABCSQwxJ2I1VvxD/Xgwuw2G2RQax30gdXU
   Date: WED, 01 Jul 2015 04:20:51 GMT

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <Error>
     <Code>PreconditionFailed</Code>
     <Message>At least one of the pre-conditions you specified did not hold</Message>
     <RequestId>8DF400000163D3F2A89604C49ABEE55E</RequestId>
     <HostId>ha0ZGaSKVm+uLOrCXXtx4Qn1aLzvoeblctVXRAqA7pty10mzUUW/yOzFue04lBqu</HostId>
     <Condition>If-Match</Condition>
   </Error>

Sample Response 4-2 (Successful Download)
-----------------------------------------

If the Etag value of the stored object is **682e760adb130c60c120da3e333a8b09**, the download is successful.

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: 5DEB00000164A21E1FC826C58F6BA001
   Accept-Ranges: bytes
   ETag: "682e760adb130c60c120da3e333a8b09"
   Last-Modified: Mon, 16 Jul 2015 08:03:34 GMT
   Content-Type: application/octet-stream
   x-obs-id-2: 32AAAQAAEAABAAAQAAEAABAAAQAAEAABCSbkdml1sLSvKnoHaRcOwRI+6+ustDwk
   Date: Mon, 16 Jul 2015 08:04:00 GMT
   Content-Length: 8

   [ 8 Bytes object content]

Sample Request 5
----------------

**Carry the signature in the URL when downloading an object**.

.. code-block:: text

   GET /object02?AccessKeyId=H4IPJX0TQTHTHEBQQCEC&Expires=1532688887&Signature=EQmDuOhaLUrzrzRNZxwS72CXeXM%3D HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: Fri, 27 Jul 2018 10:52:31 GMT

Sample Response 5
-----------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: 804F00000164DB5E5B7FB908D3BA8E00
   ETag: "682e760adb130c60c120da3e333a8b09"
   Last-Modified: Mon, 16 Jul 2015 08:03:34 GMT
   Content-Type: application/octet-stream
   x-obs-id-2: 32AAAUJAIAABAAAQAAEAABAAAQAAEAABCTlpxILjhVK/heKOWIP8Wn2IWmQoerfw
   Date: Fri, 27 Jul 2018 10:52:31 GMT
   Content-Length: 8

   [ 8 Bytes object content]

Sample Request 6
----------------

**Use the** **response-content-disposition** **parameter to download and rename an object.**

.. code-block:: text

   GET /object01?response-content-disposition=attachment; filename*=utf-8''name1 HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: WED, 01 Jul 2015 04:24:33 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:NxtSMS0jaVxlLnxlO9awaMTn47s=

Sample Response 6
-----------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: 804F00000164DB5E5B7FB908D3BA8E00
   ETag: "682e760adb130c60c120da3e333a8b09"
   Last-Modified: Mon, 16 Jul 2015 08:03:34 GMT
   Content-Type: application/octet-stream
   x-obs-id-2: 32AAAUJAIAABAAAQAAEAABAAAQAAEAABCTlpxILjhVK/heKOWIP8Wn2IWmQoerfw
   Date: Fri, 27 Jul 2018 10:52:31 GMT
   Content-Length: 8
   Content-Disposition: attachment; filename*=utf-8''name1

   [ 8 Bytes object content]

Sample Request 7
----------------

**Use the** **attname** **parameter to download and rename an object.**

.. code-block:: text

   GET /object01?attname=name1 HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: WED, 01 Jul 2015 04:24:33 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:NxtSMS0jaVxlLnxlO9awaMTn47s=

Sample Response 7
-----------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: 804F00000164DB5E5B7FB908D3BA8E00
   ETag: "682e760adb130c60c120da3e333a8b09"
   Last-Modified: Mon, 16 Jul 2015 08:03:34 GMT
   Content-Type: application/octet-stream
   x-obs-id-2: 32AAAUJAIAABAAAQAAEAABAAAQAAEAABCTlpxILjhVK/heKOWIP8Wn2IWmQoerfw
   Date: Fri, 27 Jul 2018 10:52:31 GMT
   Content-Length: 8
   Content-Disposition: attachment; filename*=utf-8''name1

   [ 8 Bytes object content]
