:original_name: obs_11_0003.html

.. _obs_11_0003:

Downloading and Installing obsutil
==================================

Download Links
--------------

:ref:`Table 1 <obs_11_0003__table57021618505>` lists the download links of obsutil for different OSs.

.. _obs_11_0003__table57021618505:

.. table:: **Table 1** Download links of obsutil

   +--------------------+-------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | OS                 | Software Package                                                                                            | Manual Verification Signature File                                                               | Automatic Verification Signature File                                                            |
   +====================+=============================================================================================================+==================================================================================================+==================================================================================================+
   | Windows (64-bit)   | `obsutil_windows64 <https://obsutil.obs.eu-de.otc.t-systems.com/obsutil_hcso_windows_amd64_5.7.9.zip>`__    | `pgp <https://obsutil.obs.eu-de.otc.t-systems.com/obsutil_hcso_windows_amd64_5.7.9.zip.asc>`__   | `cms <https://obsutil.obs.eu-de.otc.t-systems.com/obsutil_hcso_windows_amd64_5.7.9.zip.p7s>`__   |
   +--------------------+-------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | Linux AMD (64-bit) | `obsutil_linux_amd64 <https://obsutil.obs.eu-de.otc.t-systems.com/obsutil_hcso_linux_amd64_5.7.9.tar.gz>`__ | `pgp <https://obsutil.obs.eu-de.otc.t-systems.com/obsutil_hcso_linux_amd64_5.7.9.tar.gz.asc>`__  | `cms <https://obsutil.obs.eu-de.otc.t-systems.com/obsutil_hcso_linux_amd64_5.7.9.tar.gz.p7s>`__  |
   +--------------------+-------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | Linux Arm (64-bit) | `obsutil_linux_arm64 <https://obsutil.obs.eu-de.otc.t-systems.com/obsutil_hcso_linux_arm64_5.7.9.tar.gz>`__ | `pgp <https://obsutil.obs.eu-de.otc.t-systems.com/obsutil_hcso_linux_arm64_5.7.9.tar.gz.asc>`__  | `cms <https://obsutil.obs.eu-de.otc.t-systems.com/obsutil_hcso_linux_arm64_5.7.9.tar.gz.p7s>`__  |
   +--------------------+-------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | macOS (64-bit)     | `obsutil_mac64 <https://obsutil.obs.eu-de.otc.t-systems.com/obsutil_hcso_darwin_amd64_5.7.9.tar.gz>`__      | `pgp <https://obsutil.obs.eu-de.otc.t-systems.com/obsutil_hcso_darwin_amd64_5.7.9.tar.gz.asc>`__ | `cms <https://obsutil.obs.eu-de.otc.t-systems.com/obsutil_hcso_darwin_amd64_5.7.9.tar.gz.p7s>`__ |
   +--------------------+-------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+

Getting Started with obsutil
----------------------------

You can download obsutil and then use it without installation. Methods of downloading obsutil vary depending on the OS type.

.. note::

   Make sure that your cloud server has been connected to the Internet, or the obsutil installation will fail.

**Windows**

#. Click the link provided on OBS Console to download the obsutil package to your local PC.
#. Decompress the software package.
#. Use Command Prompt to go to the decompressed folder and run obsutil commands.

**Linux**

#. Open the CLI and run the **wget** command for the download link provided on OBS Console to download obsutil to your local PC.

   Linux AMD (64-bit) and Linux x86 (64-bit):

   .. note::

      -  The URL after **wget** is the download link of the installation package, for which you do not need to make any adaptations. To download the package, just copy and run the whole **wget** command.
      -  You can also download the obsutil package from a PC running Windows and then use a cross-platform transfer tool (such as WinSCP) to transfer the package to your Linux host.

#. Run the following command in the directory where the obsutil package resides:

   .. code-block::

      tar -xzvf obsutil_linux_amd64.tar.gz

#. List the obsutil directory. **x.x.x** indicates the obsutil version.

   .. code-block::

      ll

      dr-x------ 2 root root    4096 Jan  5  2024 obsutil_linux_amd64_x.x.x
      -rw------- 1 root root 3845484 Mar 27 17:05 obsutil_linux_amd64.tar.gz

#. Go to the directory where obsutil resides. **x.x.x** indicates the obsutil version.

   .. code-block::

      cd obsutil_linux_amd64_x.x.x

#. Run the following command to grant the execute permissions for obsutil:

   .. code-block::

      chmod 755 obsutil

   .. note::

      This step is required, or error "No such file or directory" will be reported when you are querying the obsutil version number.

#. Continue to run the following command in the directory. If the version number of obsutil is returned, the installation is successful.

   .. code-block::

      ./obsutil version

      obsutil version:5.7.9, obssdk version:3.24.12
      operating system:linux, arch:amd64

**macOS**

#. Click the link provided on OBS Console to download the obsutil package to your local PC.

#. Decompress the software package.

#. Open the CLI, go to the directory where obsutil belongs, and run the following command to add execute permissions to obsutil:

   .. code-block::

      chmod 755 obsutil

References
----------

-  :ref:`Quick Start <obs_11_0006>`
-  :ref:`Using the obsutil help Command to Search for Functions <obs_11_0066>`
