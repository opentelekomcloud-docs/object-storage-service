:original_name: obs_03_0034.html

.. _obs_03_0034:

Request
=======

Method
------

.. table:: **Table 1** Method description

   +--------+---------------------------+---------------------------------------------+
   | Method | URI                       | Description                                 |
   +========+===========================+=============================================+
   | PUT    | /v1/{account}/{container} | Creates a container in a specified account. |
   +--------+---------------------------+---------------------------------------------+

**{account}** indicates the name of an account.

**{container}** indicates the name of a container.

This operation does not involve a request body.

Example Request
---------------

Create a container named **marktwain**:

.. code-block::

   curl -i $publicURL/marktwain -X PUT -H "X-Auth-Token:$token"

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
| {container}           | String                | A unique container name.                                                                 |
|                       |                       |                                                                                          |
|                       | (Required)            | For details about container naming rules, see :ref:`Naming Rules <obs_03_0009>`.         |
+-----------------------+-----------------------+------------------------------------------------------------------------------------------+

:ref:`Table 2 <obs_03_0034__table2213898993436>` describes the request header parameters.

.. _obs_03_0034__table2213898993436:

.. table:: **Table 2** Request header parameters

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Header                | Type                  | Description                                                                                                                                                                                                                                                                                                     |
   +=======================+=======================+=================================================================================================================================================================================================================================================================================================================+
   | X-Auth-Token          | String                | Authentication token.                                                                                                                                                                                                                                                                                           |
   |                       |                       |                                                                                                                                                                                                                                                                                                                 |
   |                       | (Required)            |                                                                                                                                                                                                                                                                                                                 |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Container-Read      | String                | Sets a container access control list (ACL) that grants read access.                                                                                                                                                                                                                                             |
   |                       |                       |                                                                                                                                                                                                                                                                                                                 |
   |                       | (Optional)            | To set the container read ACL:                                                                                                                                                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                                                                                                                                                                 |
   |                       |                       | curl -X {PUT|POST} -i -H "X-Auth-Token: $token" -H \\                                                                                                                                                                                                                                                           |
   |                       |                       |                                                                                                                                                                                                                                                                                                                 |
   |                       |                       | "X-Container-Read: ACL" $publicURL/Container                                                                                                                                                                                                                                                                    |
   |                       |                       |                                                                                                                                                                                                                                                                                                                 |
   |                       |                       | For details about ACL format rules, see the next section.                                                                                                                                                                                                                                                       |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Container-Write     | String                | Sets a container ACL that grants write access.                                                                                                                                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                                                                                                                                                                 |
   |                       | (Optional)            | To set the container write ACL:                                                                                                                                                                                                                                                                                 |
   |                       |                       |                                                                                                                                                                                                                                                                                                                 |
   |                       |                       | curl -X {PUT|POST} -i -H "X-Auth-Token: $token" -H \\                                                                                                                                                                                                                                                           |
   |                       |                       |                                                                                                                                                                                                                                                                                                                 |
   |                       |                       | "X-Container-Write: ACL" $publicURL/Container                                                                                                                                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                                                                                                                                                                 |
   |                       |                       | For details about ACL format rules, see the next section.                                                                                                                                                                                                                                                       |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Container-Meta-name | String                | Container metadata. **{name}** is the name of a metadata item that you want to add, update, or delete. To delete this item, leave **{name}** empty in this header. You must specify an **X-Container-Meta-{name}** header for each metadata item (for each **{name}**) that you want to add, update, or delete. |
   |                       |                       |                                                                                                                                                                                                                                                                                                                 |
   |                       | (Optional)            |                                                                                                                                                                                                                                                                                                                 |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _obs_03_0034__section1003248895852:

Container Read ACL Rules (X-Container-Read)
-------------------------------------------

Container read ACL rules are as follows:

-  **.r:*#**: All referrers.
-  **.r:example.com,swift.example.com#**: Comma-separated list of referrers.
-  **.rlistings#**: Container listing access, always combined with **.r:**.
-  **.r:-example.com#**: Comma-separated list of inaccessible addresses.
-  **{account:user} #**: **account** is **projectid** and **user** is **userid**.

.. _obs_03_0034__section39003754101721:

Container Write ACL Rules (X-Container-Write)
---------------------------------------------

Container write ACL rules are as follows:

-  **{account:user} #**: Only this format is supported. **account** is **projectid** and **user** is **userid**.
