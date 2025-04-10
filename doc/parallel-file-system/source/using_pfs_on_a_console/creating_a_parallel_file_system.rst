:original_name: obs_13_0002.html

.. _obs_13_0002:

Creating a Parallel File System
===============================

You can create a parallel file system on OBS Console.

Procedure
---------

#. On the console homepage, click **Service List** in the upper left corner and choose **Storage** > **Object Storage Service**.

#. In the navigation pane, choose **Parallel File Systems**.

#. In the upper right corner of the page, click **Create Parallel File System**.

#. Select a region and enter a name for the parallel file system.

   .. note::

      -  Once a parallel file system is created, its name cannot be changed.
      -  URLs do not support uppercase letters and cannot distinguish between names containing uppercase or lowercase letters. For example, if you attempt to access the parallel file system **MyFileSystem** using a URL, the file system name will be resolved to **myfilesystem**, causing an access error. For this reason, a parallel file system name can contain only lowercase letters, digits, periods (.), and hyphens (-).

#. Configure a policy. You can select **Private**, **Public Read**, or **Public Read/Write** for the parallel file system.

#. (Optional) Add tags. Tags are used to identify parallel file systems in OBS, for the purpose of classification. Each tag is represented by one key-value pair. For details about how to add a tag, see the "Tags" section in the *Object Storage Service User Guide*.

#. Confirm the settings at the bottom of the page and click **Create Now**.

#. View the file system you created just now in the parallel file system list.

   Then, you can use the parallel file system the same way you use a bucket. For details, see :ref:`Using PFS <obs_13_0010>`.
