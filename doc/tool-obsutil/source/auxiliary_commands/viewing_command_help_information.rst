:original_name: obs_11_0025.html

.. _obs_11_0025:

Viewing Command Help Information
================================

Function
--------

You can use this command to view the commands supported by obsutil or view the help information of a specific command.

Command Line Structure
----------------------

-  In Windows

   .. code-block::

      obsutil help [command]

-  In Linux or macOS

   .. code-block::

      ./obsutil help [command]

Examples
--------

-  Take the Windows OS as an example. Run the **obsutil help mb** command to view the help information about the command for creating a bucket.

   .. code-block::

      obsutil help mb

      Summary:
        create a bucket with the specified parameters

      Syntax:
        obsutil mb obs://bucket [-acl=xxx] [-location=xxx] [-fs] [-az=xxx] [-sc=xxx] [-config=xxx] [-i=xxx] [-k=xxx] [-t=xxx] [-e=xxx]

      Options:
        -fs
          create a bucket that supports POSIX

        -az=xxx
          the AZ of the bucket, possible values are [multi-az]

        -sc=xxx
          the default storage class of the bucket, possible values are [standard|warm|cold|deep-archive]

        -acl=xxx
          the ACL of the bucket, possible values are [private|public-read|public-read-write]

        -location=xxx
          the region where the bucket is located

        -epid=xxx
          the enterprise project id of the bucket

        -kms=xxx
          the encryption id of the bucket

        -config=xxx
          the path to the custom config file when running this command

        -e=xxx
          endpoint

        -i=xxx
          access key ID

        -k=xxx
          security key ID

        -t=xxx
          security token

      Summary:
      create a bucket with the specified parameters

      Syntax:
        obsutil mb obs://bucket [-fs] [-acl=xxx] [-sc=xxx] [-location=xxx] [-config=xxx]

      Options:
        -fs
          create a bucket that supports POSIX

        -acl=xxx
          the ACL of the bucket, possible values are [private|public-read|public-read-write]

        -sc=xxx
          the default storage class of the bucket, possible values are: [standard|warm|cold]

        -location=xxx
          the region where the bucket is located

        -config=xxx
          the path to the custom config file when running this command

Parameter Description
---------------------

+-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter             | Optional or Mandatory | Description                                                                                                                                                                                                                    |
+=======================+=======================+================================================================================================================================================================================================================================+
| command               | Optional              | Currently, the help documents of the following commands are available:                                                                                                                                                         |
|                       |                       |                                                                                                                                                                                                                                |
|                       |                       | -  For **abort**, see :ref:`Deleting a Multipart Upload Task <obs_11_0020>`.                                                                                                                                                   |
|                       |                       | -  For **chattri**, see :ref:`Setting Object Properties <obs_11_0041>`.                                                                                                                                                        |
|                       |                       | -  For **cp**, see :ref:`Uploading an Object <obs_11_0013>`, :ref:`Copying an Object <obs_11_0017>`, and :ref:`Downloading an Object <obs_11_0018>`.                                                                           |
|                       |                       | -  For **ls**, see :ref:`Listing Buckets <obs_11_0009>`, :ref:`Listing Objects <obs_11_0014>`, and :ref:`Listing Multipart Upload Tasks <obs_11_0019>`.                                                                        |
|                       |                       | -  For **mb**, see :ref:`Creating a Bucket <obs_11_0008>`.                                                                                                                                                                     |
|                       |                       | -  For **mkdir**, see :ref:`Creating a Folder <obs_11_0050>`.                                                                                                                                                                  |
|                       |                       | -  For **mv**, see :ref:`Moving an Object <obs_11_0053>`.                                                                                                                                                                      |
|                       |                       | -  For **restore**, see :ref:`Restoring Objects from the Cold Storage <obs_11_0016>`.                                                                                                                                          |
|                       |                       | -  For **rm**, see :ref:`Deleting a Bucket <obs_11_0011>` and :ref:`Deleting an Object <obs_11_0021>`.                                                                                                                         |
|                       |                       | -  For **sign**, see :ref:`Generating the Download Link of an Object <obs_11_0051>`.                                                                                                                                           |
|                       |                       | -  For **stat**, see :ref:`Querying Bucket Properties <obs_11_0010>` and :ref:`Querying Object Properties <obs_11_0015>`.                                                                                                      |
|                       |                       | -  For **sync**, see :ref:`Synchronously Uploading Incremental Objects <obs_11_0042>`, :ref:`Synchronously Copying Incremental Objects <obs_11_0044>`, and :ref:`Synchronously Downloading Incremental Objects <obs_11_0043>`. |
|                       |                       | -  For **archive**, see :ref:`Archiving Log Files <obs_11_0045>`.                                                                                                                                                              |
|                       |                       | -  For **clear**, see :ref:`Deleting Part Records <obs_11_0024>`.                                                                                                                                                              |
|                       |                       | -  For **config**, see :ref:`Updating a Configuration File <obs_11_0023>`.                                                                                                                                                     |
|                       |                       | -  For **help**, see :ref:`Viewing Command Help Information <obs_11_0025>`.                                                                                                                                                    |
|                       |                       | -  For **version**, see :ref:`Querying the Version Number <obs_11_0026>`.                                                                                                                                                      |
+-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
