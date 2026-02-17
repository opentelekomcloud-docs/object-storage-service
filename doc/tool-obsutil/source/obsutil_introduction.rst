:original_name: obs_11_0001.html

.. _obs_11_0001:

obsutil Introduction
====================

obsutil is a command line tool for accessing and managing OBS. You can use this tool to create buckets and upload, download, or delete files/folders. If you are familiar with the command line interface (CLI), obsutil is a good choice in batch processing and automatic tasks.

obsutil is compatible with Windows, Linux, and macOS. :ref:`Table 1 <obs_11_0001__table1282175018104>` lists the recommended operating system (OS) versions.

.. _obs_11_0001__table1282175018104:

.. table:: **Table 1** Recommended OS versions for obsutil

   +-----------------------------------+-----------------------------------+
   | OS                                | Recommended Version               |
   +===================================+===================================+
   | Windows                           | -  Windows 7                      |
   |                                   | -  Windows 8                      |
   |                                   | -  Windows 10                     |
   |                                   | -  Windows 11                     |
   |                                   | -  Windows Server 2016            |
   |                                   | -  Windows Server 2019            |
   +-----------------------------------+-----------------------------------+
   | Linux                             | -  SUSE 11                        |
   |                                   | -  EulerOS 2                      |
   |                                   | -  CentOS 7                       |
   +-----------------------------------+-----------------------------------+
   | macOS                             | macOS 10.13.4                     |
   +-----------------------------------+-----------------------------------+

Advantages
----------

obsutil has the following advantages:

#. Easy to use
#. Lightweight and installation-free
#. Compatible with Windows, Linux, and macOS
#. Excellent performance and diversified configurations

Application Scenarios
---------------------

-  Automatic backup and archiving, for example, periodically uploading local data to OBS
-  Operations that you cannot perform using other tools (like OBS Browser+). Such operations include synchronously uploading, downloading, and copying objects.

Functions
---------

:ref:`Table 2 <obs_11_0001__table1233162315227>` lists the functions of obsutil.

.. _obs_11_0001__table1233162315227:

.. table:: **Table 2** Functions of obsutil

   +----------------------------------------------+-------------------------------------------------------------------------------------------+
   | Function                                     | Description                                                                               |
   +==============================================+===========================================================================================+
   | :ref:`Basic bucket management <obs_11_0007>` | Allows you to:                                                                            |
   |                                              |                                                                                           |
   |                                              | -  Create buckets of different storage classes in specific regions.                       |
   |                                              | -  Delete buckets.                                                                        |
   |                                              | -  Get the bucket list or configuration information.                                      |
   +----------------------------------------------+-------------------------------------------------------------------------------------------+
   | :ref:`Basic object management <obs_11_0012>` | Allows you to upload, download, delete, and list objects. In detail, you can:             |
   |                                              |                                                                                           |
   |                                              | -  Upload one or more files or folders.                                                   |
   |                                              | -  Upload large files in multipart uploads.                                               |
   |                                              | -  Synchronously upload, download, and copy incremental objects.                          |
   |                                              | -  Copy a single object or a batch of objects sharing the same prefix.                    |
   |                                              | -  Move a single object or a batch of objects sharing the same prefix.                    |
   |                                              | -  Resume failed upload, download, or copy tasks.                                         |
   +----------------------------------------------+-------------------------------------------------------------------------------------------+
   | :ref:`Logging <obs_11_0056>`                 | Provides logging on your client to record operations on buckets and objects for analysis. |
   +----------------------------------------------+-------------------------------------------------------------------------------------------+

Command Line Structures
-----------------------

Below describes how to use commands in obsutil:

-  In Windows

   **obsutil** *command* *[parameters...]* *[options...]*

-  In Linux or macOS

   **./\ obsutil** *command [parameters...] [options...]*

.. note::

   -  *command* indicates the command to execute, for example, **ls** or **cp**.

   -  *parameters* indicates mandatory parameters, for example, the bucket name during bucket creation.

   -  *options* indicates optional parameters. They must start with a hyphen (-).

   -  Square brackets ([]) are not part of a command. Remove them before executing a specific command.

   -  You must escape special characters (including & < > and spaces) in a command using quotation marks. Single quotation marks are for Linux or macOS, and double quotation marks for Windows.

   -  You can pass additional parameters in the **-**\ *key*\ **=**\ *value* or **-**\ *key* *value* format, for example, **-acl=private**, or **-acl private**. Both formats are the same. Choose one as you like.

   -  In Windows, you can execute **obsutil.exe** to enter interactive mode. In this mode, you can run *command [parameters...] [options...]* where **obsutil** is not needed. Below gives an example:

      .. code-block::

         Enter "exit" or "quit" to logout
         Enter "help" or "help command" to show help docs
         Input your command:
         -->ls -limit=3 -s
         obs://bucket-001
         obs://bucket-002
         obs://bucket-003
         Bucket number: 3

         Input your command:
         -->

   -  If you log in to a remote macOS or Linux via SSH to use obsutil, set **TMOUT** to **0** to prevent obsutil from logging out due to SSH timeout.
