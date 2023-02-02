:original_name: obs_03_0075.html

.. _obs_03_0075:

Request
=======

Method
------

.. table:: **Table 1** Method description

   +--------+------------------------------------+-----------------------------------------------+
   | Method | URI                                | Description                                   |
   +========+====================================+===============================================+
   | POST   | /v1/{account}/{container}/{object} | Creates, updates, or deletes object metadata. |
   +--------+------------------------------------+-----------------------------------------------+

**{account}** indicates the name of an account.

**{container}** indicates the name of a container.

**{object}** indicates the name of an object.

A POST request deletes all existing user metadata.

Metadata creation or update depends on whether the specified metadata already exists. Existing metadata is updated, and missing metadata is created.

This operation does not involve a request body.

Example Request
---------------

Create or update metadata:

.. code-block:: text

   curl -i $publicURL/marktwain/goodbye  -X POST -H "X-Auth-Token:$token" -H "X-Object-Meta-name:value"

Delete metadata:

.. code-block:: text

   curl -i $publicURL/marktwain/goodbye -X POST -H "X-Auth-Token:$token" -H "X-Object-Meta-name:"

Request Query Parameters
------------------------

This request does not include query parameters.

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

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Header                | Type                  | Description                                                                                                                                                                                                                                                      |
   +=======================+=======================+==================================================================================================================================================================================================================================================================+
   | X-Auth-Token          | String                | Authentication token. If you omit this header, your request fails unless the account owner has granted you access through an ACL.                                                                                                                                |
   |                       |                       |                                                                                                                                                                                                                                                                  |
   |                       | (Required)            |                                                                                                                                                                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Object-Meta-name    | String                | Object metadata, where **{name}** is the name of the metadata item. To delete this item, leave **{name}** empty in this header. You must specify an **X-Object-Meta-{name}** header for each metadata item (for each **{name}**) that you want to add or update. |
   |                       |                       |                                                                                                                                                                                                                                                                  |
   |                       | (Optional)            |                                                                                                                                                                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type          | String                | Sets the MIME type of the object.                                                                                                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                                                                                                  |
   |                       | (Optional)            |                                                                                                                                                                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Detect-Content-Type | Boolean               | If it is set to **true**, OBS guesses the content type based on the file name extension and ignores the value sent in the **Content-Type** header, if present.                                                                                                   |
   |                       |                       |                                                                                                                                                                                                                                                                  |
   |                       | (Optional)            |                                                                                                                                                                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Length        | String                | Set to the length of the object content. Do not set if chunked transfer encoding is being used.                                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                                                                                                                  |
   |                       | (Optional)            |                                                                                                                                                                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Disposition   | String                | When the header is set to **{newname}** and an object is downloaded through a browser, the default object name **{newname}** is returned.                                                                                                                        |
   |                       |                       |                                                                                                                                                                                                                                                                  |
   |                       | (Optional)            |                                                                                                                                                                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Encoding      | String                | If this header is set, the value is the encoding format used when an object is downloaded through a browser.                                                                                                                                                     |
   |                       |                       |                                                                                                                                                                                                                                                                  |
   |                       | (Optional)            |                                                                                                                                                                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
