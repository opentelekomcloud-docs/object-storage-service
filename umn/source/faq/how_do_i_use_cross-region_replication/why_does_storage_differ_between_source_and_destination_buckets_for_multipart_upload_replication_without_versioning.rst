:original_name: obs_faq_101803.html

.. _obs_faq_101803:

Why Does Storage Differ Between Source and Destination Buckets for Multipart Upload Replication Without Versioning?
===================================================================================================================

If the source and destination buckets are from different regions and do not have versioning enabled, uploading an object to the source bucket in multipart upload mode will overwrite an existing object with the same name in the bucket. The metadata of the overwritten object cannot be found when the object is replicated to the destination bucket. If certain overwritten parts in the source bucket have been replicated to the destination bucket, these parts cannot be assembled and will remain in the destination bucket.

**Solution**: Configure a lifecycle rule to delete expired fragments for the destination bucket. For details, see :ref:`Configuring a Lifecycle Rule <obs_03_0335>`.

For example, if bucket A and bucket B do not have versioning enabled, and a replication rule is set for bucket A to replicate objects to bucket B, uploading **object.txt** to bucket A repeatedly in multipart upload mode may result in fragments of **object.txt** in bucket B. In this case, you need to manually delete the parts that cannot be assembled or configure a lifecycle rule to delete expired fragments in the destination bucket.
