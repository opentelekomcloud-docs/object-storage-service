:original_name: obs_03_1051.html

.. _obs_03_1051:

Overview
========

Lifecycle management for OBS includes periodically deleting objects from buckets and transitioning between object storage classes based on pre-defined rules.

You may configure lifecycle management rules to:

-  Periodically delete files that are only meant to be retained for specified periods of time.
-  Transition documents that are seldom accessed to the Warm or Cold storage class or delete them.

You can define lifecycle rules to identify objects in the scenarios above and further manage their lifecycles.

Using lifecycle rules to transition objects that are no longer frequently accessed to the Cold or Warm storage class can save costs. Transition basically means that the object storage class is altered without copying the object. You can also manually change the storage class of an object on the **Objects** page. For details, see :ref:`Uploading a File or Folder <obs_03_1061>`.

Lifecycle management rules have two key elements:

-  Policy: You can configure a lifecycle rule for it to apply to a set of objects with the specified prefix, or to apply to the entire bucket (that is, apply to all the objects in the bucket).
-  Time: You can use a lifecycle rule to specify the number of days after which objects that have been last updated and meet specified conditions are automatically transitioned to the Warm or Cold storage class, or are automatically deleted upon expiration.

   -  **Transition to Warm**: This defines the number of days since the last object update after which objects meeting specified conditions are automatically transitioned to the Warm storage class.
   -  **Transition to Cold**: This defines the number of days since the last object update after which objects meeting specified conditions are automatically transitioned to the Cold storage class.
   -  **Expiration Time**: This defines the number of days since the last object update after which objects meeting specified conditions are automatically expired and then deleted.

Objects can be transitioned to Warm at least 30 days after their last update. If you configure to transition objects first to Warm and then Cold, the objects must stay Warm at least 30 days before they can be transitioned to Cold. For example, if you configure to transition objects to Warm 33 days after their last update, the objects can be transitioned to Cold at least 63 days after their last update. If only transition to Cold is used, but transition to Warm is not, there is no limit on the number of days for transition. The number of days for objects to expire must be greater than the two transition times.
