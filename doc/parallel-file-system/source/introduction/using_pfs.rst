:original_name: obs_13_0010.html

.. _obs_13_0010:

Using PFS
=========

PFS provides the console and REST APIs for managing and accessing data. Your applications can be seamlessly interconnected with PFS. No modifications to your applications are needed. You can process files stored in PFS anytime, anywhere, and quickly obtain the processed files. PFS supports both POSIX and OBS APIs, so you can process files the same way you process objects. There is flexible conversion supported between objects and files.

You can use PFS in the following ways:

.. note::

   Access permissions for OBS buckets also apply to parallel file systems. Before using a parallel file system, ensure that you have the required permissions to access OBS buckets.

.. table:: **Table 1** How to use PFS

   +---------+---------------------------------------------------------------------------------------------------------------------+------------------------------------------------------+
   | Method  | Function                                                                                                            | Reference                                            |
   +=========+=====================================================================================================================+======================================================+
   | Console | On the console, you can create parallel file systems, and you can also view and manage your file systems and files. | :ref:`Creating a Parallel File System <obs_13_0002>` |
   +---------+---------------------------------------------------------------------------------------------------------------------+------------------------------------------------------+
   | OBS API | Use parallel file systems by calling OBS APIs.                                                                      | :ref:`Supported APIs <obs_13_0004>`                  |
   +---------+---------------------------------------------------------------------------------------------------------------------+------------------------------------------------------+
