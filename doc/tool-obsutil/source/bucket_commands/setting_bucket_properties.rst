:original_name: obs_11_0040.html

.. _obs_11_0040:

Setting Bucket Properties
=========================

Function
--------

You can use this command to set the properties of a bucket, such as storage classes and access policies.

Command Line Structure
----------------------

-  In Windows

   .. code-block::

      obsutil chattri obs://bucket [-sc=xxx] [-acl=xxx] [-aclXml=xxx] [-config=xxx]

-  In Linux or macOS

   .. code-block::

      ./obsutil chattri obs://bucket [-sc=xxx] [-acl=xxx] [-aclXml=xxx] [-config=xxx]

Examples
--------

-  Take the Windows OS as an example. Run the **obsutil chattri obs://bucket-test -acl=private** command to change the access control policy of the bucket to private read and write.

   .. code-block::

      obsutil chattri obs://bucket-test -acl=private

      Start at 2024-09-29 07:58:46.0506904 +0000 UTC

      Set the acl of bucket [bucket-test] to [private] successfully, request id [04050000016836C5DA6FB21F14A2A0C0]

Parameter Description
---------------------

+-----------------------+---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter             | Optional or Mandatory           | Description                                                                                                                                                                                                                                                      |
+=======================+=================================+==================================================================================================================================================================================================================================================================+
| bucket                | Mandatory                       | The bucket name                                                                                                                                                                                                                                                  |
+-----------------------+---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| sc                    | Optional (additional parameter) | The default storage class of the bucket. Possible values are:                                                                                                                                                                                                    |
|                       |                                 |                                                                                                                                                                                                                                                                  |
|                       |                                 | -  **standard**: Standard storage class. It features low access latency and high throughput, and is applicable to storing frequently accessed data (multiple accesses per month) or data that is smaller than 1 MB.                                              |
|                       |                                 | -  **warm**: Warm storage class. It is ideal for storing infrequently accessed (less than 12 times a year) data, but when needed, the access has to be fast.                                                                                                     |
|                       |                                 | -  **cold**: Cold storage class. It provides secure, durable, and inexpensive storage for rarely-accessed (once a year) data.                                                                                                                                    |
+-----------------------+---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| acl                   | Optional (additional parameter) | The predefined access control policy of the bucket. Possible values are:                                                                                                                                                                                         |
|                       |                                 |                                                                                                                                                                                                                                                                  |
|                       |                                 | -  private                                                                                                                                                                                                                                                       |
|                       |                                 | -  public-read                                                                                                                                                                                                                                                   |
|                       |                                 | -  public-read-write                                                                                                                                                                                                                                             |
|                       |                                 |                                                                                                                                                                                                                                                                  |
|                       |                                 | .. note::                                                                                                                                                                                                                                                        |
|                       |                                 |                                                                                                                                                                                                                                                                  |
|                       |                                 |    The preceding three values indicate private read and write, public read, and public read and write.                                                                                                                                                           |
+-----------------------+---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| aclXml                | Optional (additional parameter) | The bucket's access control policy, in XML format                                                                                                                                                                                                                |
|                       |                                 |                                                                                                                                                                                                                                                                  |
|                       |                                 | .. code-block::                                                                                                                                                                                                                                                  |
|                       |                                 |                                                                                                                                                                                                                                                                  |
|                       |                                 |    <AccessControlPolicy>                                                                                                                                                                                                                                         |
|                       |                                 |        <Owner>                                                                                                                                                                                                                                                   |
|                       |                                 |            <ID>ownerid</ID>                                                                                                                                                                                                                                      |
|                       |                                 |        </Owner>                                                                                                                                                                                                                                                  |
|                       |                                 |        <AccessControlList>                                                                                                                                                                                                                                       |
|                       |                                 |            <Grant>                                                                                                                                                                                                                                               |
|                       |                                 |                <Grantee>                                                                                                                                                                                                                                         |
|                       |                                 |                    <ID>userid</ID>                                                                                                                                                                                                                               |
|                       |                                 |                </Grantee>                                                                                                                                                                                                                                        |
|                       |                                 |                <Permission>[WRITE|WRITE_ACP|READ|READ_ACP|FULL_CONTROL]</Permission>                                                                                                                                                                             |
|                       |                                 |            </Grant>                                                                                                                                                                                                                                              |
|                       |                                 |            <Grant>                                                                                                                                                                                                                                               |
|                       |                                 |                <Grantee>                                                                                                                                                                                                                                         |
|                       |                                 |                    <Canned>Everyone</Canned>                                                                                                                                                                                                                     |
|                       |                                 |                </Grantee>                                                                                                                                                                                                                                        |
|                       |                                 |                <Permission>[WRITE|WRITE_ACP|READ|READ_ACP|FULL_CONTROL]</Permission>                                                                                                                                                                             |
|                       |                                 |            </Grant>                                                                                                                                                                                                                                              |
|                       |                                 |        </AccessControlList>                                                                                                                                                                                                                                      |
|                       |                                 |    </AccessControlPolicy>                                                                                                                                                                                                                                        |
|                       |                                 |                                                                                                                                                                                                                                                                  |
|                       |                                 | .. note::                                                                                                                                                                                                                                                        |
|                       |                                 |                                                                                                                                                                                                                                                                  |
|                       |                                 |    -  **Owner**: Optional. Specify the bucket owner's ID.                                                                                                                                                                                                        |
|                       |                                 |    -  In **AccessControlList**, the **Grant** field contains the authorized users. **Grantee** specifies the IDs of authorized users. **Canned** specifies the authorized user group (currently, only **Everyone** is supported).                                |
|                       |                                 |    -  The following permissions can be granted: WRITE (write), WRITE_ACP (write ACL), READ (read), READ_ACP (read ACL), and FULL_CONTROL (full control).                                                                                                         |
|                       |                                 |                                                                                                                                                                                                                                                                  |
|                       |                                 | .. important::                                                                                                                                                                                                                                                   |
|                       |                                 |                                                                                                                                                                                                                                                                  |
|                       |                                 |    NOTICE:                                                                                                                                                                                                                                                       |
|                       |                                 |    Because angle brackets (<) and (>) are unavoidably included in the parameter value, you must use quotation marks to enclose them for escaping when running the command. Use single quotation marks for Linux or macOS and double quotation marks for Windows. |
+-----------------------+---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| bucket-cname          | Optional (additional parameter) | The user-defined domain name bound to the bucket                                                                                                                                                                                                                 |
|                       |                                 |                                                                                                                                                                                                                                                                  |
|                       |                                 | .. note::                                                                                                                                                                                                                                                        |
|                       |                                 |                                                                                                                                                                                                                                                                  |
|                       |                                 |    This parameter is only supported by obsutil 5.7.9 and later.                                                                                                                                                                                                  |
+-----------------------+---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| config                | Optional (additional parameter) | The user-defined configuration file for executing the current command. For details about parameters that can be configured, see :ref:`Configuration Parameters <obs_11_0035>`.                                                                                   |
+-----------------------+---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| payer                 | Optional (additional parameter) | Specifies that requester pays is enabled.                                                                                                                                                                                                                        |
+-----------------------+---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. note::

   Only one from **sc**, **acl**, or **aclXml** can be set for each command.
