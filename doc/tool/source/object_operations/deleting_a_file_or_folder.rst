:original_name: obs_03_1066.html

.. _obs_03_1066:

Deleting a File or Folder
=========================

Delete an existing file or folder as needed.

Context
-------

Deleting a folder will also delete all files in it. Ensure that all files in a folder can be deleted before deleting the folder.

Deleting unwanted files or folders saves space and costs.

You can use lifecycle management to periodically delete some unwanted files or batch delete all files or folders in OBS.

Procedure
---------

#. Log in to OBS Browser+.

#. Go to the target bucket. Select the file or folder you want to delete and click **Delete**.

   You can hold down **Ctrl** or **Shift** to select multiple files or folders and batch delete them. You can also press **Ctrl+A** to select all the files or folders. The operations are consistent with those in Windows operating systems.

#. In the displayed dialog box, click **OK**.

Important Notes
---------------

In big data scenarios, parallel file systems usually have deep directory levels and each directory has a large number of files. In such case, deleting directories from parallel file systems may fail due to timeout. To address this problem, you are advised to delete directories in either of the following ways:

#. On the Hadoop client that has OBSA, an OBS client plugin, embedded, run the **hadoop fs - rmr obs://{**\ *Name of a parallel file system*\ **}/{**\ *Directory name*\ **}** command.
#. Configure a lifecycle rule for directories so that they can be deleted in background based on the preset lifecycle rule.
