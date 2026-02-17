:original_name: obs_11_0050.html

.. _obs_11_0050:

Creating a Folder
=================

Function
--------

You can use this command to create a folder in a specified bucket or local file system.

.. important::

   No error is returned if a folder with the same name as an existing one is created, and the content of the existing folder remains unchanged.

Command Line Structure
----------------------

-  In Windows

   -  Creating a folder in a specified bucket

      .. code-block::

         obsutil mkdir obs://bucket/folder[/subfolder1/subfolder2] [-config=xxx]

   -  Creating a folder in the local file system

      .. code-block::

         obsutil mkdir folder_url [-config=xxx]

-  In Linux or macOS

   -  Creating a folder in a specified bucket

      .. code-block::

         ./obsutil mkdir obs://bucket/folder[/subfolder1/subfolder2] [-config=xxx]

   -  Creating a folder in the local file system

      .. code-block::

         ./obsutil mkdir folder_url [-config=xxx]

Examples
--------

-  Take the Windows OS as an example. Run the **obsutil mkdir obs://bucket-test/folder1/folder2** command to create a folder in a bucket.

   .. code-block::

      obsutil mkdir obs://bucket-test/folder1/folder2

      The bucket [bucket-test] does not support POSIX, create folder(s) step by step
      Create folder [obs://bucket-test/folder1/] successfully, request id [0000016979E1D23C860BB3D8E4577C5E]
      Create folder [obs://bucket-test/folder1/folder2] successfully, request id [0000016979E1D2B2860BB5181229C72C]

Parameter Description
---------------------

+-----------------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter             | Optional or Mandatory                                     | Description                                                                                                                                                                    |
+=======================+===========================================================+================================================================================================================================================================================+
| bucket                | Mandatory when creating a folder in a specified bucket    | The bucket name                                                                                                                                                                |
+-----------------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| folder                | Mandatory when creating a folder in a specified bucket    | The folder path in the bucket. This value can contain multi-level folders. Separate each level with a slash (/).                                                               |
+-----------------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| folder_url            | Mandatory when creating a folder in the local file system | The folder path in the local file system. The value can be an absolute path or a relative path.                                                                                |
+-----------------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| bucket-cname          | Optional (additional parameter)                           | The user-defined domain name bound to the bucket                                                                                                                               |
|                       |                                                           |                                                                                                                                                                                |
|                       |                                                           | .. note::                                                                                                                                                                      |
|                       |                                                           |                                                                                                                                                                                |
|                       |                                                           |    This parameter is only supported by obsutil 5.7.9 and later.                                                                                                                |
+-----------------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| config                | Optional (additional parameter)                           | The user-defined configuration file for executing the current command. For details about parameters that can be configured, see :ref:`Configuration Parameters <obs_11_0035>`. |
+-----------------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| payer                 | Optional (additional parameter)                           | Specifies that requester pays is enabled.                                                                                                                                      |
+-----------------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
