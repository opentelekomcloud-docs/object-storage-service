:original_name: obs_11_0066.html

.. _obs_11_0066:

Using the obsutil help Command to Search for Functions
======================================================

obsutil provides **help** commands for viewing the help documents of each command. To query the help document of the bucket creation command, perform the following steps:

#. Run the **obsutil help** command to query the list of all supported commands.

#. Find the abbreviation of the command to be viewed based on the document description in the command list. For example, the abbreviation of the command for creating a bucket is **mb**.

#. Run the **obsutil help mb** command to view the usage and detailed functions of the **mb** command, illustrated as follows:

   .. code-block::

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

#. Run the **obsutil mb obs://bucket-test -location xxx** command to create a bucket named **bucket-test** in the *xxx* region.

.. note::

   -  For more information about the **help** command, see :ref:`Viewing Command Help Information <obs_11_0025>`.
   -  You can set the **helpLanguage** parameter in the configuration file to configure the language type of the **help** command. For example, **helpLanguage=Chinese** indicates that the language type of the help command is Chinese.
   -  The supported languages are Chinese and English. The default language is English.
