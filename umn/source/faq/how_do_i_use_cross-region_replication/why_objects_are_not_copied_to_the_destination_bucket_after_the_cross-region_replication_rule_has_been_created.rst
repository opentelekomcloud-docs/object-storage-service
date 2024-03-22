:original_name: obs_faq_0137.html

.. _obs_faq_0137:

Why Objects Are Not Copied to the Destination Bucket After the Cross-Region Replication Rule Has Been Created?
==============================================================================================================

-  If the function of synchronizing existing objects is not enabled for a cross-region replication rule, existing objects in a bucket will not be copied to the destination bucket.
-  Newly uploaded objects in the Cold storage class are not replicated to the destination bucket.
-  A cross-region replication rule may not take effect immediately upon its configuration. Accordingly, the objects that this rule is applied to may not be replicated immediately after the rule is configured.
