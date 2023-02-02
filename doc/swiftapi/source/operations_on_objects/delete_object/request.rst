:original_name: obs_03_0067.html

.. _obs_03_0067:

Request
=======

Method
------

.. table:: **Table 1** Method description

   +--------+---------------------------------------------------------+----------------------------------------------------+
   | Method | URI                                                     | Description                                        |
   +========+=========================================================+====================================================+
   | DELETE | /v1/{account}/{container}/{object}{?multipart-manifest} | Permanently deletes an object from the OBS system. |
   +--------+---------------------------------------------------------+----------------------------------------------------+

**{account}** indicates the name of an account.

**{container}** indicates the name of a container.

**{object}** indicates the name of an object.

This operation does not involve a request body.

Example Request
---------------

Delete the **helloworld** object from the **marktwain** container.

.. code-block:: text

   curl -i $publicURL/
   marktwain/helloworld -X DELETE -H "X-Auth-Token: $token"

Request Query Parameters
------------------------

+-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Header                | Type                  | Description                                                                                                                                                        |
+=======================+=======================+====================================================================================================================================================================+
| multipart-manifest    | String                | If you include the **multipart-manifest=delete** query parameter and the object is a static large object, the segment objects and the manifest object are deleted. |
|                       |                       |                                                                                                                                                                    |
|                       | (Optional)            | If you omit the **multipart-manifest=delete** query parameter, the manifest object is deleted and the segment objects are not deleted.                             |
|                       |                       |                                                                                                                                                                    |
|                       |                       | If this is a dynamic large object, do not specify **multipart-manifest=delete** query parameter.                                                                   |
+-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+
   | Header                | Type                  | Description                                                                                                                       |
   +=======================+=======================+===================================================================================================================================+
   | X-Auth-Token          | String                | Authentication token. If you omit this header, your request fails unless the account owner has granted you access through an ACL. |
   |                       |                       |                                                                                                                                   |
   |                       | (Required)            |                                                                                                                                   |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+
