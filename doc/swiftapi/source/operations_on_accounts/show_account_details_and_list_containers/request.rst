:original_name: obs_03_0017.html

.. _obs_03_0017:

Request
=======

Method
------

.. table:: **Table 1** Method description

   +--------+-----------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | Method | URI                                                             | Description                                                                                                       |
   +========+=================================================================+===================================================================================================================+
   | GET    | /v1/{account}{?limit,marker,end_marker,format,prefix,delimiter} | Shows details of a specified account and lists the containers, sorted by name in ascending order, in the account. |
   +--------+-----------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+

**{account}** indicates the name of an account.

This operation does not involve a request body.

Example Request
---------------

Show account details and list containers, and ask for a JSON response:

.. code-block::

   curl -i $publicURL?format=json -X GET -H "X-Auth-Token:$token"

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

.. note::

   If the value of **Accept** is invalid, OBS (compatible with OpenStack Swift) returns the 406 (Not Acceptable) error code. Then, OpenStack Swift will process the request based on the default value of **Accept**.

Request Query Parameters
------------------------

.. table:: **Table 2** Request query parameters

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                              |
   +=======================+=======================+==========================================================================================================================================================+
   | limit                 | Int                   | Limits the number of containers in a query result.                                                                                                       |
   |                       |                       |                                                                                                                                                          |
   |                       | (Optional)            | Value range: **0** to **10000**                                                                                                                          |
   |                       |                       |                                                                                                                                                          |
   |                       |                       | Default value: **10000**                                                                                                                                 |
   |                       |                       |                                                                                                                                                          |
   |                       |                       | If this parameter is set to a value larger than 10000, an error is reported.                                                                             |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker                | String                | Returns container names that are greater than the specified marker.                                                                                      |
   |                       |                       |                                                                                                                                                          |
   |                       | (Optional)            |                                                                                                                                                          |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_marker            | String                | Returns container names that are smaller than the specified marker.                                                                                      |
   |                       |                       |                                                                                                                                                          |
   |                       | (Optional)            |                                                                                                                                                          |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | format                | String                | Sets the format of the returned container list. The valid values are **plain** (default), **json**, and **xml**. Its function is the same as **Accept**. |
   |                       |                       |                                                                                                                                                          |
   |                       | (Optional)            |                                                                                                                                                          |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | prefix                | String                | Returns containers that have the specified prefix.                                                                                                       |
   |                       |                       |                                                                                                                                                          |
   |                       | (Optional)            |                                                                                                                                                          |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | delimiter             | Char                  | Returns the container names that are nested in the account.                                                                                              |
   |                       |                       |                                                                                                                                                          |
   |                       | (Optional)            |                                                                                                                                                          |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
