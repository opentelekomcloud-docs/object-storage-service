:original_name: obs_03_0002.html

.. _obs_03_0002:

Cross-Region Replication Overview
=================================

OBS offers disaster recovery across regions, catering to your needs for remote backup.

Cross-region replication refers to the process of automatically and asynchronously replicating data from a source bucket in one region to a destination bucket in another region based on the created replication rule. Source and destination buckets must belong to the same account. Replication across accounts is currently not supported.

You can configure a rule to replicate only objects with a specified prefix or replicate all objects in a bucket. Replicated objects in the destination bucket are copies of those in the source bucket. Objects in both buckets have the same name and metadata (including the content, size, last modification time, creator, version ID, custom metadata, and ACL). By default, the storage class of the replicated object is the same as that of the source object. You can also specify a storage class for the replicated object.


.. figure:: /_static/images/en-us_image_0136493204.png
   :alt: **Figure 1** Cross-region replication

   **Figure 1** Cross-region replication

Contents Replicated
-------------------

After the cross-region replication rule is enabled, objects that meet the following conditions are copied to the destination bucket:

-  Newly uploaded objects (excluding objects in the Cold storage class)
-  Updated objects, for example, objects whose content or ACL information is updated
-  Historical objects in a bucket (The function of synchronizing existing objects must be enabled.)

Application Scenarios
---------------------

-  The same OBS resources need to be accessed in different locations. To minimize the access latency, you can use cross-region replication to create object copies in the nearest region.
-  Due to business reasons, you need to migrate OBS data to the data center in another region.
-  To ensure data security and availability, you need to create explicit backups for all data written to OBS in the data center of another region. Therefore, secure backup data is available if the source data is damaged irrevocably.

Constraints
-----------

Cross-region replication has the following constraints:

-  Currently, only buckets of version 3.0 support cross-region replication. To check the bucket version, go to the **Overview** page of the bucket on OBS Console. Then you can view the bucket version in the **Basic Information** area.

-  The source bucket and the destination bucket must belong to different regions separately. Data cannot be copied between buckets in the same region.

-  Objects of the Cold storage class in the source bucket cannot be copied to the destination bucket through the cross-region replication function.

-  If the region where the destination bucket resides does not support the storage classes, object copies will be stored in the standard storage class.

-  The versioning status of the source and destination buckets must keep the same.

-  Objects in a source bucket can be copied to only one destination bucket, and cannot be copied again from the destination bucket to another bucket. For example, bucket A and bucket B are in two different regions. You can copy data from bucket A to bucket B or the other way round. However, data copies in either bucket A or bucket B cannot be replicated anymore.

-  Object deletion actions made on the source bucket are usually not synchronized to the destination bucket when synchronous deletion of objects is disabled. The object deletion synchronization will happen only when both the source and destination buckets have versioning enabled and you delete an object from the source bucket without specifying a version.

   When synchronous deletion of objects is enabled, object deletion actions made on the source bucket will be synchronized to the destination bucket. Deleting an object from the source bucket also deletes the object from the destination bucket.

-  For an enabled cross-region replication rule, if you change the versioning status of the destination bucket, the replication of objects will fail. If you want to change the versioning status of the source bucket, delete the replication configuration first, and then make the change.

-  Ensure that owners of the source and destination buckets have the read and write permissions to the two buckets. Otherwise, data cannot be synchronized. If the system does not have the permissions to read the source bucket or write the destination bucket due to read/write permission errors, objects cannot be copied successfully, and such replication will not be resumed even if the permission error is rectified.

-  For a source bucket, you can create only one cross-region replication rule that applies to the whole bucket for replication of all objects in the bucket. However, you can create a maximum of 100 cross-region replication rules based on object prefixes for the replication of objects that match the prefixes.

-  OBS currently only supports the replication between one source bucket and one destination bucket. Replication from one source bucket to multiple destination buckets is not supported. The destination bucket can be modified. However, modifying the destination bucket will change the destination bucket of all existing rules.

-  If you delete the OBS agency for an enabled cross-region replication rule, the object replication will be in the **FAILED** status.

-  Do not delete, overwrite object replicas in the destination bucket, or modify their ACLs, which may cause inconsistency of latest object versions or permission control settings between the destination bucket and the source bucket.

-  After a replication with **Synchronize Existing Objects** enabled is complete, if the replication policy keeps unchanged, any ACL changes of source objects will be synchronized to object copies. However, ACL changes of source historical objects will not be synchronized to the copies of historical objects.
