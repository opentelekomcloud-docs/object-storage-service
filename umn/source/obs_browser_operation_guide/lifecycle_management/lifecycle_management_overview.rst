:original_name: obs_03_0425.html

.. _obs_03_0425:

Lifecycle Management Overview
=============================

Lifecycle management means periodically deleting objects in a bucket or transitioning between object storage classes by configuring rules.


.. figure:: /_static/images/en-us_image_0138955590.png
   :alt: **Figure 1** Lifecycle management

   **Figure 1** Lifecycle management

You may configure lifecycle rules to:

-  Periodically delete logs that are only meant to be retained for a specific period of time (a week or a month).
-  Transition documents that are seldom accessed to the Warm or Cold storage class or delete them.

You can define lifecycle rules for your scenarios similar to those mentioned above to better manage your objects.

Objects that are no longer frequently accessed can be transitioned to **Warm** or **Cold**, saving your costs. In short, transition basically means that the object storage class is altered without copying the object. You can also manually change the storage class of an object on the **Objects** page. For details, see :ref:`Uploading a File or Folder <obs_03_0414>`.

Lifecycle rules have two key elements:

-  Policy: You can specify the prefix of object names so that objects whose names have this prefix are restricted by the rules. You can configure lifecycle rules for a bucket so that all objects in the bucket can be restricted by the lifecycle rules.
-  Time: You can specify the number of days after which objects that have been last updated and meet specified conditions are automatically transitioned to Warm, Cold, or expire and are then automatically deleted.

   -  Transition to Warm: This defines the number of days since the last object update after which objects meeting specified conditions are automatically transitioned to the Warm storage class.
   -  Transition to Cold: This defines the number of days since the last object update after which objects meeting specified conditions are automatically transitioned to the Cold storage class.
   -  Expiration time: This defines the number of days since the last object update after which objects meeting specified conditions are automatically expired and then deleted.

The previous number of days for objects to be transitioned to **Warm** is at least 30. If objects are configured to be transitioned to both **Warm** and **Cold**, the number of days for transition to **Cold** must be at least 30 days later than that for transition to **Warm**. For example, if the number of days for transition to **Warm** is 33, that for transition to **Cold** must be 63 at least. If only transition to **Cold** is enabled and transition to **Warm** is disabled, there is no limit on the number of days for transition. The number set for expiration time must be larger than that specified for any of the transition operations.
