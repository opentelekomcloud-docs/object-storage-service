:original_name: obs_03_0031.html

.. _obs_03_0031:

Response
========

Response Headers
----------------

+--------------------------+-----------------------+------------------------------------------------------------------------------------------+
| Header                   | Type                  | Description                                                                              |
+==========================+=======================+==========================================================================================+
| Accept-Ranges            | String                | Type of ranges that the object accepts.                                                  |
|                          |                       |                                                                                          |
|                          | (Required)            |                                                                                          |
+--------------------------+-----------------------+------------------------------------------------------------------------------------------+
| X-Container-Bytes-Used   | Int                   | Total number of bytes that are stored in OBS for the container.                          |
|                          |                       |                                                                                          |
|                          | (Required)            |                                                                                          |
+--------------------------+-----------------------+------------------------------------------------------------------------------------------+
| X-Container-Object-Count | Int                   | Number of objects in the container.                                                      |
|                          |                       |                                                                                          |
|                          | (Required)            |                                                                                          |
+--------------------------+-----------------------+------------------------------------------------------------------------------------------+
| X-Container-Meta-name    | String                | Custom container metadata item, where **{name}** is the name of the metadata item.       |
|                          |                       |                                                                                          |
|                          | (Optional)            |                                                                                          |
+--------------------------+-----------------------+------------------------------------------------------------------------------------------+
| Content-Length           | String                | If the operation succeeds, the value is the length of the object list information.       |
|                          |                       |                                                                                          |
|                          | (Required)            | If the operation fails, this value is the length of the error text in the response body. |
+--------------------------+-----------------------+------------------------------------------------------------------------------------------+
| Content-Type             | String                | MIME type of the text in the response body.                                              |
|                          |                       |                                                                                          |
|                          | (Required)            |                                                                                          |
+--------------------------+-----------------------+------------------------------------------------------------------------------------------+
| Date                     | Datetime              | Transaction date and time.                                                               |
|                          |                       |                                                                                          |
|                          | (Required)            |                                                                                          |
+--------------------------+-----------------------+------------------------------------------------------------------------------------------+
| X-Trans-Id               | Uuid                  | A unique transaction identifier.                                                         |
|                          |                       |                                                                                          |
|                          | (Required)            |                                                                                          |
+--------------------------+-----------------------+------------------------------------------------------------------------------------------+
| X-Timestamp              | Datetime              | The time when the container was created.                                                 |
|                          |                       |                                                                                          |
|                          | (Required)            | The format is a UNIX Epoch timestamp.                                                    |
+--------------------------+-----------------------+------------------------------------------------------------------------------------------+

Response Body Parameters
------------------------

If the response format is json or xml, object details are shown. :ref:`Table 1 <obs_03_0031__table64595445162712>` describes the response body parameters:

.. _obs_03_0031__table64595445162712:

.. table:: **Table 1** Response body parameters

   +---------------+----------+--------------------------------------------------------------+
   | Parameter     | Type     | Description                                                  |
   +===============+==========+==============================================================+
   | name          | String   | An object name.                                              |
   +---------------+----------+--------------------------------------------------------------+
   | hash          | String   | MD5 checksum value of the object content.                    |
   +---------------+----------+--------------------------------------------------------------+
   | bytes         | Int      | Total number of bytes that are stored in OBS for the object. |
   +---------------+----------+--------------------------------------------------------------+
   | content_type  | String   | Content type of the object.                                  |
   +---------------+----------+--------------------------------------------------------------+
   | last_modified | Datetime | Date and time when the object was last modified.             |
   +---------------+----------+--------------------------------------------------------------+
