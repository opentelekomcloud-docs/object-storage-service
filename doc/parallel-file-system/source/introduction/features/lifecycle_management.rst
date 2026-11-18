:original_name: obs_13_0013.html

.. _obs_13_0013:

Lifecycle Management
====================

The use cases and main functions of object lifecycle management also work on files in parallel file systems. For more information, see `Lifecycle Management <https://docs.otc.t-systems.com/object-storage-service/umn/obs_console_operation_guide/lifecycle_management/index.html>`__.

Differences Between File and Object Lifecycle Management
--------------------------------------------------------

-  A lifecycle rule can be used to manage files, but it cannot transition a directory to the Cold storage class. However, a lifecycle rule can delete an empty directory upon expiration.
-  File deletion upon expiration can be configured using either the API or console, while transition to Warm or Cold storage class can only be configured using the API.
-  If direct reading is enabled for a parallel file system, you can read files stored in the Cold storage class without restoring them first.
-  A maximum of 20 lifecycle rules can be configured for a parallel file system.
-  The time applied for a lifecycle rule to work on a file is when the data of the file was last updated.
-  After a lifecycle rule is configured for a parallel file system, there are limits on how many directories that the rule can be applied to. If the configuration exceeds the limit, the lifecycle rule execution will be prolonged.

   #. There can be no more than 100,000 level-1 subdirectories in each directory.
   #. There can be no more than 10 million subdirectories (folders) matching the prefix defined in the rule in total.
   #. There can be no more than 30 million files matching the prefix defined in the rule in total.

Notes
-----

-  If renamed files or files in a renamed directory meet the conditions specified in a lifecycle rule, the time when the file data was most recently updated, not when the files were renamed, will be applied for the lifecycle rule to take effect. In addition, the effective time of the lifecycle rule may be delayed for up to seven days.

-  For a file copy on a client, the lifecycle rule determines when to expire the file copy or transition it to the Cold storage class based on the file copy creation time.

   -  For example, if a file, **src.txt**, was created on January 1, 2019, and was then copied to the **des.txt** file by running the **cp -a src.txt des.txt** command on September 1, 2019, then the lifecycle rule calculated when to perform the specified actions on the file copy based on September 1, 2019.

-  In the lifecycle rule of a parallel file system, directories in the file system are periodically scanned, and then deleted if they meet the expiration conditions. Scan intervals (usually seven days) vary depending on cluster configurations. A scan starts from the deepest directory, and the scanned empty directories that meet the expiration conditions will be deleted, but those non-empty directories will not be processed. For this mechanism, a single-level directory that meets the expiration conditions will be deleted 0 to 7 days after it has been emptied. Accordingly, a two-level directory will be deleted 0 to 14 days after it has been emptied. Each time a directory level is added, the waiting time for deletion increases by seven days.
