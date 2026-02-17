:original_name: obs_11_0062.html

.. _obs_11_0062:

Creating an Authorization Code for Directory Sharing
====================================================

Function
--------

You can use this command to specify the bucket name, object name prefix, and access code to create an authorization code for directory sharing.

Command Line Structure
----------------------

-  In Windows

   .. code-block::

      obsutil create-share obs://bucket[/prefix] [-ac=xxx] [-vp=xxx] [-dst=xxx] [-config=xxx]

-  In Linux or macOS

   .. code-block::

      ./obsutil create-share obs://bucket[/prefix] [-ac=xxx] [-vp=xxx] [-dst=xxx] [-config=xxx]

Examples
--------

-  In Windows, you can run the **obsutil create-share obs://bucket/test/ -ac=123456 -vp=1m** command to create an authorization code that is valid within one month.

   .. code-block::

      obsutil create-share obs://bucket/test/ -ac=123456 -vp=1m

      Authorization Code:
      token=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

      Access Code:
      123456

      Valid Until:
      Sat, 26 Oct 2019 11:28:10 GMT +0800

Parameter Description
---------------------

+-----------------------+---------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter             | Optional or Mandatory           | Description                                                                                                                                                                                                                                                                                                                                                               |
+=======================+=================================+===========================================================================================================================================================================================================================================================================================================================================================================+
| bucket                | Mandatory                       | The bucket name                                                                                                                                                                                                                                                                                                                                                           |
+-----------------------+---------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| prefix                | Optional                        | The prefix of an object name. If this parameter is specified, objects starting with this prefix are shared. If this parameter is left blank, all objects in the bucket are shared.                                                                                                                                                                                        |
|                       |                                 |                                                                                                                                                                                                                                                                                                                                                                           |
|                       |                                 | .. note::                                                                                                                                                                                                                                                                                                                                                                 |
|                       |                                 |                                                                                                                                                                                                                                                                                                                                                                           |
|                       |                                 |    It is recommended that the value end with a slash (/).                                                                                                                                                                                                                                                                                                                 |
+-----------------------+---------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| ac                    | Optional (additional parameter) | The access code                                                                                                                                                                                                                                                                                                                                                           |
|                       |                                 |                                                                                                                                                                                                                                                                                                                                                                           |
|                       |                                 | .. note::                                                                                                                                                                                                                                                                                                                                                                 |
|                       |                                 |                                                                                                                                                                                                                                                                                                                                                                           |
|                       |                                 |    -  If no access code is passed using this parameter, obsutil tool prompts you to enter the access code in interactive mode.                                                                                                                                                                                                                                            |
|                       |                                 |    -  An access code is a six-digit string.                                                                                                                                                                                                                                                                                                                               |
+-----------------------+---------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| vp                    | Optional (additional parameter) | The validity period of an authorization code. The default value is one day, indicating that the generated authorization code is valid for only one day.                                                                                                                                                                                                                   |
|                       |                                 |                                                                                                                                                                                                                                                                                                                                                                           |
|                       |                                 | .. note::                                                                                                                                                                                                                                                                                                                                                                 |
|                       |                                 |                                                                                                                                                                                                                                                                                                                                                                           |
|                       |                                 |    -  This parameter supports different time units, including: **m** (month), **w** (week), **d** (day), **h** (hour), **min** (minute), and **s** (second). For example, **1d** indicates that the authorization code is valid within one day, **2w** indicates that the code is valid within two weeks, and **3h** indicates that the code is valid within three hours. |
|                       |                                 |    -  The default time unit is **s** (second), for example, **3600** indicates that the authorization code is valid within 3600 seconds.                                                                                                                                                                                                                                  |
+-----------------------+---------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| dst                   | Optional (additional parameter) | The path for storing the generated authorization code                                                                                                                                                                                                                                                                                                                     |
+-----------------------+---------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| config                | Optional (additional parameter) | The user-defined configuration file for executing the current command. For details about parameters that can be configured, see :ref:`Configuration Parameters <obs_11_0035>`.                                                                                                                                                                                            |
+-----------------------+---------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| payer                 | Optional (additional parameter) | Specifies that requester pays is enabled.                                                                                                                                                                                                                                                                                                                                 |
+-----------------------+---------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

================== ==========================
Field              Description
================== ==========================
Authorization Code The code for authorization
Access Code        The access code
Valid Until        The expiration time
================== ==========================
