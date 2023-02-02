:original_name: obs_03_0025.html

.. _obs_03_0025:

Request
=======

Method
------

.. table:: **Table 1** Method description

   ====== ============= ======================================
   Method URI           Description
   ====== ============= ======================================
   HEAD   /v1/{account} Shows metadata of a specified account.
   ====== ============= ======================================

**{account}** indicates the name of an account. Metadata of an account includes the number of containers, number of objects, and total number of bytes that are stored in OBS for the account.

This operation does not involve a request body.

Example Request
---------------

.. code-block::

   curl -i $publicURL -X HEAD -H "X-Auth-Token:$token"

Request Query Parameters
------------------------

This operation does not include request query parameters.

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
