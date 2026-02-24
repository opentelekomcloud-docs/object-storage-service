:original_name: obs_11_0011.html

.. _obs_11_0011:

Deleting a Bucket
=================

Function
--------

You can use this command to delete a bucket. The bucket to be deleted must be empty (containing no objects, historical versions, or fragments).

.. note::

   To delete a non-empty bucket, run the commands in :ref:`Deleting a Multipart Upload Task <obs_11_0020>` and :ref:`Deleting an Object <obs_11_0021>` to clear the bucket, and then run the following command to delete the bucket.

Command Line Structure
----------------------

-  In Windows

   .. code-block::

      obsutil rm obs://bucket [-f] [-config=xxx]

-  In Linux or macOS

   .. code-block::

      ./obsutil rm obs://bucket [-f] [-config=xxx]

Examples
--------

-  Take the Windows OS as an example. Run the **obsutil rm obs://bucket-test** command to delete bucket **bucket-test**.

   .. code-block::

      obsutil rm obs://bucket-test

      Start at 2024-09-30 07:58:33.736622 +0000 UTC

      Do you want to delete bucket [bucket-test] ? Please input (y/n) to confirm:
      y
      Delete bucket [bucket-test] successfully!

Parameter Description
---------------------

+-----------+---------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter | Optional or Mandatory           | Description                                                                                                                                                                    |
+===========+=================================+================================================================================================================================================================================+
| bucket    | Mandatory                       | The bucket name                                                                                                                                                                |
+-----------+---------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| f         | Optional (additional parameter) | Runs in force mode.                                                                                                                                                            |
+-----------+---------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| config    | Optional (additional parameter) | The user-defined configuration file for executing the current command. For details about parameters that can be configured, see :ref:`Configuration Parameters <obs_11_0035>`. |
+-----------+---------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| payer     | Optional (additional parameter) | Specifies that requester pays is enabled.                                                                                                                                      |
+-----------+---------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
