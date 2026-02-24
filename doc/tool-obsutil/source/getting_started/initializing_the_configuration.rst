:original_name: obs_11_0005.html

.. _obs_11_0005:

Initializing the Configuration
==============================

Before using obsutil, you need to configure the OBS endpoint and AK/SK for obsutil to interconnect with OBS. Then, you can use obsutil to operate OBS buckets and objects.

Prerequisites
-------------

-  You have obtained the enabled `regions and endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__ of OBS.
-  You have obtained the AK/SK. For details, see :ref:`Creating Access Keys (AK and SK) <obs_11_0061>`.

obsutil Initialization Methods
------------------------------

Run the **config** command (for more information about **config**, see :ref:`Updating a Configuration File <obs_11_0023>`):

-  In Windows

   Using a permanent AK/SK pair:

   .. code-block::

      obsutil config -i=xxxxx -k=xxxxx -e=xxxxx

   Using a temporary AK/SK pair and a security token:

   .. code-block::

      obsutil config -i=xxxxx -k=xxxxx -t=xxxxx -e=xxxxx

-  In Linux or macOS

   Using a permanent AK/SK pair:

   .. code-block::

      ./obsutil config -i=xxxxx -k=xxxx -e=xxxxx

   Using a temporary AK/SK pair and a security token:

   .. code-block::

      ./obsutil config -i=xxxxx -k=xxxxx -t=xxxxx -e=xxxxx

   .. table:: **Table 1** Parameter description

      +-----------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter | Optional or Mandatory | Description                                                                                                                                                                                                                                                    |
      +===========+=======================+================================================================================================================================================================================================================================================================+
      | i         | Mandatory             | AK in permanent or temporary security credentials                                                                                                                                                                                                              |
      +-----------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | k         | Mandatory             | SK in permanent or temporary security credentials                                                                                                                                                                                                              |
      +-----------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | e         | Mandatory             | Endpoint for accessing OBS, which can contain the protocol type, domain name, and port number (optional), for example, **https://**\ *your-endpoint*\ **:443**. (For security purposes, you are advised to use HTTPS. The port number **443** can be omitted.) |
      +-----------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | t         | Optional              | Security token in the temporary security credentials. It is mandatory when temporary security credentials are used.                                                                                                                                            |
      +-----------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. note::

   -  After the command is executed, there will be the **.obsutilconfig** file created in the directory (**~** in Linux or macOS or **C:\\Users\\<**\ *username*\ **>** in Windows) where obsutil commands run. This file contains all the configuration information of obsutil.
   -  For details about the parameters in the **.obsutilconfig** file, see :ref:`Configuration Parameters <obs_11_0035>`.
   -  The **.obsutilconfig** file contains the AK/SK information, so it is hidden by default to prevent leakage. To query this file, run the following command in the directory where obsutil commands run.

      -  In Windows

         .. code-block::

            dir

      -  In Linux or macOS

         .. code-block::

            ls -a

         or

         .. code-block::

            ls -al

   -  obsutil encrypts the AK/SK information in the **.obsutilconfig** file.

Method 3: Initialize obsutil in interactive mode.

-  In Windows

   Using a permanent AK/SK pair (you do not need to enter a token, and press **Enter** to skip it):

   .. code-block::

      obsutil config -interactive

      Please input your ak:
      xxxxxxxxxxxxxxxxxxxxxxxxx
      Please input your sk:
      xxxxxxxxxxxxxxxxxxxxxxxxx
      Please input your endpoint:
      xxxxxxxxxxxxxxxxxxxxxxxxx
      Please input your token:

      Config file url:
        C:\Users\tools\.obsutilconfig

      Update config file successfully!

   Using a temporary AK/SK pair and a security token:

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

-  In Linux or macOS

   Using a permanent AK/SK pair (you do not need to enter a token, and press **Enter** to skip it):

   .. code-block::

      ./obsutil config -interactive

      Please input your ak:
      xxxxxxxxxxxxxxxxxxxxxxxxx
      Please input your sk:
      xxxxxxxxxxxxxxxxxxxxxxxxx
      Please input your endpoint:
      xxxxxxxxxxxxxxxxxxxxxxxxx
      Please input your token:

      Config file url:
        /root/.obsutilconfig

      Update config file successfully!

   Using a temporary AK/SK pair and a security token:

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

Checking the Connectivity
-------------------------

After the initial configuration is complete, run the following command to check the connectivity:

-  In Windows

   .. code-block::

      obsutil ls -s

-  In Linux or macOS

   .. code-block::

      ./obsutil ls -s

Check the command output:

-  If it contains "Bucket number", the configuration is correct.
-  If it contains "Http status [403]", the access keys are wrong.
-  If it contains "A connection attempt failed", OBS cannot be connected. Then, check the network condition.
-  If it contains "Error: cloud_url [url] is not in well format", the domain name to be accessed is incorrect. Check the domain name in the configuration file.

.. note::

   If the command output contains "Http status [403]", you may not have the required permissions for obtaining the bucket list. A further analysis is required to identify the root cause.
