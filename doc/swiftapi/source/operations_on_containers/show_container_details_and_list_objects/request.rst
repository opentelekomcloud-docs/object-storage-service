:original_name: obs_03_0030.html

.. _obs_03_0030:

Request
=======

Method
------

.. table:: **Table 1** Method description

   +--------+----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------+
   | Method | URI                                                                              | Description                                                                                                     |
   +========+==================================================================================+=================================================================================================================+
   | GET    | /v1/{account}/{container}{?limit,marker,end_marker,prefix,format,delimiter,path} | Shows metadata of a specified container and lists objects, sorted by name in ascending order, in the container. |
   +--------+----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------+

**{account}** indicates the name of an account.

**{container}** indicates the name of a container.

This operation does not involve a request body.

Example Request
---------------

Show container details for and list objects in the **marktwain** container, and ask for a JSON response:

.. code-block::

   curl -i $publicURL/marktwain?format=json -X GET -H "X-Auth-Token:$token"

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

+-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
| Parameter             | Type                  | Description                                                                                                               |
+=======================+=======================+===========================================================================================================================+
| X-Auth-Token          | String                | Authentication token.                                                                                                     |
|                       |                       |                                                                                                                           |
|                       | (Required)            |                                                                                                                           |
+-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
| Accept                | String                | Similar to the **format** query parameter, set this header to **application/json**, **application/xml**, or **text/xml**. |
|                       |                       |                                                                                                                           |
|                       | (Optional)            |                                                                                                                           |
+-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+

Request Query Parameters
------------------------

:ref:`Table 2 <obs_03_0030__table53889649171022>` describes the query parameters of "Show Container Details and List Objects".

.. _obs_03_0030__table53889649171022:

.. table:: **Table 2** Request query parameters

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                          |
   +=======================+=======================+======================================================================================================================================================================+
   | limit                 | Int                   | Limits the number of objects in a query result.                                                                                                                      |
   |                       |                       |                                                                                                                                                                      |
   |                       | (Optional)            | Value range: **0** to **10000**                                                                                                                                      |
   |                       |                       |                                                                                                                                                                      |
   |                       |                       | Default value: **10000**                                                                                                                                             |
   |                       |                       |                                                                                                                                                                      |
   |                       |                       | If this parameter is set to a value larger than 10000, an error is reported.                                                                                         |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker                | String                | Returns object names that are greater than the specified marker.                                                                                                     |
   |                       |                       |                                                                                                                                                                      |
   |                       | (Optional)            |                                                                                                                                                                      |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_marker            | String                | Returns object names that are smaller than the specified marker.                                                                                                     |
   |                       |                       |                                                                                                                                                                      |
   |                       | (Optional)            |                                                                                                                                                                      |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | format                | String                | Sets the format of the returned object list. The valid values are **plain** (default), **json**, and **xml**. Its function is the same as **Accept**.                |
   |                       |                       |                                                                                                                                                                      |
   |                       | (Optional)            |                                                                                                                                                                      |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | prefix                | String                | Returns objects that have the specified prefix.                                                                                                                      |
   |                       |                       |                                                                                                                                                                      |
   |                       | (Optional)            |                                                                                                                                                                      |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | delimiter             | Char                  | Returns the object names that are nested in the container.                                                                                                           |
   |                       |                       |                                                                                                                                                                      |
   |                       | (Optional)            |                                                                                                                                                                      |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | path                  | String                | Returns the object names that are nested in the specified path. Equivalent to setting **delimiter** to **/** and **prefix** to the path with a slash (/) at the end. |
   |                       |                       |                                                                                                                                                                      |
   |                       | (Optional)            |                                                                                                                                                                      |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

There are two issues with OpenStack Swift that OBS (compatible with OpenStack Swift) does not have:

-  If the first character of an object is set to the **delimiter** parameter, the expected result cannot be correctly returned.

   For example, if **bucket01** contains object **obj0**, and the **delimiter=o** parameter is used in a query, OBS (compatible with OpenStack Swift) returns result **o**. OpenStack Swift, however, returns **obj0** which is incorrect.

-  If the **path** parameter is used, subdirectories cannot be shown.

   Given the same configuration for OBS (compatible with OpenStack Swift) and OpenStack Swift, suppose a container includes objects **o/1**, **o/2**, and **o/subdir1/1**. When the request (with **path=o** used) is sent to OpenStack Swift, **o/subdir1/1** would not be found.

   +-----------------------------------+-----------------------------------+
   | Requested Party                   | Returned Result                   |
   +===================================+===================================+
   | OpenStack Swift                   | o/1                               |
   |                                   |                                   |
   |                                   | o/2                               |
   +-----------------------------------+-----------------------------------+
   | OBS                               | o/1                               |
   |                                   |                                   |
   |                                   | o/2                               |
   |                                   |                                   |
   |                                   | o/subdir1/1                       |
   +-----------------------------------+-----------------------------------+
