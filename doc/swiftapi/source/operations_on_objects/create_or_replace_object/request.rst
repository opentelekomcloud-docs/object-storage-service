:original_name: obs_03_0059.html

.. _obs_03_0059:

Request
=======

Method
------

.. table:: **Table 1** Method description

   +--------+---------------------------------------------------------------------------------------+-----------------------------------------------+
   | Method | URI                                                                                   | Description                                   |
   +========+=======================================================================================+===============================================+
   | PUT    | /v1/{account}/{container}/{object}{?temp_url_sig,temp_url_expires,multipart-manifest} | Creates an object in the specified container. |
   +--------+---------------------------------------------------------------------------------------+-----------------------------------------------+

**{account}** indicates the name of an account. **{container}** indicates the name of a container. **{object}** indicates the name of an object.

The request body of this operation is the object content.

Example Request
---------------

Create an object:

.. code-block:: text

   curl -i $publicURL/marktwain/helloworld.txt -X PUT
    -H "X-Auth-Token: $token"

Request Query Parameters
------------------------

:ref:`Table 2 <obs_03_0059__table21447202143412>` describes the query parameters for getting the object content.

.. _obs_03_0059__table21447202143412:

.. table:: **Table 2** Request query parameters

   +--------------------+--------+------------------------------------------------------------------------------------------------------------------------+-----------------+
   | Parameter          | Type   | Description                                                                                                            | Required or Not |
   +====================+========+========================================================================================================================+=================+
   | temp_url_sig       | String | Used with TempURL to sign the request.                                                                                 | No              |
   +--------------------+--------+------------------------------------------------------------------------------------------------------------------------+-----------------+
   | temp_url_expires   | String | Used with TempURL to specify the expiry time of the signature.                                                         | No              |
   +--------------------+--------+------------------------------------------------------------------------------------------------------------------------+-----------------+
   | multipart-manifest | String | If **multipart-manifest=put** is set, the object is a static large object manifest and the body contains the manifest. | No              |
   +--------------------+--------+------------------------------------------------------------------------------------------------------------------------+-----------------+

Request Headers
---------------

Request URI parameters

+-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
| Parameter             | Type                  | Description                                                                                           |
+=======================+=======================+=======================================================================================================+
| {account}             | String                | A unique account name. In the current version, it indicates a unique ID for the account.              |
|                       |                       |                                                                                                       |
|                       | (Required)            |                                                                                                       |
+-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
| {container}           | String                | A unique container name.                                                                              |
|                       |                       |                                                                                                       |
|                       | (Required)            | For details about container naming rules, see :ref:`Naming Rules <obs_03_0009>`.                      |
+-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
| {object}              | String                | An object name.                                                                                       |
|                       |                       |                                                                                                       |
|                       | (Required)            | For details about object naming rules, see :ref:`Object Naming Rules <obs_03_0009__section23579102>`. |
+-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request header parameters

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Header                | Type                  | Description                                                                                                                                                                                                                                                      |
   +=======================+=======================+==================================================================================================================================================================================================================================================================+
   | X-Auth-Token          | String                | Authentication token.                                                                                                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                                                                                  |
   |                       | (Required)            |                                                                                                                                                                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Object-Meta-name    | String                | Object metadata, where **{name}** is the name of the metadata item. To delete this item, leave **{name}** empty in this header. You must specify an **X-Object-Meta-{name}** header for each metadata item (for each **{name}**) that you want to add or update. |
   |                       |                       |                                                                                                                                                                                                                                                                  |
   |                       | (Optional)            |                                                                                                                                                                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type          | String                | Sets the MIME type of the object.                                                                                                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                                                                                                  |
   |                       | (Optional)            |                                                                                                                                                                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Detect-Content-Type | Boolean               | If it is set to **true**, OBS guesses the content type based on the file name extension and ignores the value sent in the **Content-Type** header, if present.                                                                                                   |
   |                       |                       |                                                                                                                                                                                                                                                                  |
   |                       | (Optional)            |                                                                                                                                                                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | If-None-Match         | String                | Only an **If-None-Match: \*** header can be specified. If an object already exists, the object fails to be created and a 412 status code is returned.                                                                                                            |
   |                       |                       |                                                                                                                                                                                                                                                                  |
   |                       | (Optional)            |                                                                                                                                                                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Object-Manifest     | String                | Set to specify that this is a dynamic large object manifest object. The value is the container and object name prefix of the segment objects in the *container/prefix* format. UTF-8 encoding must be used.                                                      |
   |                       |                       |                                                                                                                                                                                                                                                                  |
   |                       | (Optional)            |                                                                                                                                                                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Length        | String                | Set to the length of the object content. Do not set if chunked transfer encoding is being used.                                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                                                                                                                  |
   |                       | (Optional)            |                                                                                                                                                                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Transfer-Encoding     | String                | Set to **chunked** to enable chunked transfer encoding. If used, the **Content-Length** header is ignored.                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                                                                                                  |
   |                       | (Optional)            |                                                                                                                                                                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Copy-From           | String                | The format is {container}/{object}. When this header is set, {container}/{object} is copied to create an object. UTF-8 encoding must be used.                                                                                                                    |
   |                       |                       |                                                                                                                                                                                                                                                                  |
   |                       | (Optional)            | Using **PUT** with **X-Copy-From** has the same effect as using the **COPY** operation to copy an object.                                                                                                                                                        |
   |                       |                       |                                                                                                                                                                                                                                                                  |
   |                       |                       | Using **PUT** with **X-Copy-From** has the same effect as **COPY** to create an object.                                                                                                                                                                          |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ETag                  | String                | MD5 checksum value of the request body. If the MD5 checksum value of the request body is equal to the value of **ETag**, the upload was successful. If not equal, a 422 status code is returned.                                                                 |
   |                       |                       |                                                                                                                                                                                                                                                                  |
   |                       | (Optional)            | Checking the MD5 checksum value for an upload is recommended.                                                                                                                                                                                                    |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Disposition   | String                | When the header is set to **{newname}** and an object is downloaded through a browser, the default object name **{newname}** is returned.                                                                                                                        |
   |                       |                       |                                                                                                                                                                                                                                                                  |
   |                       | (Optional)            |                                                                                                                                                                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Encoding      | String                | If this header is set, the value is the encoding format used when an object is downloaded through a browser.                                                                                                                                                     |
   |                       |                       |                                                                                                                                                                                                                                                                  |
   |                       | (Optional)            |                                                                                                                                                                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. note::

   If chunked transfer encoding is used and the value of **Content-Length** in a request is greater than the actual length of an object to be uploaded, OBS (compatible with OpenStack Swift) returns a 201 status code to indicate that the object was created successfully. In the same scenario, OpenStack Swift, in contrast, returns a 408 (Request Timeout) status code, even if but the object was created successfully.
