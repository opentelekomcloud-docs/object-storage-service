:original_name: obs_03_0063.html

.. _obs_03_0063:

Request
=======

Method
------

.. table:: **Table 1** Method description

   +--------+------------------------------------+------------------------------------------------------------------------------+
   | Method | URI                                | Description                                                                  |
   +========+====================================+==============================================================================+
   | COPY   | /v1/{account}/{container}/{object} | Copies an object to another object in OBS (compatible with OpenStack Swift). |
   +--------+------------------------------------+------------------------------------------------------------------------------+

**{account}** indicates the name of an account.

**{container}** indicates the name of a container.

**{object}** indicates the name of an object.

This operation does not involve a request body.

Example Request
---------------

Copy the **goodbye** object from the **marktwain** container to the **janeausten** container:

.. code-block:: text

   curl -i $publicURL/marktwain/goodbye -X COPY -H "X-Auth-Token:
   $token" -H "Destination: janeausten/goodbye"

.. code-block:: text

   curl -i $publicURL/janeausten/goodbye -X PUT -H "X-Auth-Token:
   $token" -H "X-Copy-From: /marktwain/goodbye" -H "Content-Length:
   0"

Request Query Parameters
------------------------

This operation does not include request query parameters.

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

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Header                | Type                  | Description                                                                                                                                                                                          |
   +=======================+=======================+======================================================================================================================================================================================================+
   | X-Auth-Token          | String                | Authentication token. If you omit this header, your request fails unless the account owner has granted you access through an ACL.                                                                    |
   |                       |                       |                                                                                                                                                                                                      |
   |                       | (Required)            |                                                                                                                                                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Destination           | String                | The container and object name of the destination object in the **/container/object** format.                                                                                                         |
   |                       |                       |                                                                                                                                                                                                      |
   |                       | (Required)            |                                                                                                                                                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Object-Meta-name    | String                | Object metadata, where **{name}** is the name of the metadata item. You must specify an **X-Object-Meta-{name}** header for each metadata item (for each **{name}**) that you want to add or update. |
   |                       |                       |                                                                                                                                                                                                      |
   |                       | (Optional)            |                                                                                                                                                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type          | String                | Sets the MIME type of the object.                                                                                                                                                                    |
   |                       |                       |                                                                                                                                                                                                      |
   |                       | (Optional)            |                                                                                                                                                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Length        | String                | Object length.                                                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                                      |
   |                       | (Optional)            |                                                                                                                                                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Disposition   | String                | When the header is set to **{newname}** and an object is downloaded through a browser, the default object name **{newname}** is returned.                                                            |
   |                       |                       |                                                                                                                                                                                                      |
   |                       | (Optional)            |                                                                                                                                                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Encoding      | String                | If this header is set, the value is the encoding format used when an object is downloaded through a browser.                                                                                         |
   |                       |                       |                                                                                                                                                                                                      |
   |                       | (Optional)            |                                                                                                                                                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Copy-From           | String                | Container and object name of the source object in the **/container/object** format.                                                                                                                  |
   |                       |                       |                                                                                                                                                                                                      |
   |                       | (Optional)            |                                                                                                                                                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. note::

   If the **X-Copy-From** or **Destination** header is used to specify the name of a source or destination object, only the **/container/object** format is supported. OpenStack Swift lets you to use a URL as the name of a source or destination object.
