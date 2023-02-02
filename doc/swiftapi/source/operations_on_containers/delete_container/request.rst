:original_name: obs_03_0038.html

.. _obs_03_0038:

Request
=======

Method
------

.. table:: **Table 1** Method description

   +--------+---------------------------+-----------------------------------------------------------------------------------+
   | Method | URI                       | Description                                                                       |
   +========+===========================+===================================================================================+
   | DELETE | /v1/{account}/{container} | Deletes a container in a specified account. Only empty containers can be deleted. |
   +--------+---------------------------+-----------------------------------------------------------------------------------+

**{account}** indicates the name of an account. **{container}** indicates the name of a container.

This operation does not involve a request body.

Example Request
---------------

Delete the empty containers from the specified account:

.. code-block::

   curl -i $publicURL/steven -X DELETE -H "X-Auth-Token:$token"

Request Query Parameters
------------------------

+-----------------------+-----------------------+---------------------------------------------------------------------------+
| Parameter             | Type                  | Description                                                               |
+=======================+=======================+===========================================================================+
| bulk-delete           | String                | Bulk-deletes objects. This parameter is used with the deletion list file. |
|                       |                       |                                                                           |
|                       | (Optional)            | A maximum of 10,000 objects can be deleted at once.                       |
+-----------------------+-----------------------+---------------------------------------------------------------------------+

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
| {container}           | String                | A unique container name.                                                                 |
|                       |                       |                                                                                          |
|                       | (Required)            | For details about container naming rules, see :ref:`Naming Rules <obs_03_0009>`.         |
+-----------------------+-----------------------+------------------------------------------------------------------------------------------+

Request header parameters

+-----------------------+-----------------------+-----------------------+
| Parameter             | Type                  | Description           |
+=======================+=======================+=======================+
| X-Auth-Token          | String                | Authentication token. |
|                       |                       |                       |
|                       | (Required)            |                       |
+-----------------------+-----------------------+-----------------------+
