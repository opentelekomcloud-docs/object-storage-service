:original_name: obs_13_0010.html

.. _obs_13_0010:

Using PFS
=========

PFS provides both a console and REST APIs for managing and accessing data, so that your applications can seamlessly interconnect with PFS without requiring any modifications. This allows you to process files stored in PFS anytime, anywhere and retrieve the processed files quickly. PFS supports both Portable Operating System Interface (POSIX) and OBS APIs, so you can process files the same way you process objects. This achieves interoperability between objects and files.

The table below describes the ways to use PFS in detail.

.. note::

   Access permissions for OBS also apply to PFS. Before using PFS, make sure that you have the permissions required to access OBS resources.

.. table:: **Table 1** Ways to use PFS

   +-------------+-----------------------------------------------------------------------+-------------------------------------------------------------+
   | Way         | Function                                                              | Reference                                                   |
   +=============+=======================================================================+=============================================================+
   | PFS Console | On the console, you can create parallel file systems and manage them. | :ref:`Creating a Parallel File System <obs_13_0002>`        |
   +-------------+-----------------------------------------------------------------------+-------------------------------------------------------------+
   | OBS API     | You can make API calls to use parallel file systems.                  | :ref:`Compatibility Between OBS APIs and PFS <obs_13_0004>` |
   +-------------+-----------------------------------------------------------------------+-------------------------------------------------------------+
