:original_name: obs_04_0080.html

.. _obs_04_0080:

Uploading Objects - PUT
=======================

Functions
---------

After bucket creation in OBS, you can use this operation to upload an object to the bucket. Uploading an object adds it to a bucket. This requires users to have the write operation.

.. note::

   The name of each object in a bucket must be unique.

With versioning not enabled, if an object to be uploaded has the same name as an existing object in the bucket, the newly uploaded object will overwrite the existing one. To protect data from being corrupted during transmission, you can add the **Content-MD5** parameter in the request header. After receiving the request, OBS will perform an MD5 consistency check. If the two MD5 values are inconsistent, the system returns an error message.

You can also specify the value of the **x-obs-acl** parameter to configure an access control policy for the object. If the **x-obs-acl** parameter is not specified when an anonymous user uploads an object, the object can be accessed by all OBS users by default.

This operation supports server-side encryption.

For a single upload, the size of the object to be uploaded ranges [0, 5 GB]. To upload a file greater than 5 GB, see :ref:`Operations on Multipart Upload <obs_04_0096>`.

OBS does not have real folders. To facilitate data management, OBS provides a method to simulate a folder by adding a slash (/) to the object name, for example, **test/123.jpg**. You can simulate **test** as a folder and **123.jpg** as the name of a file under the **test** folder. However, the object key remains **test/123.jpg**. Objects named in this format appear as folders on the console.

Differences Between PUT and POST Methods
----------------------------------------

Parameters are passed through the request header if the PUT method is used to upload objects; if the POST method is used to upload objects, parameters are passed through the form field in the message body.

With the PUT method, you need to specify the object name in the URL, but object name is not required with the POST method, which uses the bucket domain name as the URL. The request lines of the two methods are as follows:

.. code-block:: text

   PUT /ObjectName HTTP/1.1

.. code-block:: text

   POST / HTTP/1.1

For details about POST upload, see :ref:`Uploading Objects - POST <obs_04_0081>`.

Versioning
----------

If versioning is enabled for a bucket, the system automatically generates a unique version ID for the requested object in this bucket and returns the version ID in response header **x-obs-version-id**. If versioning is suspended for the bucket, the object version ID is **null**. For details about the versioning statuses of a bucket, see :ref:`Configuring Versioning for a Bucket <obs_04_0037>`.

Request Syntax
--------------

.. code-block:: text

   PUT /ObjectName HTTP/1.1
   Host: bucketname.obs.region.example.com
   Content-Type: application/xml
   Content-Length: length
   Authorization: authorization
   Date: date
   <Optional Additional Header>
   <object Content>

Request Parameters
------------------

This request contains no parameters.

Request Headers
---------------

This request uses common headers. For details, see :ref:`Table 3 <obs_04_0007__table25197309>`. The request can use additional headers, as listed in :ref:`Table 1 <obs_04_0080__table21799862>`.

.. note::

   OBS supports the six HTTP request headers: Cache-Control, Expires, Content-Encoding, Content-Disposition, Content-Type, and Content-Language. If these headers are carried in an object upload request, their values are saved. You can also call the metadata modification API, provided by OBS, to change the values of the six headers. When the object is downloaded or queried, the saved values are set for corresponding HTTP headers and returned to the client.

.. _obs_04_0080__table21799862:

.. table:: **Table 1** Request headers

   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | Header                                          | Description                                                                                                                                                                                                                              | Mandatory                                         |
   +=================================================+==========================================================================================================================================================================================================================================+===================================================+
   | Content-MD5                                     | Base64-encoded 128-bit MD5 digest of the message according to RFC 1864.                                                                                                                                                                  | No                                                |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Example: **n58IG6hfM7vqI4K0vnWpog==**                                                                                                                                                                                                    |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-acl                                       | This header can be added to set access control policies for objects when creating the objects. The access control policies are the predefined common policies, including **private**, **public-read**, **public-read-write**.            | No                                                |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Note: This header is a predefined policy expressed in a character string.                                                                                                                                                                |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Example: **x-obs-acl: public-read**                                                                                                                                                                                                      |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-grant-read                                | When creating an object, you can use this header to authorize all users in an account the permission to read objects and obtain object metadata.                                                                                         | No                                                |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Example: **x-obs-grant-read: id=domainID**. If multiple accounts are authorized, separate them with commas (,).                                                                                                                          |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-grant-read-acp                            | When creating an object, you can use this header to authorize all users in an account the permission to obtain the object ACL.                                                                                                           | No                                                |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Example: **x-obs-grant-read-acp: id=domainID**. If multiple accounts are authorized, separate them with commas (,).                                                                                                                      |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-grant-write-acp                           | When creating an object, you can use this header to authorize all users in an account the permission to write the object ACL.                                                                                                            | No                                                |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Example: **x-obs-grant-write-acp: id=domainID**. If multiple accounts are authorized, separate them with commas (,).                                                                                                                     |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-grant-full-control                        | When creating an object, you can use this header to authorize all users in an account the permission to read the object, obtain the object metadata, obtain the object ACL, and write the object ACL.                                    | No                                                |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Example: **x-obs-grant-full-control: id=domainID**. If multiple accounts are authorized, separate them with commas (,).                                                                                                                  |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-storage-class                             | When creating an object, you can use this header to specify the storage class for the object. If you do not use this header, the object storage class is the default storage class of the bucket.                                        | No                                                |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Storage class value options: **STANDARD** (Standard), **WARM** (Warm), **COLD** (Cold). These values are case sensitive.                                                                                                                 |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Example: **x-obs-storage-class: STANDARD**                                                                                                                                                                                               |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-meta-\*                                   | When creating an object, you can use a header starting with **x-obs-meta-** to define object metadata in an HTTP request. Custom metadata will be returned in the response header when you retrieve or query the metadata of the object. | No                                                |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Example: **x-obs-meta-test: test metadata**                                                                                                                                                                                              |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-website-redirect-location                 | If a bucket is configured with the static website hosting function, it will redirect requests for this object to another object in the same bucket or to an external URL. OBS stores the value of this header in the object metadata.    | No                                                |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | In the following example, the request header sets the redirection to an object (**anotherPage.html**) in the same bucket:                                                                                                                |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | x-obs-website-redirect-location:/anotherPage.html                                                                                                                                                                                        |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | In the following example, the request header sets the object redirection to an external URL:                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | x-obs-website-redirect-location:http://www.example.com/                                                                                                                                                                                  |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Default value: none                                                                                                                                                                                                                      |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Constraint: The value must be prefixed by a slash (/), **http://**, or **https://**. The length of the value cannot exceed 2 KB.                                                                                                         |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-server-side-encryption                    | Indicates that SSE-KMS is used.                                                                                                                                                                                                          | No. This header is required when SSE-KMS is used. |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Example: **x-obs-server-side-encryption: kms**                                                                                                                                                                                           |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-server-side-encryption-kms-key-id         | Master key ID. This header is used in SSE-KMS mode. If the customer does not provide the master key ID, the default master key ID will be used.                                                                                          | No                                                |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | The following two formats are supported:                                                                                                                                                                                                 |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | 1. *regionID*\ **:**\ *domainID*\ **:key/**\ *key_id*                                                                                                                                                                                    |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | 2. *key*\ **\_**\ *id*                                                                                                                                                                                                                   |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | *regionID* is the ID of the region to which the key belongs. *domainID* is the account ID of the tenant to which the key belongs. *key_id* is the key ID created in KMS.                                                                 |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Example:                                                                                                                                                                                                                                 |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | 1. x-obs-server-side-encryption-kms-key-id:*region*:domainiddomainiddomainiddoma0001: key/4f1cd4de-ab64-4807-920a-47fc42e7f0d0                                                                                                           |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | 2. x-obs-server-side-encryption-kms-key-id: 4f1cd4de-ab64-4807-920a-47fc42e7f0d0                                                                                                                                                         |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-server-side-encryption-customer-algorithm | Encryption algorithm. The header is used in SSE-C mode.                                                                                                                                                                                  | No. This header is required when SSE-C is used.   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Example: **x-obs-server-side-encryption-customer-algorithm: AES256**                                                                                                                                                                     |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Constraint: This header must be used together with **x-obs-server-side-encryption-customer-key** and **x-obs-server-side-encryption-customer-key-MD5**.                                                                                  |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-server-side-encryption-customer-key       | Indicates a key used to encrypt objects. The header is used in SSE-C mode. This key is used to encrypt objects.                                                                                                                          | No. This header is required when SSE-C is used.   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Example: **x-obs-server-side-encryption-customer-key:K7QkYpBkM5+hca27fsNkUnNVaobncnLht/rCB2o/9Cw=**                                                                                                                                      |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Constraint: This header is a Base64-encoded 256-bit key and must be used together with **x-obs-server-side-encryption-customer-algorithm** and **x-obs-server-side-encryption-customer-key-MD5**.                                        |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-server-side-encryption-customer-key-MD5   | Indicates the MD5 value of a key used to encrypt objects. The header is used in SSE-C mode. The MD5 value is used to check whether any error occurs during the transmission of the key.                                                  | No. This header is required when SSE-C is used.   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Example: **x-obs-server-side-encryption-customer-key-MD5:4XvB3tbNTN+tIEVa0/fGaQ==**                                                                                                                                                      |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Constraint: This header is a Base64-encoded 128-bit MD5 value and must be used together with **x-obs-server-side-encryption-customer-algorithm** and **x-obs-server-side-encryption-customer-key**.                                      |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | success-action-redirect                         | Indicates the address (URL) to which a successfully responded request is redirected.                                                                                                                                                     | No                                                |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | -  If the value is valid and the request is successful, OBS returns status code 303. **Location** contains **success_action_redirect** as well as the bucket name, object name, and object ETag.                                         |                                                   |
   |                                                 | -  If this parameter is invalid, OBS ignores this parameter. The response code is 204, and the **Location** is the object address.                                                                                                       |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                             |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-expires                                   | Indicates the expiration time of an object, in days. An object will be automatically deleted once it expires (calculated from the last modification time of the object).                                                                 | No                                                |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | This field can be configured only when an object is uploaded and cannot be modified through the metadata modification API.                                                                                                               |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: integer                                                                                                                                                                                                                            |                                                   |
   |                                                 |                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Example: **x-obs-expires:3**                                                                                                                                                                                                             |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+

Request Elements
----------------

This request contains no elements. Its body contains only the content of the requested object.

Response Syntax
---------------

::

   HTTP/1.1 status_code
   Content-Length: length
   Content-Type: type

Response Headers
----------------

The response to the request uses common headers. For details, see :ref:`Table 1 <obs_04_0013__d0e686>`.

In addition to the common response headers, the following message headers may also be used. For details, see :ref:`Table 2 <obs_04_0080__table24122936102344>`.

.. _obs_04_0080__table24122936102344:

.. table:: **Table 2** Additional response header parameters

   +-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Header                                          | Description                                                                                                                                                                       |
   +=================================================+===================================================================================================================================================================================+
   | x-obs-version-id                                | Object version ID. If versioning is enabled for the bucket, the object version ID will be returned.                                                                               |
   |                                                 |                                                                                                                                                                                   |
   |                                                 | Type: string                                                                                                                                                                      |
   +-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption                    | This header is included in a response if SSE-KMS is used.                                                                                                                         |
   |                                                 |                                                                                                                                                                                   |
   |                                                 | Type: string                                                                                                                                                                      |
   |                                                 |                                                                                                                                                                                   |
   |                                                 | Example: **x-obs-server-side-encryption:kms**                                                                                                                                     |
   +-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption-kms-key-id         | Indicates the master key ID. This header is included in a response if SSE-KMS is used.                                                                                            |
   |                                                 |                                                                                                                                                                                   |
   |                                                 | Type: string                                                                                                                                                                      |
   |                                                 |                                                                                                                                                                                   |
   |                                                 | Format: *regionID*\ **:**\ *domainID*\ **:key/**\ *key_id*                                                                                                                        |
   |                                                 |                                                                                                                                                                                   |
   |                                                 | *regionID* is the ID of the region to which the key belongs. *domainID* is the account ID of the tenant to which the key belongs. *key_id* is the key ID used in this encryption. |
   |                                                 |                                                                                                                                                                                   |
   |                                                 | Example: **x-obs-server-side-encryption-kms-key-id:**\ *region*\ **:domainiddomainiddomainiddoma0001:key/4f1cd4de-ab64-4807-920a-47fc42e7f0d0**                                   |
   +-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption-customer-algorithm | An encryption algorithm. This header is included in a response if SSE-C is used.                                                                                                  |
   |                                                 |                                                                                                                                                                                   |
   |                                                 | Type: string                                                                                                                                                                      |
   |                                                 |                                                                                                                                                                                   |
   |                                                 | Example: **x-obs-server-side-encryption-customer-algorithm:AES256**                                                                                                               |
   +-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption-customer-key-MD5   | The MD5 value of a key used to encrypt objects. This header is included in a response if SSE-C is used.                                                                           |
   |                                                 |                                                                                                                                                                                   |
   |                                                 | Type: string                                                                                                                                                                      |
   |                                                 |                                                                                                                                                                                   |
   |                                                 | Example: **x-obs-server-side-encryption-customer-key-MD5:4XvB3tbNTN+tIEVa0/fGaQ==**                                                                                               |
   +-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-storage-class                             | This header is returned when the storage class of an object is not Standard. The value can be **WARM** or **COLD**.                                                               |
   |                                                 |                                                                                                                                                                                   |
   |                                                 | Type: string                                                                                                                                                                      |
   +-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Elements
-----------------

This response involves no elements.

Error Responses
---------------

No special error responses are returned. For details about error responses, see :ref:`Table 2 <obs_04_0115__d0e843>`.

Sample Request 1
----------------

**Upload an object.**

.. code-block:: text

   PUT /object01 HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: WED, 01 Jul 2015 04:11:15 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:gYqplLq30dEX7GMi2qFWyjdFsyw=
   Content-Length: 10240
   Expect: 100-continue

   [1024 Byte data content]

Sample Response 1
-----------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: BF2600000164364C10805D385E1E3C67
   ETag: "d41d8cd98f00b204e9800998ecf8427e"
   x-obs-id-2: 32AAAWJAMAABAAAQAAEAABAAAQAAEAABCTzu4Jp2lquWuXsjnLyPPiT3cfGhqPoY
   Date: WED, 01 Jul 2015 04:11:15 GMT
   Content-Length: 0

Sample Request 2
----------------

**Set the ACL when uploading an object.**

.. code-block:: text

   PUT /object01 HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: WED, 01 Jul 2015 04:13:55 GMT
   x-obs-grant-read:id=52f24s3593as5730ea4f722483579ai7,id=a93fcas852f24s3596ea8366794f7224
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:gYqplLq30dEX7GMi2qFWyjdFsyw=
   Content-Length: 10240
   Expect: 100-continue

   [1024 Byte data content]

Sample Response 2
-----------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: BB7800000164845759E4F3B39ABEE55E
   ETag: "d41d8cd98f00b204e9800998ecf8427e"
   x-obs-id-2: 32AAAQAAEAABAAAQAAEAABAAAQAAEAABCSReVRNuas0knI+Y96iXrZA7BLUgj06Z
   Date: WED, 01 Jul 2015 04:13:55 GMT
   Content-Length: 0

Sample Request 3
----------------

**Upload objects when versioning is enabled for the bucket.**

.. code-block:: text

   PUT /object01 HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: WED, 01 Jul 2015 04:17:12 GMT
   x-obs-storage-class: WARM
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:uFVJhp/dJqj/CJIVLrSZ0gpw3ng=
   Content-Length: 10240
   Expect: 100-continue

   [1024 Byte data content]

Sample Response 3
-----------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: DCD2FC9CAB78000001439A51DB2B2577
   ETag: "d41d8cd98f00b204e9800998ecf8427e"
   X-OBS-ID-2: GcVgfeOJHx8JZHTHrRqkPsbKdB583fYbr3RBbHT6mMrBstReVILBZbMAdLiBYy1l
   Date: WED, 01 Jul 2015 04:17:12 GMT
   x-obs-version-id: AAABQ4q2M9_c0vycq3gAAAAAVURTRkha
   Content-Length: 0

Sample Request 4
----------------

**MD5 is carried when an object is uploaded.**

.. code-block:: text

   PUT /object01 HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: WED, 01 Jul 2015 04:17:50 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:uFVJhp/dJqj/CJIVLrSZ0gpw3ng=
   Content-Length: 10
   Content-MD5: 6Afx/PgtEy+bsBjKZzihnw==
   Expect: 100-continue

   1234567890

Sample Response 4
-----------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: BB7800000164B165971F91D82217D105
   X-OBS-ID-2: 32AAAUJAIAABAAAQAAEAABAAAQAAEAABCSEKhBpS4BB3dSMNqMtuNxQDD9XvOw5h
   ETag: "1072e1b96b47d7ec859710068aa70d57"
   Date: WED, 01 Jul 2015 04:17:50 GMT
   Content-Length: 0

Sample Request 5
----------------

**If static website hosting has been configured for a bucket, you can configure parameters as follows when you upload an object. Then, users will be redirected when they download the object.**

.. code-block:: text

   PUT /object01 HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: WED, 01 Jul 2015 04:17:12 GMT
   x-obs-website-redirect-location: http://www.example.com/
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:uFVJhp/dJqj/CJIVLrSZ0gpw3ng=
   Content-Length: 10240
   Expect: 100-continue

   [1024 Byte data content]

Sample Response 5
-----------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: DCD2FC9CAB78000001439A51DB2B2577
   x-obs-id-2: 32AAAUJAIAABAAAQAAEAABAAAQAAEAABCTmxB5ufMj/7/GzP8TFwTbp33u0xhn2Z
   ETag: "1072e1b96b47d7ec859710068aa70d57"
   Date: WED, 01 Jul 2015 04:17:12 GMT
   x-obs-version-id: AAABQ4q2M9_c0vycq3gAAAAAVURTRkha
   Content-Length: 0

Sample Request 6
----------------

**Upload an object and carry the signature in the URL**.

.. code-block:: text

   PUT /object02?AccessKeyId=H4IPJX0TQTHTHEBQQCEC&Expires=1532688887&Signature=EQmDuOhaLUrzrzRNZxwS72CXeXM%3D HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Content-Length: 1024

   [1024 Byte data content]

Sample Response 6
-----------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: DCD2FC9CAB78000001439A51DB2B2577
   x-obs-id-2: 32AAAUJAIAABAAAQAAEAABAAAQAAEAABCTmxB5ufMj/7/GzP8TFwTbp33u0xhn2Z
   ETag: "1072e1b96b47d7ec859710068aa70d57"
   Date: Fri, 27 Jul 2018 10:52:31 GMT
   x-obs-version-id: AAABQ4q2M9_c0vycq3gAAAAAVURTRkha
   Content-Length: 0

Sample Request 7
----------------

**Upload an object of a specified storage class.**

.. code-block:: text

   PUT /object01 HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: WED, 01 Jul 2015 04:15:07 GMT
   x-obs-storage-class: WARM
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:uFVJhp/dJqj/CJIVLrSZ0gpw3ng=
   Content-Length: 10240
   Expect: 100-continue

   [1024 Byte data content]

Sample Response 7
-----------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: BB7800000164846A2112F98BF970AA7E
   ETag: "d41d8cd98f00b204e9800998ecf8427e"
   x-obs-id-2: a39E0UgAIAABAAAQAAEAABAAAQAAEAABCTPOUJu5XlNyU32fvKjM/92MQZK2gtoB
   Date: WED, 01 Jul 2015 04:15:07 GMT
   Content-Length: 0
