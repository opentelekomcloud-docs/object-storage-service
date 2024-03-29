:original_name: obs_03_0043.html

.. _obs_03_0043:

Response
========

Response Headers
----------------

+-----------------------+-----------------------+------------------------------------------------------------------------------------------+
| Header                | Type                  | Description                                                                              |
+=======================+=======================+==========================================================================================+
| Content-Length        | String                | If the operation succeeds, this value is 0.                                              |
|                       |                       |                                                                                          |
|                       | (Required)            | If the operation fails, this value is the length of the error text in the response body. |
+-----------------------+-----------------------+------------------------------------------------------------------------------------------+
| Content-Type          | String                | MIME type of the object.                                                                 |
|                       |                       |                                                                                          |
|                       | (Required)            |                                                                                          |
+-----------------------+-----------------------+------------------------------------------------------------------------------------------+
| Date                  | Datetime              | Transaction date and time.                                                               |
|                       |                       |                                                                                          |
|                       | (Required)            |                                                                                          |
+-----------------------+-----------------------+------------------------------------------------------------------------------------------+
| X-Trans-Id            | Uuid                  | A unique transaction identifier.                                                         |
|                       |                       |                                                                                          |
|                       | (Required)            |                                                                                          |
+-----------------------+-----------------------+------------------------------------------------------------------------------------------+
| X-Timestamp           | Datetime              | Object creation time and date, in UNIX Epoch timestamp format.                           |
|                       |                       |                                                                                          |
|                       | (Required)            |                                                                                          |
+-----------------------+-----------------------+------------------------------------------------------------------------------------------+
