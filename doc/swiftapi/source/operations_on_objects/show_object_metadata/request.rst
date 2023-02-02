:original_name: obs_03_0071.html

.. _obs_03_0071:

Request
=======

Method
------

.. table:: **Table 1** Method description

   +--------+--------------------------------------------------------------------+------------------------+
   | Method | URI                                                                | Description            |
   +========+====================================================================+========================+
   | HEAD   | /v1/{account}/{container}/{object}{?temp_url_sig,temp_url_expires} | Shows object metadata. |
   +--------+--------------------------------------------------------------------+------------------------+

**{account}** indicates the name of an account.

**{container}** indicates the name of a container.

**{object}** indicates the name of an object.

This operation does not involve a request body.

Example Request
---------------

Show object metadata:

.. code-block:: text

   curl -i $publicURL/marktwain/goodbye -X HEAD -H "X-Auth-Token:$token"

Request Query Parameters
------------------------

+-----------------------+-----------------------+----------------------------------------------------------------+
| Parameter             | Type                  | Description                                                    |
+=======================+=======================+================================================================+
| temp_url_sig          | String                | Used with TempURL to sign the request.                         |
|                       |                       |                                                                |
|                       | (Optional)            |                                                                |
+-----------------------+-----------------------+----------------------------------------------------------------+
| temp_url_expires      | String                | Used with TempURL to specify the expiry time of the signature. |
|                       |                       |                                                                |
|                       | (Optional)            |                                                                |
+-----------------------+-----------------------+----------------------------------------------------------------+

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

.. table:: **Table 2** Request header parameters

   +-----------------------+-----------------------+-----------------------+
   | Header                | Type                  | Description           |
   +=======================+=======================+=======================+
   | X-Auth-Token          | String                | Authentication token. |
   |                       |                       |                       |
   |                       | (Required)            |                       |
   +-----------------------+-----------------------+-----------------------+
