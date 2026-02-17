:original_name: obs_11_0039.html

.. _obs_11_0039:

Using obsutil to Replicate Data Across Regions on the Client Side
=================================================================

obsutil client supports cross-region replication. You can directly replicate data from a source bucket to the destination bucket through data streams. The source bucket and destination bucket can be any two OBS buckets. Objects can be replicated between buckets in different regions under the same account or across accounts. The following procedure describes how to replicate data between buckets across accounts and regions:

#. Run the **obsutil config** command to configure the AK, SK, and endpoint of the source bucket account.

   -  In Windows

      .. code-block::

         obsutil config -interactive -crr

   -  In Linux

      .. code-block::

         ./obsutil config -interactive -crr

#. Run the **obsutil config** command to configure the AK, SK, and endpoint of the destination bucket account.

   -  In Windows

      .. code-block::

         obsutil config -interactive

   -  In Linux

      .. code-block::

         ./obsutil config -interactive

#. Check the connectivity to ensure that the destination bucket is correctly configured.

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

#. Run the **cp** command to specify that cross-region replication method is used to copy objects from the source bucket to the destination bucket.

   -  In Windows

      .. code-block::

         obsutil cp obs://src-bucket obs://dst-bucket -f -r -crr

   -  In Linux

      .. code-block::

         ./obsutil cp obs://src-bucket obs://dst-bucket -f -r -crr

.. note::

   -  To use the cross-region replication function, you need to specify the **-crr** parameter. If this parameter is specified, update the configuration of the client-side cross-region replication in the configuration file. For details, see :ref:`Updating a Configuration File <obs_11_0023>`.
   -  The configurations of the source bucket and destination bucket are respectively **akCrr/skCrr/tokenCrr/endpointCrr** and **ak/sk/token/endpoint** in the configuration file.
   -  The preceding procedure is also applicable to the situation when the source and destination buckets belong to the same account.

.. caution::

   When the **-crr** parameter is used, the source object's standard metadata, including **Cache-Control**, **Expires**, **Content-Encoding**, **Content-Disposition**, **Content-Type**, and **Content-Language**, will not be copied.

   When the **-crr** parameter is used for cross-region replication, the ACL of the source object will not be copied. You can use **[-acl=**\ *xxx*\ **]** to specify the ACL for the target object. If the ACL is not specified, the object inherits the ACL of the bucket by default.
