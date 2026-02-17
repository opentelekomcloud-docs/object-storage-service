:original_name: obs_11_0049.html

.. _obs_11_0049:

Setting obsutil Commands as Built-in Commands
=============================================

Scenario
--------

Because obsutil is external software, you need to access the directory where obsutil resides before running obsutil commands, which is not convenient.

An OS provides built-in commands so that the command-dependent directories are loaded to the memory when the system is started. In this way, you can run the commands in any directory, which improves the tool's usability.

This section introduces how to set obsutil commands as built-in commands in different OSs.

Setting obsutil Commands as Built-in Commands in Windows
--------------------------------------------------------

#. In the CLI, run the **echo %PATH%** command to query all the paths configured in the current system. Then select one as the operation path.
#. Run the **mklink** *PATH*\ **/obsutil.exe** *OBSUTIL_PATH* command to set obsutil commands as built-in commands in the system.

   .. note::

      *PATH* indicates the operation path selected in step 1. *OBSUTIL_PATH* indicates the absolute path of **obsutil.exe**.

#. Check whether the configuration is successful: Run the **obsutil help** command in the CLI. If the help information is displayed, the configuration is successful.

Setting obsutil Commands as Built-in Commands in Linux or macOS
---------------------------------------------------------------

#. Run the following command to create a directory for the obsutil tool:

   .. code-block::

      mkdir /obsutil

   .. note::

      -  Skip this step if the directory already exists.
      -  You must run the command as user **root**.

#. Run the following command to grant the **755** permission for the tool's directory:

   .. code-block::

      chmod 755 /obsutil

   .. note::

      -  Skip this step if the permission for the directory is **drwxr-xr-x**.
      -  You must run the command as user **root**.

#. Copy the obsutil tool to the directory created in step 1 and change its permission to **711**. Assume that the original path of the tool is **/home/test/obsutil**. Run the following command:

   .. code-block::

      cp /home/test/obsutil /obsutil
      chmod 711 /obsutil/obsutil

#. Run the **vi /etc/profile** command, type **i** to enter the Insert mode to edit the file. Add **export PATH=$PATH:/obsutil** at the end of the file. Then press **ESC** to exit the editing mode, and then type **:wq!** and press **Enter** to save the file and exit.

   .. note::

      Skip this step if the new line already exists in the **/etc/profile** file.

#. Run the **echo $PATH** command to query the current environment variables. If **:/obsutil** in included in the query result, indicating that the **/obsutil** environment variable already exists, go to the next step. Otherwise, run the **source /etc/profile** command.

#. Check whether the configuration is successful: Run the **obsutil help** command in any directory. If the help information is displayed, the configuration is successful.

FAQs
----

#. How do I locate the obsutil configuration file after setting obsutil commands to built-in commands?

   The **.obsutilconfig** file in the same directory where obsutil commands reside is the configuration file of the obsutil tool. You can also run the **obsutil config** command to obtain the configuration file path. An example is provided as follows:

   .. code-block::

      obsutil config
      Config file url:
        D:\tools\.obsutilconfig

#. How do I delete obsutil commands after setting them as built-in commands?

   -  In Windows:

      a. Run the **where obsutil** command to locate the path of obsutil commands.

         .. code-block::

            where obsutil
            E:\tools\bin\obsutil.exe

      b. Run the **del** *PATH* command to delete obsutil commands.

         .. code-block::

            del E:\tools\bin\obsutil.exe

         .. note::

            Replace *PATH* with the path of obsutil commands. **E:\\tools\\bin\\obsutil.exe** is used in the preceding example.

   -  In Linux or macOS:

      a. Run the **which obsutil** command to locate the path of obsutil commands.

         .. code-block::

            which obsutil
            /obsutil/obsutil

      b. Run the **rm -rf** *PATH* command to delete obsutil commands.

         .. code-block::

            rm -rf /obsutil/obsutil

         .. note::

            Replace *PATH* with the path of obsutil commands. **/obsutil/obsutil** is used in the preceding example.

      c. Restore the system environment variable: Delete the path of obsutil that is set in the **/etc/profile** file.

         .. note::

            If the **/etc/profile** file contains line **export PATH=$PATH:/obsutil**, delete the line. Or if the file contains line **export PATH=$PATH:/test/bin:/obsutil:/test1**, delete **:/obsutil** from the line.

#. What should I do if the execution of built-in obsutil commands fails in Linux or macOS?

   -  If the message **Permission denied** is displayed after executing **obsutil help**, run the **chmod 755** *OBSUTIL_PATH* command (replace *OBSUTIL_PATH* with the path of obsutil) to add an execute permission for the obsutil tool.
   -  If the message **command not found** is displayed, log in again.
   -  If the message **Cannot create parent folder for xx/.obsutilconfig, xx Permission denied** is displayed, check whether the home directory of the user exists.

      .. important::

         In the Ubuntu OS, if you run the **useradd** command to add a user, the home directory of the user is not created by default. You need to create it manually. Therefore, you are advised to run the **adduser** command to add a user.

#. What can I do if no log file is generated after running built-in obsutil commands in Linux or macOS?

   If you have properly configured **sdkLogPath** and **utilLogPath** in the configuration file, but still no log file is generated after command execution, then check whether the user who runs the command has the read and write permissions on **sdkLogPath** and **utilLogPath**.
