:original_name: obs_03_0046.html

.. _obs_03_0046:

Request
=======

Method
------

.. table:: **Table 1** Method description

   +--------+---------------------------+-----------------------------------------------------------------------------------------------------------------------+
   | Method | URI                       | Description                                                                                                           |
   +========+===========================+=======================================================================================================================+
   | HEAD   | /v1/{account}/{container} | Shows container metadata, including the number of objects and the total bytes of all objects stored in the container. |
   +--------+---------------------------+-----------------------------------------------------------------------------------------------------------------------+

**{account}** indicates the name of an account.

**{container}** indicates the name of a container.

This operation does not involve a request body.

Example Request
---------------

Show metadata of container **marktwain**:

.. code-block::

   curl -i $publicURL/marktwain -X HEAD -H "X-Auth-Token:$token"

Request Query Parameters
------------------------

This request does not include query parameters.

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
