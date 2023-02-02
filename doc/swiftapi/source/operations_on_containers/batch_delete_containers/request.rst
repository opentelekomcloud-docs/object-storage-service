:original_name: obs_03_0050.html

.. _obs_03_0050:

Request
=======

Method
------

+--------+---------------------------+--------------------------------------------------------------------------------+
| Method | URI                       | Description                                                                    |
+========+===========================+================================================================================+
| POST   | /v1/{account}?bulk-delete | Batch deletes containers. A maximum of 10,000 empty containers can be deleted. |
+--------+---------------------------+--------------------------------------------------------------------------------+

**{account}** indicates the name of an account.

The request body is a text file that includes the containers to be deleted. Each line in the text file represents a container to be deleted.

Example Request
---------------

Batch delete containers:

.. code-block::

   curl -i $publicURL?bulk-delete -XPOST -H "X-Auth-Token:$token" -T ./deletesample

Request Query Parameters
------------------------

+-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------+
| Parameter             | Type                  | Description                                                                                                 |
+=======================+=======================+=============================================================================================================+
| bulk-delete           | String                | Bulk-deletes containers. It is used together with the text file that includes the containers to be deleted. |
|                       |                       |                                                                                                             |
|                       | (Required)            | A maximum of 10,000 empty containers can be deleted at once.                                                |
+-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------+

Request Headers
---------------

Request URI parameters

+-----------------------+-----------------------+------------------------------------------------------------------------------------------+
| Parameter             | Type                  | Description                                                                              |
+=======================+=======================+==========================================================================================+
| {account}             | String                | A unique account name. In the current version, it indicates a unique ID for the account. |
|                       |                       |                                                                                          |
|                       | (Required)            |                                                                                          |
+-----------------------+-----------------------+------------------------------------------------------------------------------------------+

Request header parameters

+-----------------------+-----------------------+-----------------------+
| Parameter             | Type                  | Description           |
+=======================+=======================+=======================+
| X-Auth-Token          | String                | Authentication token. |
|                       |                       |                       |
|                       | (Required)            |                       |
+-----------------------+-----------------------+-----------------------+
