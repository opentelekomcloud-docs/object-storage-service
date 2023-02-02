:original_name: obs_03_0018.html

.. _obs_03_0018:

Response
========

Response Headers
----------------

.. table:: **Table 1** Response header parameters

   +-------------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | Header                        | Type                  | Description                                                                              |
   +===============================+=======================+==========================================================================================+
   | Accept-Ranges                 | String                | Type of ranges that the object accepts.                                                  |
   |                               |                       |                                                                                          |
   |                               | (Required)            |                                                                                          |
   +-------------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | X-Account-Bytes-Used          | Int                   | Total number of bytes that are stored in OBS for the account.                            |
   |                               |                       |                                                                                          |
   |                               | (Required)            |                                                                                          |
   +-------------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | X-Account-Container-Count     | Int                   | Number of containers in the account.                                                     |
   |                               |                       |                                                                                          |
   |                               | (Required)            |                                                                                          |
   +-------------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | X-Account-Object-Count        | Int                   | Number of objects in the account.                                                        |
   |                               |                       |                                                                                          |
   |                               | (Required)            |                                                                                          |
   +-------------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | X-Account-Meta-name           | String                | Custom account metadata item, where **{name}** is the name of the metadata item.         |
   |                               |                       |                                                                                          |
   |                               | (Optional)            |                                                                                          |
   +-------------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | X-Account-Meta-Quota-Bytes    | Int                   | Quota of the account.                                                                    |
   |                               |                       |                                                                                          |
   |                               | (Optional)            |                                                                                          |
   +-------------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | X-Account-Meta-Temp-URL-Key   | String                | Secret key value for TempURL.                                                            |
   |                               |                       |                                                                                          |
   |                               | (Optional)            |                                                                                          |
   +-------------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | X-Account-Meta-Temp-URL-Key-2 | String                | A second secret key value for TempURL.                                                   |
   |                               |                       |                                                                                          |
   |                               | (Optional)            |                                                                                          |
   +-------------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | X-Account-Project-Domain-Id   | String                | ID of the domain to which the account belongs.                                           |
   |                               |                       |                                                                                          |
   |                               | (Required)            |                                                                                          |
   +-------------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | Content-Length                | String                | If the operation succeeds, the value is the length of the container list information.    |
   |                               |                       |                                                                                          |
   |                               | (Required)            | If the operation fails, this value is the length of the error text in the response body. |
   +-------------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | Content-Type                  | String                | Type of the text in the response body.                                                   |
   |                               |                       |                                                                                          |
   |                               | (Required)            |                                                                                          |
   +-------------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | Date                          | Datetime              | Transaction date and time.                                                               |
   |                               |                       |                                                                                          |
   |                               | (Required)            |                                                                                          |
   +-------------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | X-Trans-Id                    | Uuid                  | A unique transaction identifier.                                                         |
   |                               |                       |                                                                                          |
   |                               | (Required)            |                                                                                          |
   +-------------------------------+-----------------------+------------------------------------------------------------------------------------------+
   | X-Timestamp                   | Datetime              | Object creation time and date, in UNIX Epoch timestamp format.                           |
   |                               |                       |                                                                                          |
   |                               | (Required)            |                                                                                          |
   +-------------------------------+-----------------------+------------------------------------------------------------------------------------------+

Response Body Parameters
------------------------

If the response format is json or xml, container details are shown. The following table describes the response body parameters:

.. table:: **Table 2** Response body parameters

   +-----------+--------+-----------------------------------------------------------+
   | Parameter | Type   | Description                                               |
   +===========+========+===========================================================+
   | name      | String | Name of the container.                                    |
   +-----------+--------+-----------------------------------------------------------+
   | count     | Int    | Number of objects in the container.                       |
   +-----------+--------+-----------------------------------------------------------+
   | bytes     | Int    | Total number of bytes that are stored in OBS for objects. |
   +-----------+--------+-----------------------------------------------------------+

.. note::

   For performance purposes, of the response headers, OBS (compatible with OpenStack Swift) does not update **X-Account-Bytes-Used**, **X-Account-Container-Count**, and **X-Account-Object-Count** in real time.
