:original_name: obs_11_0063.html

.. _obs_11_0063:

Listing Objects by Using an Authorization Code
==============================================

Function
--------

You can use this command to query objects in a bucket with an authorization code. The returned objects are sorted in lexicographical order.

Command Line Structure
----------------------

-  In Windows

   -  Enter an authorization code directly.

      .. code-block::

         obsutil share-ls authorization_code [-ac=xxx] [-prefix=xxx] [-s] [-d] [-marker=xxx] [-bf=xxx] [-limit=1]  [-config=xxx]

   -  Use the file path to pass an authorization code.

      .. code-block::

         obsutil share-ls file://authorization_code_file_url [-ac=xxx] [-prefix=xxx] [-s] [-d] [-marker=xxx] [-bf=xxx] [-limit=1]  [-config=xxx]

-  In Linux or macOS

   -  Enter an authorization code directly.

      .. code-block::

         ./obsutil share-ls authorization_code [-ac=xxx] [-prefix=xxx] [-s] [-d] [-marker=xxx] [-bf=xxx] [-limit=1] [-config=xxx]

   -  Use the file path to pass an authorization code.

      .. code-block::

         ./obsutil share-ls file://authorization_code_file_url [-ac=xxx] [-prefix=xxx] [-s] [-d] [-marker=xxx] [-bf=xxx] [-limit=1] [-config=xxx]

Examples
--------

-  In Windows, you can run the **obsutil share-ls xxx -ac=123456 -limit=1** command to query objects in a bucket using an authorization code.

   .. code-block::

      obsutil share-ls xxx -ac=123456 -limit=1
      The authorized prefix is [test/test.tar.gz]
      Listing objects .
      Object list:
      key                                             LastModified                  Size      StorageClass        ETag
      obs://bucket-test/test/test.tar.gz              2019-07-11T14:50:59Z          48.92KB   standard    "1dd27294ad2f152b43cd111e9fe3990f"

      Total size of prefix [test/]: 48.92KB
      Folder number: 0
      File number: 1
      The authorized prefix is [test/]

-  In Windows, you can run the **obsutil share-ls xxx -ac=123456 -limit=1** command to query directories in a bucket using an authorization code.

   .. code-block::

      obsutil share-ls xxx -ac=123456 -limit=1

      The authorized prefix is [test]

      Listing objects .

      Folder list:
      obs://bucket-test/test/

      Object list:
      key                                             LastModified                  Size      StorageClass        ETag
      obs://bucket-test/test/test.tar.gz              2019-07-11T14:50:59Z          48.92KB   standard    "1dd27294ad2f152b43cd111e9fe3990f"

      Total size of prefix [test/]: 48.92KB
      Folder number: 1
      File number: 1
      The authorized prefix is [test/]

Parameter Description
---------------------

+------------------------------------+---------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter                          | Optional or Mandatory           | Description                                                                                                                                                                                                                                                                                        |
+====================================+=================================+====================================================================================================================================================================================================================================================================================================+
| authorization_code                 | Mandatory                       | The code for authorization                                                                                                                                                                                                                                                                         |
|                                    |                                 |                                                                                                                                                                                                                                                                                                    |
| or                                 |                                 | .. note::                                                                                                                                                                                                                                                                                          |
|                                    |                                 |                                                                                                                                                                                                                                                                                                    |
| file://authorization_code_file_url |                                 |    If the authorization code starts with **file://**, the authorization code is obtained from a local file.                                                                                                                                                                                        |
+------------------------------------+---------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| ac                                 | Optional (additional parameter) | The access code                                                                                                                                                                                                                                                                                    |
|                                    |                                 |                                                                                                                                                                                                                                                                                                    |
|                                    |                                 | .. note::                                                                                                                                                                                                                                                                                          |
|                                    |                                 |                                                                                                                                                                                                                                                                                                    |
|                                    |                                 |    -  If no access code is specified using this parameter, obsutil tool prompts you to enter the access code in interactive mode.                                                                                                                                                                  |
|                                    |                                 |    -  An access code is a six-digit string.                                                                                                                                                                                                                                                        |
+------------------------------------+---------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| prefix                             | Optional (additional parameter) | The object name prefix specified for listing objects using an authorization code                                                                                                                                                                                                                   |
|                                    |                                 |                                                                                                                                                                                                                                                                                                    |
|                                    |                                 | .. note::                                                                                                                                                                                                                                                                                          |
|                                    |                                 |                                                                                                                                                                                                                                                                                                    |
|                                    |                                 |    -  If this parameter is specified, objects starting with this prefix are listed.                                                                                                                                                                                                                |
|                                    |                                 |    -  If this parameter is left blank, all objects in the authorized path are shared.                                                                                                                                                                                                              |
+------------------------------------+---------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| s                                  | Optional (additional parameter) | Displays simplified query result.                                                                                                                                                                                                                                                                  |
|                                    |                                 |                                                                                                                                                                                                                                                                                                    |
|                                    |                                 | .. note::                                                                                                                                                                                                                                                                                          |
|                                    |                                 |                                                                                                                                                                                                                                                                                                    |
|                                    |                                 |    In the simplified format, the returned result contains only the object name.                                                                                                                                                                                                                    |
+------------------------------------+---------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| d                                  | Optional (additional parameter) | Lists only objects and subdirectories in the current directory, instead of recursively listing all objects and subdirectories.                                                                                                                                                                     |
|                                    |                                 |                                                                                                                                                                                                                                                                                                    |
|                                    |                                 | .. note::                                                                                                                                                                                                                                                                                          |
|                                    |                                 |                                                                                                                                                                                                                                                                                                    |
|                                    |                                 |    According to the naming conventions in OBS, a slash (/) is used as the directory separator.                                                                                                                                                                                                     |
+------------------------------------+---------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| marker                             | Optional (additional parameter) | The start position for listing objects in a bucket using an authorization code. The objects following this start position are sorted in lexicographical order by object name.                                                                                                                      |
+------------------------------------+---------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| bf                                 | Optional (additional parameter) | The display formats of bytes in the listing result. Possible values are:                                                                                                                                                                                                                           |
|                                    |                                 |                                                                                                                                                                                                                                                                                                    |
|                                    |                                 | -  human-readable                                                                                                                                                                                                                                                                                  |
|                                    |                                 | -  raw                                                                                                                                                                                                                                                                                             |
|                                    |                                 |                                                                                                                                                                                                                                                                                                    |
|                                    |                                 | .. note::                                                                                                                                                                                                                                                                                          |
|                                    |                                 |                                                                                                                                                                                                                                                                                                    |
|                                    |                                 |    If this parameter is not configured, the display format of bytes in the result is determined by the **humanReadableFormat** parameter in the configuration file.                                                                                                                                |
+------------------------------------+---------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| limit                              | Optional (additional parameter) | The maximum number of objects that can be listed. If the value is less than or equal to 0, all objects are listed. If it is left blank, 1000 objects are listed by default.                                                                                                                        |
|                                    |                                 |                                                                                                                                                                                                                                                                                                    |
|                                    |                                 | .. note::                                                                                                                                                                                                                                                                                          |
|                                    |                                 |                                                                                                                                                                                                                                                                                                    |
|                                    |                                 |    If there are a large number of objects in a bucket, you are advised to set this parameter to limit the number of objects to be listed each time. If not all objects are listed, **marker** of the next request will be returned in the result, which you can use to list the remaining objects. |
+------------------------------------+---------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| config                             | Optional (additional parameter) | The user-defined configuration file for executing the current command. For details about parameters that can be configured, see :ref:`Configuration Parameters <obs_11_0035>`.                                                                                                                     |
+------------------------------------+---------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
