:original_name: obs_11_0023.html

.. _obs_11_0023:

Updating a Configuration File
=============================

Function
--------

You can update items in the **.obsutilconfig** file, including the endpoint, AK, SK, and token.

:ref:`Configuration Parameters <obs_11_0035>` describes parameters in the **.obsutilconfig** file.

Command Line Structure
----------------------

-  In Windows

   .. code-block::

      obsutil config -interactive [-crr] [-config=xxx]

-  In Linux or macOS

   .. code-block::

      ./obsutil config -interactive [-crr] [-config=xxx]

Examples
--------

-  Take Windows as an example. Run the **obsutil config -interactive** command to update the access keys and OBS endpoint in the default configuration file.

   .. code-block::

      obsutil config -interactive

      Please input your ak:
      xxxxxxxxxxxxxxxxxxxxxxxxx
      Please input your sk:
      xxxxxxxxxxxxxxxxxxxxxxxxx
      Please input your endpoint:
      xxxxxxxxxxxxxxxxxxxxxxxxx
      Please input your token:
      xxxxxxxxxxxxxxxxxxxxxxxxx
      Config file url:
        C:\Users\tools\.obsutilconfig

      Update config file successfully!

-  Take Linux as an example. Run the **./obsutil config -interactive** command to update the access keys and OBS endpoint in the default configuration file.

   .. code-block::

      ./obsutil config -interactive

      Please input your ak:
      xxxxxxxxxxxxxxxxxxxxxxxxx
      Please input your sk:
      xxxxxxxxxxxxxxxxxxxxxxxxx
      Please input your endpoint:
      xxxxxxxxxxxxxxxxxxxxxxxxx
      Please input your token:
      xxxxxxxxxxxxxxxxxxxxxxxxx
      Config file url:
        /root/.obsutilconfig

      Update config file successfully!

Parameter Description
---------------------

+-----------------------+---------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter             | Optional or Mandatory           | Description                                                                                                                                                                         |
+=======================+=================================+=====================================================================================================================================================================================+
| interactive           | Optional (additional parameter) | Updates settings in interactive mode.                                                                                                                                               |
+-----------------------+---------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| crr                   | Optional (additional parameter) | Updates the settings of client-side cross-region replication.                                                                                                                       |
|                       |                                 |                                                                                                                                                                                     |
|                       |                                 | .. note::                                                                                                                                                                           |
|                       |                                 |                                                                                                                                                                                     |
|                       |                                 |    If this parameter is not specified, **endpoint**, **ak**, **sk**, and **token** will be updated.                                                                                 |
|                       |                                 |                                                                                                                                                                                     |
|                       |                                 |    If this parameter is specified, **endpointCrr**, **akCrr**, **skCrr**, and **tokenCrr** will be updated.                                                                         |
+-----------------------+---------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| config                | Optional (additional parameter) | The user-defined configuration file for executing the current command. For details about parameters that can be configured, see :ref:`Configuration Parameters <obs_11_0035>`.      |
|                       |                                 |                                                                                                                                                                                     |
|                       |                                 | By specifying this parameter and a path, you can update parameters in the user-defined configuration file. Otherwise, parameters in the default configuration file will be updated. |
+-----------------------+---------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
