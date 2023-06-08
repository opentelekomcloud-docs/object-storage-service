:original_name: obs_04_0081.html

.. _obs_04_0081:

Uploading Objects - POST
========================

Functions
---------

This operation uploads an object to a bucket. To use this operation, you must have the write permission on the bucket.

.. note::

   The name of each object in a bucket must be unique.

With versioning not enabled, if an object to be uploaded has the same name as an existing object in the bucket, the newly uploaded object will overwrite the existing one. To protect data from being corrupted during transmission, you can add the **Content-MD5** parameter in the form field. After receiving the request, OBS will perform an MD5 consistency check. If the two MD5 values are inconsistent, the system returns an error message. You can also specify the value of the **x-obs-acl** parameter to configure an access control policy for the object.

You can also upload an object using the POST method.

For a single upload, the size of the object to be uploaded ranges [0, 5 GB]. To upload a file greater than 5 GB, see :ref:`Operations on Multipart Upload <obs_04_0096>`.

This operation supports server-side encryption.

Differences Between PUT and POST Methods
----------------------------------------

Parameters are passed through the request header if the PUT method is used to upload objects; if the POST method is used to upload objects, parameters are passed through the form field in the message body.

With the PUT method, you need to specify the object name in the URL, but object name is not required with the POST method, which uses the bucket domain name as the URL. The request lines of the two methods are as follows:

.. code-block:: text

   PUT /ObjectName HTTP/1.1

.. code-block:: text

   POST / HTTP/1.1

For details about PUT upload, see :ref:`Uploading Objects - PUT <obs_04_0080>`.

Versioning
----------

If versioning is enabled for a bucket, the system automatically generates a unique version ID for the requested object in this bucket and returns the version ID in response header **x-obs-version-id**. If versioning is suspended for a bucket, the version ID of the requested object in this bucket is **null**. For details about the versioning statuses of a bucket, see :ref:`Configuring Versioning for a Bucket <obs_04_0037>`.

Request Syntax
--------------

.. code-block:: text

   POST / HTTP/1.1
   Host: bucketname.obs.region.example.com
   User-Agent: browser_data
   Accept: file_types
   Accept-Language: Regions
   Accept-Encoding: encoding
   Accept-Charset: character_set
   Keep-Alive: 300
   Connection: keep-alive
   Content-Type: multipart/form-data; boundary=9431149156168
   Content-Length: length


   --9431149156168
   Content-Disposition: form-data; name="key"

   acl
   --9431149156168
   Content-Disposition: form-data; name="success_action_redirect"

   success_redirect
   --9431149156168
   Content-Disposition: form-data; name="content-Type"

   content_type
   --9431149156168
   Content-Disposition: form-data; name="x-obs-meta-uuid"

   uuid
   --9431149156168
   Content-Disposition: form-data; name="x-obs-meta-tag"

   metadata
   --9431149156168
   Content-Disposition: form-data; name="AccessKeyId"

   access-key-id
   --9431149156168
   Content-Disposition: form-data; name="policy"

   encoded_policy
   --9431149156168
   Content-Disposition: form-data; name="signature"

   signature=
   --9431149156168
   Content-Disposition: form-data; name="file"; filename="MyFilename"
   Content-Type: image/jpeg

   file_content
   --9431149156168
   Content-Disposition: form-data; name="submit"

   Upload to OBS
   --9431149156168--

Request Parameters
------------------

This request contains no parameters.

Request Headers
---------------

This request uses common headers. For details, see :ref:`Table 3 <obs_04_0007__table25197309>`.

If you want to get CORS configuration information, you must use the headers in :ref:`Table 1 <obs_04_0081__table45572552212656>`.

.. _obs_04_0081__table45572552212656:

.. table:: **Table 1** Request headers for obtaining CORS configuration

   +--------------------------------+--------------------------------------------------------------------------------------------------+-----------------------+
   | Header                         | Description                                                                                      | Mandatory             |
   +================================+==================================================================================================+=======================+
   | Origin                         | Origin of the cross-domain request specified by the pre-request. Generally, it is a domain name. | Yes                   |
   |                                |                                                                                                  |                       |
   |                                | Type: string                                                                                     |                       |
   +--------------------------------+--------------------------------------------------------------------------------------------------+-----------------------+
   | Access-Control-Request-Headers | Indicates the HTTP headers of a request. The request can use multiple HTTP headers.              | No                    |
   |                                |                                                                                                  |                       |
   |                                | Type: string                                                                                     |                       |
   +--------------------------------+--------------------------------------------------------------------------------------------------+-----------------------+

Request Elements
----------------

This request uses form elements. :ref:`Table 2 <obs_04_0081__table13225554>` describes the form elements.

.. _obs_04_0081__table13225554:

.. table:: **Table 2** Form elements

   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | Parameter                                       | Description                                                                                                                                                                                                                                                                              | Mandatory                                         |
   +=================================================+==========================================================================================================================================================================================================================================================================================+===================================================+
   | file                                            | Indicates the content of the object to be uploaded.                                                                                                                                                                                                                                      | Yes                                               |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: binary content or text                                                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Constraint: This parameter must be the last parameter in a form. Otherwise, parameters after this parameter will be all discarded. Additionally, each request contains only one file parameter.                                                                                          |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | key                                             | Indicates the name of the object to be created.                                                                                                                                                                                                                                          | Yes                                               |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                                                             |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | AccessKeyId                                     | Access key ID (AK) of the requester.                                                                                                                                                                                                                                                     | Yes when the constraint is met.                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Constraint: This parameter is mandatory if there is security policy parameter **policy** or **signature** in the request.                                                                                                                                                                |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | policy                                          | Indicates the security policy in the request. For details about the policy format, see the policy format in :ref:`Authentication of Signature Carried in the Table Uploaded Through a Browser <obs_04_0012>`.                                                                            | Yes when the constraint is met.                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Constraint: This parameter is mandatory if the bucket provides the **AccessKeyId** (or **signature**).                                                                                                                                                                                   |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | signature                                       | Indicates a signature string calculated based on StringToSign.                                                                                                                                                                                                                           | Yes when the constraint is met.                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Constraint: This parameter is mandatory if the bucket provides the **AccessKeyId** (or **policy**).                                                                                                                                                                                      |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | token                                           | Specifies the AK, signature, and security policy of the request initiator. The priority of a token is higher than that of a specified AK, the request signature, and the security policy of the request initiator.                                                                       | No                                                |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Example:                                                                                                                                                                                                                                                                                 |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | In HTML: <input type= "text" name="token" value="ak:signature:policy" />                                                                                                                                                                                                                 |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-acl                                       | When creating an object, you can add this message header to set the permission control policy for the object. The predefined common policies are as follows: **private**, **public-read**, **public-read-write**, **public-read-delivered**, and **public-read-write-delivered**.        | No                                                |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | An example is provided as follows:                                                                                                                                                                                                                                                       |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | In POLICY: {"acl": "public-read" }                                                                                                                                                                                                                                                       |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | In HTML: <input type="text" name="acl" value="public-read" />                                                                                                                                                                                                                            |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-grant-read                                | When creating an object, you can use this header to authorize all users in an account the permission to read objects and obtain object metadata.                                                                                                                                         | No                                                |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | An example is provided as follows:                                                                                                                                                                                                                                                       |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | In POLICY: {'grant-read': 'id=domainId1' },                                                                                                                                                                                                                                              |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | In HTML: <input type="text" name="grant-read" value="id=domainId1" />                                                                                                                                                                                                                    |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-grant-read-acp                            | When creating an object, you can use this header to authorize all users in an account the permission to obtain the object ACL.                                                                                                                                                           | No                                                |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | An example is provided as follows:                                                                                                                                                                                                                                                       |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | In POLICY: {"grant-read-acp": "id=domainId1" },                                                                                                                                                                                                                                          |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | In HTML: <input type="text" name="grant-read-acp" value="id=domainId1" />                                                                                                                                                                                                                |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-grant-write-acp                           | When creating an object, you can use this header to authorize all users in an account the permission to write the object ACL.                                                                                                                                                            | No                                                |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | An example is provided as follows:                                                                                                                                                                                                                                                       |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | In POLICY: {"grant-write-acp": "id=domainId1" },                                                                                                                                                                                                                                         |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | In HTML: <input type="text" name="grant-write-acp" value="id=domainId1" />                                                                                                                                                                                                               |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-grant-full-control                        | When creating an object, you can use this header to authorize all users in an account the permission to read the object, obtain the object metadata, obtain the object ACL, and write the object ACL.                                                                                    | No                                                |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | An example is provided as follows:                                                                                                                                                                                                                                                       |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | In POLICY: {"grant-full-control": "id=domainId1" },                                                                                                                                                                                                                                      |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | In HTML: <input type="text" name="grant-full-control" value="id=domainId1" />                                                                                                                                                                                                            |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-storage-class                             | When creating an object, you can use this header to specify the storage class for the object. If you do not use this header, the object storage class is the default storage class of the bucket.                                                                                        | No                                                |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Storage class value options: **STANDARD** (Standard), **WARM** (Warm), **COLD** (Cold). These values are case sensitive.                                                                                                                                                                 |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | An example is provided as follows:                                                                                                                                                                                                                                                       |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | In POLICY: {"storage-class": "STANDARD" },                                                                                                                                                                                                                                               |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | In HTML: <input type="text" name="x-obs-storage-class" value="STANDARD" />                                                                                                                                                                                                               |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | Cache-Control,                                  | Standard HTTP headers. OBS records those headers. If you download the object or send the HEAD Object request, those parameter values are returned.                                                                                                                                       | No                                                |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   | Content-Type,                                   | Type: string                                                                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   | Content-Disposition,                            | An example is provided as follows:                                                                                                                                                                                                                                                       |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   | Content-Encoding                                | In POLICY: ["starts-with", "$Content-Type", "text/"],                                                                                                                                                                                                                                    |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   | Expires                                         | In HTML: <input type="text" name="content-type" value="text/plain" />                                                                                                                                                                                                                    |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | success_action_redirect                         | Indicates the address (URL) to which a successfully responded request is redirected.                                                                                                                                                                                                     | No                                                |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | -  If the value is valid and the request is successful, OBS returns status code 303. **Location** contains **success_action_redirect** as well as the bucket name, object name, and object ETag.                                                                                         |                                                   |
   |                                                 | -  If this parameter value is invalid, OBS ignores this parameter. In such case, the **Location** header is the object address, and OBS returns the response code based on whether the operation succeeds or fails.                                                                      |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | An example is provided as follows:                                                                                                                                                                                                                                                       |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | In POLICY: {"success_action_redirect": "http://123458.com"},                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | In HTML: <input type="text" name="success_action_redirect" value="http://123458.com" />                                                                                                                                                                                                  |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-meta-\*                                   | Indicates user-defined metadata. When creating an object, you can use this header or a header starting with **x-obs-meta-** to define object metadata in an HTTP request. Custom metadata will be returned in the response header when you retrieve or query the metadata of the object. | No                                                |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | An example is provided as follows:                                                                                                                                                                                                                                                       |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | In POLICY: {" x-obs-meta-test ": " test metadata " },                                                                                                                                                                                                                                    |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | In HTML: <input type="text" name=" x-obs-meta-test " value=" test metadata " />                                                                                                                                                                                                          |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | success_action_status                           | Indicates the status code returned after the request is successfully received. Possible values are **200**, **201**, and **204**.                                                                                                                                                        | No                                                |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | -  If this parameter is set to **200** or **204**, the body in the OBS response message is empty.                                                                                                                                                                                        |                                                   |
   |                                                 | -  If this parameter is set to **201**, the OBS response message contains an XML document that describes the response to the request.                                                                                                                                                    |                                                   |
   |                                                 | -  If the value is not set or if it is set to an invalid value, the OBS returns an empty document with a 204 status code.                                                                                                                                                                |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | An example is provided as follows:                                                                                                                                                                                                                                                       |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | In POLICY: ["starts-with", "$success_action_status", ""],                                                                                                                                                                                                                                |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | In HTML: <input type="text" name="success_action_status" value="200" />                                                                                                                                                                                                                  |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-website-redirect-location                 | If a bucket is configured with the static website hosting function, it will redirect requests for this object to another object in the same bucket or to an external URL. OBS stores the value of this header in the object metadata.                                                    | No                                                |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Default value: none                                                                                                                                                                                                                                                                      |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Constraint: The value must be prefixed by a slash (/), **http://**, or **https://**. The length of the value cannot exceed 2 KB.                                                                                                                                                         |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-server-side-encryption                    | Indicates that SSE-KMS is used.                                                                                                                                                                                                                                                          | No. This header is required when SSE-KMS is used. |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Example: **x-obs-server-side-encryption:kms**                                                                                                                                                                                                                                            |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-server-side-encryption-kms-key-id         | Master key ID. This header is used in SSE-KMS mode. If the customer does not provide the master key ID, the default master key ID will be used.                                                                                                                                          | No                                                |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | The following two formats are supported:                                                                                                                                                                                                                                                 |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | 1. *regionID*\ **:**\ *domainID*\ **:key/**\ *key_id*                                                                                                                                                                                                                                    |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | 2. *key_id*                                                                                                                                                                                                                                                                              |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | *regionID* is the ID of the region to which the key belongs. *domainID* is the account ID of the tenant to which the key belongs. *key_id* is the key ID created in KMS.                                                                                                                 |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Example:                                                                                                                                                                                                                                                                                 |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | 1. x-obs-server-side-encryption-kms-key-id: *region*:domainiddomainiddomainiddoma0001:key/4f1cd4de-ab64-4807-920a-47fc42e7f0d0                                                                                                                                                           |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | 2. x-obs-server-side-encryption-kms-key-id:4f1cd4de-ab64-4807-920a-47fc42e7f0d0                                                                                                                                                                                                          |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-server-side-encryption-customer-algorithm | Encryption algorithm. The header is used in SSE-C mode.                                                                                                                                                                                                                                  | No. This header is required when SSE-C is used.   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Example: **x-obs-server-side-encryption-customer-algorithm:AES256**                                                                                                                                                                                                                      |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Constraint: This header must be used together with **x-obs-server-side-encryption-customer-key** and **x-obs-server-side-encryption-customer-key-MD5**.                                                                                                                                  |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-server-side-encryption-customer-key       | A key used to encrypt objects. The header is used in SSE-C mode. This key is used to encrypt objects.                                                                                                                                                                                    | No. This header is required when SSE-C is used.   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Example: **x-obs-server-side-encryption-customer-key:K7QkYpBkM5+hca27fsNkUnNVaobncnLht/rCB2o/9Cw=**                                                                                                                                                                                      |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Constraint: This header is a Base64-encoded 256-bit key and must be used together with **x-obs-server-side-encryption-customer-algorithm** and **x-obs-server-side-encryption-customer-key-MD5**.                                                                                        |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-server-side-encryption-customer-key-MD5   | Indicates the MD5 value of a key used to encrypt objects. The header is used in SSE-C mode. The MD5 value is used to check whether any error occurs during the transmission of the key.                                                                                                  | No. This header is required when SSE-C is used.   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                                                             |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Example: **x-obs-server-side-encryption-customer-key-MD5:4XvB3tbNTN+tIEVa0/fGaQ==**                                                                                                                                                                                                      |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Constraint: This header is a Base64-encoded 128-bit MD5 value and must be used together with **x-obs-server-side-encryption-customer-algorithm** and **x-obs-server-side-encryption-customer-key**.                                                                                      |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-expires                                   | Indicates the expiration time of an object, in days. An object will be automatically deleted once it expires (calculated from the last modification time of the object).                                                                                                                 | No                                                |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Type: integer                                                                                                                                                                                                                                                                            |                                                   |
   |                                                 |                                                                                                                                                                                                                                                                                          |                                                   |
   |                                                 | Example: **x-obs-expires:3**                                                                                                                                                                                                                                                             |                                                   |
   +-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+

Response Syntax
---------------

::

   HTTP/1.1 status_code
   Content-Type: application/xml
   Location: location
   Date: date
   ETag: etag

Response Headers
----------------

The response to the request uses common headers. For details, see :ref:`Table 1 <obs_04_0013__d0e686>`.

In addition to the common response headers, the following message headers may also be used. For details, see :ref:`Table 3 <obs_04_0081__table35215532173747>`.

.. _obs_04_0081__table35215532173747:

.. table:: **Table 3** Additional response headers

   +-------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Header                                          | Description                                                                                                                                                                                       |
   +=================================================+===================================================================================================================================================================================================+
   | x-obs-version-id                                | Object version ID. If versioning is enabled for the bucket, the object version ID will be returned. A string **null** will be returned if the bucket housing the object has versioning suspended. |
   |                                                 |                                                                                                                                                                                                   |
   |                                                 | Type: string                                                                                                                                                                                      |
   +-------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Access-Control-Allow-Origin                     | Indicates that the origin is included in the response if the origin in the request meets the CORS configuration requirements when CORS is configured for buckets.                                 |
   |                                                 |                                                                                                                                                                                                   |
   |                                                 | Type: string                                                                                                                                                                                      |
   +-------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Access-Control-Allow-Headers                    | Indicates that the headers are included in the response if headers in the request meet the CORS configuration requirements when CORS is configured for buckets.                                   |
   |                                                 |                                                                                                                                                                                                   |
   |                                                 | Type: string                                                                                                                                                                                      |
   +-------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Access-Control-Max-Age                          | Indicates MaxAgeSeconds in the CORS configuration of the server when CORS is configured for buckets.                                                                                              |
   |                                                 |                                                                                                                                                                                                   |
   |                                                 | Type: integer                                                                                                                                                                                     |
   +-------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Access-Control-Allow-Methods                    | Indicates that methods in the rule are included in the response if Access-Control-Request-Method in the request meets the CORS configuration requirements when CORS is configured for buckets.    |
   |                                                 |                                                                                                                                                                                                   |
   |                                                 | Type: string                                                                                                                                                                                      |
   |                                                 |                                                                                                                                                                                                   |
   |                                                 | Possible values are GET, PUT, HEAD, POST, and DELETE.                                                                                                                                             |
   +-------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Access-Control-Expose-Headers                   | Value of **ExposeHeader** in the CORS configuration of a server when CORS is configured for buckets.                                                                                              |
   |                                                 |                                                                                                                                                                                                   |
   |                                                 | Type: string                                                                                                                                                                                      |
   +-------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption                    | This header is included in a response if SSE-KMS is used.                                                                                                                                         |
   |                                                 |                                                                                                                                                                                                   |
   |                                                 | Type: string                                                                                                                                                                                      |
   |                                                 |                                                                                                                                                                                                   |
   |                                                 | Example: **x-obs-server-side-encryption:kms**                                                                                                                                                     |
   +-------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption-kms-key-id         | Indicates the master key ID. This header is included in a response if SSE-KMS is used.                                                                                                            |
   |                                                 |                                                                                                                                                                                                   |
   |                                                 | Type: string                                                                                                                                                                                      |
   |                                                 |                                                                                                                                                                                                   |
   |                                                 | Format: *regionID*\ **:**\ *domainID*\ **:key/**\ *key_id*                                                                                                                                        |
   |                                                 |                                                                                                                                                                                                   |
   |                                                 | *regionID* is the ID of the region to which the key belongs. *domainID* is the account ID of the tenant to which the key belongs. *key_id* is the key ID used in this encryption.                 |
   |                                                 |                                                                                                                                                                                                   |
   |                                                 | Example: **x-obs-server-side-encryption-kms-key-id:**\ *region*\ **:domainiddomainiddomainiddoma0001:key/4f1cd4de-ab64-4807-920a-47fc42e7f0d0**                                                   |
   +-------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption-customer-algorithm | Indicates an encryption algorithm. This header is included in a response if SSE-C is used.                                                                                                        |
   |                                                 |                                                                                                                                                                                                   |
   |                                                 | Type: string                                                                                                                                                                                      |
   |                                                 |                                                                                                                                                                                                   |
   |                                                 | Example: **x-obs-server-side-encryption-customer-algorithm:AES256**                                                                                                                               |
   +-------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption-customer-key-MD5   | Indicates the MD5 value of a key used to encrypt objects. This header is included in a response if SSE-C is used.                                                                                 |
   |                                                 |                                                                                                                                                                                                   |
   |                                                 | Type: string                                                                                                                                                                                      |
   |                                                 |                                                                                                                                                                                                   |
   |                                                 | Example: **x-obs-server-side-encryption-customer-key-MD5:4XvB3tbNTN+tIEVa0/fGaQ==**                                                                                                               |
   +-------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Elements
-----------------

This response involves no elements.

Error Responses
---------------

No special error responses are returned. For details about error responses, see :ref:`Table 2 <obs_04_0115__d0e843>`.

Sample Request 1
----------------

**Common POST upload**

.. code-block:: text

   POST / HTTP/1.1
   Date: WED, 01 Jul 2015 04:15:23 GMT
   Host: examplebucket.obs.region.example.com
   Content-Type: multipart/form-data; boundary=7db143f50da2
   Content-Length: 2424
   Origin: www.example.com
   Access-Control-Request-Headers:acc_header_1

   --7db143f50da2
   Content-Disposition: form-data; name="key"

   object01
   --7db143f50da2
   Content-Disposition: form-data; name="acl"

   public-read
   --7db143f50da2
   Content-Disposition: form-data; name="content-type"

   text/plain
   --7db143f50da2
   Content-Disposition: form-data; name="expires"

   WED, 01 Jul 2015 04:16:15 GMT
   --7db143f50da2
   Content-Disposition: form-data; name="AccessKeyId"

   14RZT432N80TGDF2Y2G2
   --7db143f50da2
   Content-Disposition: form-data; name="policy"

   ew0KICAiZXhaaXJhdGlvbiI6ICIyMDE1LTA3LTAxVDEyOjAwOjAwLjAwMFoiLA0KICAiY29uZGl0aW9ucyI6IFsNCiAgICB7ImJ1Y2tldCI6ICJleG1hcGxlYnVja2V0IiB9LA0KICAgIHsiYWNsIjogInB1YmxpYy1yZWFkIiB9LA0KICAgIHsiRXhaaXJlcyI6ICIxMDAwIiB9LA0KICAgIFsiZXEiLCAiJGtleSIsICJvYmplY3QwMSJdLA0KICAgIFsic3RhcnRzLXdpdGgiLCAiJENvbnRlbnQtVHlwZSIsICJ0ZXh0LyJdLA0KICBdDQp9DQo=
   --7db143f50da2
   Content-Disposition: form-data; name="signature"

   Vk6rwO0Nq09BLhvNSIYwSJTRQ+k=
   --7db143f50da2
   Content-Disposition: form-data; name="file"; filename="C:\Testtools\UpLoadFiles\object\1024Bytes.txt"
   Content-Type: text/plain

   01234567890
   --7db143f50da2
   Content-Disposition: form-data; name="submit"

   Upload
   --7db143f50da2--

Sample Response 1
-----------------

After CORS is configured for a bucket, the response contains the **Access-Control-\*** information.

::

   HTTP/1.1 204 No Content
   x-obs-request-id: 90E2BA00C26C00000133B442A90063FD
   x-obs-id-2: OTBFMkJBMDBDMjZDMDAwMDAxMzNCNDQyQTkwMDYzRkRBQUFBQUFBQWJiYmJiYmJi
   Access-Control-Allow-Origin: www.example.com
   Access-Control-Allow-Methods: POST,GET,HEAD,PUT
   Access-Control-Allow-Headers: acc_header_01
   Access-Control-Max-Age: 100
   Access-Control-Expose-Headers: exp_header_01
   Content-Type: text/xml
   Location: http://examplebucket.obs.region.example.com/object01
   Date: WED, 01 Jul 2015 04:15:23 GMT
   ETag: "ab7abb0da4bca5323ab6119bb5dcd296"

Sample Request 2
----------------

**Upload an object with the** **x-obs-acl, storage class, and redirection header fields carried in the request message.**

Before encoding, the policy content is as follows:

::

   {
       "expiration":"2018-07-17T04:54:35Z",
       "conditions":[
           {
               "content-type":"text/plain"
           },
           {
               "x-obs-storage-class":"WARM"
           },
           {
               "success_action_redirect":"http://www.example.com"
           },
           {
               "x-obs-acl":"public-read"
           },
           [
               "starts-with",
               "$bucket",
               ""
           ],
           [
               "starts-with",
               "$key",
               ""
           ]
       ]
   }

Sample request:

.. code-block:: text

   POST / HTTP/1.1
   Host: examplebucket.obs.region.example.com
   Accept-Encoding: identity
   Content-Length: 947
   Content-Type: multipart/form-data; boundary=9431149156168
   User-Agent: OBS/Test

   --9431149156168
   Content-Disposition: form-data; name="x-obs-acl"

   public-read
   --9431149156168
   Content-Disposition: form-data; name="AccessKeyId"

   H4IPJX0TQTHTHEBQQCEC
   --9431149156168
   Content-Disposition: form-data; name="key"

   my-obs-object-key-demo
   --9431149156168
   Content-Disposition: form-data; name="signature"

   WNwv8P1ZiWdqPQqjXeLmAfzPDAI=
   --9431149156168
   Content-Disposition: form-data; name="policy"

   eyJleHBpcmF0aW9uIjoiMjAxOC0wNy0xN1QwODozNDoyM1oiLCAiY29uZGl0aW9ucyI6W3siY29udGVudC10eXBlIjoidGV4dC9wbGFpbiJ9LHsieC1vYnMtYWNsIjoicHVibGljLXJlYWQifSxbInN0YXJ0cy13aXRoIiwgIiRidWNrZXQiLCAiIl0sWyJzdGFydHMtd2l0aCIsICIka2V5IiwgIiJdXX0=
   --9431149156168
   Content-Disposition: form-data; name="content-type"

   text/plain
   --9431149156168
   Content-Disposition: form-data; name="file"; filename="myfile"
   Content-Type: text/plain

   c2c6cd0f-898e-11e8-aab6-e567c91fb541
   52b8e8a0-8481-4696-96f3-910635215a78

   --9431149156168--

Sample Response 2
-----------------

::

   HTTP/1.1 204 No Content
   Server: OBS
   Location: http://examplebucket.obs.region.example.com/my-obs-object-key-demo
   ETag: "17a83fc8d431273405bd266114b7e034"
   x-obs-request-id: 5DEB00000164A728A7C7F4E032214CFA
   x-obs-id-2: 32AAAUJAIAABAAAQAAEAABAAAQAAEAABCSwj2PcBE0YcoLHUDO7GSj+rVByzjflA
   Date: Tue, 17 Jul 2018 07:33:36 GMT

Sample Request 3
----------------

**Use a token for authentication.**

.. code-block:: text

   POST / HTTP/1.1
   Content-Type:multipart/form-data; boundary=9431149156168
   Content-Length: 634
   Host: examplebucket.obs.region.example.com

   --9431149156168
   Content-Disposition: form-data; name="key"
   obj01

   --9431149156168
   Content-Disposition: form-data; name="token"
   UDSIAMSTUBTEST002538:XsVcTzR2/A284oE4VH9qPndGcuE=:eyJjb25kaXRpb25zIjogW3siYnVja2V0IjogInRlc3QzMDAzMDU4NzE2NjI2ODkzNjcuMTIifSwgeyJDb250ZW50LVR5cGUiOiAiYXBwbGljYXRpb24veG1sIn0sIFsiZXEiLCAiJGtleSIsICJvYmoudHh0Il1dLCAiZXhwaXJhdGlvbiI6ICIyMDIyLTA5LTA5VDEyOjA5OjI3WiJ9

   --9431149156168
   Content-Disposition: form-data; name="file"; filename="myfile"
   Content-Type: text/plain
   01234567890

   --9431149156168--
   Content-Disposition: form-data; name="submit"
   Upload to OBS

Sample Response 3
-----------------

**The response to the authentication using a token**

::

   HTTP/1.1 204 No Content
   Server: OBS
   Location: http://examplebucket.obs.region.example.com/my-obs-object-key-demo
   ETag: "7eda50a430fed940023acb9c4c6a2fff"
   x-obs-request-id: 000001832010443D80F30B649B969C47
   x-obs-id-2: 32AAAUgAIAABAAAQAAEAABAAAQAAEAABCTj0yO9KJd5In+i9pzTgCDVG9vMnk7O/
   Date: Fri,09Sep 2022 02: 24:40 GMT
