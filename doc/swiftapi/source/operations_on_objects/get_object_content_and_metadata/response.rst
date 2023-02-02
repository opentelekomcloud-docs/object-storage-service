:original_name: obs_03_0056.html

.. _obs_03_0056:

Response
========

Response Headers
----------------

The following table describes the response headers:

.. table:: **Table 1** Response header parameters

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Header                | Type                  | Description                                                                                                                                                   |
   +=======================+=======================+===============================================================================================================================================================+
   | Accept-Ranges         | String                | Type of ranges that the object accepts.                                                                                                                       |
   |                       |                       |                                                                                                                                                               |
   |                       | (Required)            |                                                                                                                                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Object-Meta-name    | String                | Custom object metadata item, where **{name}** is the name of the metadata item.                                                                               |
   |                       |                       |                                                                                                                                                               |
   |                       | (Required)            |                                                                                                                                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Timestamp           | Datetime              | Object creation time and date, in UNIX Epoch timestamp format.                                                                                                |
   |                       |                       |                                                                                                                                                               |
   |                       | (Required)            |                                                                                                                                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ETag                  | String                | For ordinary objects, this value is the MD5 checksum of the object content.                                                                                   |
   |                       |                       |                                                                                                                                                               |
   |                       | (Required)            | For manifest objects, this value is the MD5 checksum of the concatenated string of MD5 checksums for each of the segments in the manifest.                    |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Encoding      | String                | Code used when an object is downloaded through a browser.                                                                                                     |
   |                       |                       |                                                                                                                                                               |
   |                       | (Optional)            |                                                                                                                                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Disposition   | String                | When an object is downloaded through a browser, the default object name is **newname**.                                                                       |
   |                       |                       |                                                                                                                                                               |
   |                       | (Optional)            |                                                                                                                                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Object-Manifest     | String                | This is the identifier of a dynamic large object. The value is the container and object name prefix of the segment objects in the form of *container/prefix*. |
   |                       |                       |                                                                                                                                                               |
   |                       | (Optional)            |                                                                                                                                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Static-Large-Object | String                | Identifier of a large static object.                                                                                                                          |
   |                       |                       |                                                                                                                                                               |
   |                       | (Optional)            |                                                                                                                                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Length        | String                | If the operation succeeds, the value is the content length of the obtained object.                                                                            |
   |                       |                       |                                                                                                                                                               |
   |                       | (Required)            | If the operation fails, this value is the length of the error text in the response body.                                                                      |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type          | String                | MIME type of the object.                                                                                                                                      |
   |                       |                       |                                                                                                                                                               |
   |                       | (Required)            |                                                                                                                                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Date                  | Datetime              | Transaction date and time.                                                                                                                                    |
   |                       |                       |                                                                                                                                                               |
   |                       | (Required)            |                                                                                                                                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Trans-Id            | Uuid                  | A unique transaction identifier.                                                                                                                              |
   |                       |                       |                                                                                                                                                               |
   |                       | (Required)            |                                                                                                                                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. note::

   If the MIME type of the object in the object upload is not in *XXX/XXX* format, OBS (compatible with OpenStack Swift) uses the default type **application/octet-stream**. OpenStack Swift is able to return **Content-Type** in non-*XXX/XXX* format.
