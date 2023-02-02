:original_name: obs_03_0055.html

.. _obs_03_0055:

Request
=======

Method
------

.. table:: **Table 1** Method description

   +--------+---------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Method | URI                                                                                   | Description                                                |
   +========+=======================================================================================+============================================================+
   | GET    | /v1/{account}/{container}/{object}{?temp_url_sig,temp_url_expires,multipart-manifest} | Downloads the object content and gets the object metadata. |
   +--------+---------------------------------------------------------------------------------------+------------------------------------------------------------+

**{account}** indicates the name of an account. **{container}** indicates the name of a container. **{object}** indicates the name of an object.

This operation does not involve a request body.

Example Request
---------------

Show the content and metadata of the **goodbye** object in the **marktwain** container:

.. code-block::

   curl -i $publicURL/marktwain/goodbye -X GET -H "X-Auth-Token:$token"

Request Query Parameters
------------------------

:ref:`Table 2 <obs_03_0055__table2272850011511>` describes the query parameters for getting the object content.

.. _obs_03_0055__table2272850011511:

.. table:: **Table 2** Request query parameters

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                     |
   +=======================+=======================+=================================================================================================================================================================================================+
   | temp_url_sig          | String                | Used with TempURL to sign the request.                                                                                                                                                          |
   |                       |                       |                                                                                                                                                                                                 |
   |                       | (Optional)            |                                                                                                                                                                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | temp_url_expires      | String                | Used with TempURL to specify the expiry time of the signature.                                                                                                                                  |
   |                       |                       |                                                                                                                                                                                                 |
   |                       | (Optional)            |                                                                                                                                                                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | multipart-manifest    | String                | If the value is **get** and the object is a large object, the content of the **manifest** file for the static or dynamic large object, instead of the content of the large object, is returned. |
   |                       |                       |                                                                                                                                                                                                 |
   |                       | (Optional)            |                                                                                                                                                                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | filename              | String                | If objects are accessed based on TempURL, use the value of **filename** to replace that of **filename** in the **Content-Disposition** header.                                                  |
   |                       |                       |                                                                                                                                                                                                 |
   |                       | (Optional)            |                                                                                                                                                                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | inline                | NA                    | If objects are accessed based on TempURL, replace the content of the **Content-Disposition** response header with **inline**.                                                                   |
   |                       |                       |                                                                                                                                                                                                 |
   |                       | (Optional)            |                                                                                                                                                                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
   | Header                | Type                  | Description                                                                                                      |
   +=======================+=======================+==================================================================================================================+
   | X-Auth-Token          | String                | Authentication token.                                                                                            |
   |                       |                       |                                                                                                                  |
   |                       | (Required)            |                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
   | Range                 | String                | Range of the content to get.                                                                                     |
   |                       |                       |                                                                                                                  |
   |                       | (Optional)            | For example:                                                                                                     |
   |                       |                       |                                                                                                                  |
   |                       |                       | -  Range: bytes=-5. The last five bytes.                                                                         |
   |                       |                       | -  Range: bytes=10-15. The five bytes of data after a 10-byte offset.                                            |
   |                       |                       | -  Range: bytes=6-. Byte 6 and after.                                                                            |
   |                       |                       | -  Range: bytes=1-3,2-5. A multi-part response that contains bytes 1 to 3 inclusive, and bytes 2 to 5 inclusive. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
   | If-Match              | String                | If the MD5 value of the queried object is equal to the specified value, the object is returned.                  |
   |                       |                       |                                                                                                                  |
   |                       | (Optional)            |                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
   | If-None-Match         | String                | If the MD5 value of the queried object is not equal to the specified value, the object is returned.              |
   |                       |                       |                                                                                                                  |
   |                       | (Optional)            |                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
   | If-Modified-Since     | String                | If the queried object was modified before the specified time, the object is returned.                            |
   |                       |                       |                                                                                                                  |
   |                       | (Optional)            |                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
   | If-Unmodified-Since   | String                | If the queried object was not modified before the specified time, the object is returned.                        |
   |                       |                       |                                                                                                                  |
   |                       | (Optional)            |                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
