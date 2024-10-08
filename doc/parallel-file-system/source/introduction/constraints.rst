:original_name: obs_13_0009.html

.. _obs_13_0009:

Constraints
===========

**Operations**

-  An existing OBS bucket cannot be changed to a parallel file system. For details about how to create a parallel file system, see :ref:`Creating a Parallel File System <obs_13_0002>`.
-  Parallel file systems do not support quota configuration. By default, there is no quota limit.

**Functions**

-  Image processing currently cannot be used to process (such as downsize, resize, or watermark) images stored in parallel file systems.
-  Server-side encryption is not supported.
-  Cross-region replication is not supported.
-  Versioning is not supported.
-  Bucket inventory is not supported.
-  Static website hosting is not supported.
-  Changing file storage class is not supported.
-  Configuration of default storage class for a parallel file system is not supported.

**Naming**

-  In a parallel file system, a file name cannot contain two consecutive slashes (//). For example, if you name a file as **test//123.txt**, an error will be reported.
