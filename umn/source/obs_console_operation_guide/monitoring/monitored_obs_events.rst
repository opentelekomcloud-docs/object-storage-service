:original_name: obs_03_063603.html

.. _obs_03_063603:

Monitored OBS Events
====================

Functions
---------

You can configure alarm rules on Cloud Eye to monitor critical events or operation events related to your cloud resources. Once configured, Cloud Eye will notify you when the specified events happen.

Namespace
---------

SYS.OBS

Monitored Events
----------------

.. _obs_03_063603__table13653193214714:

.. table:: **Table 1** OBS events that can be monitored

   +-----------------------------+--------------------+-----------+----------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Event Name                  | Event ID           | Severity  | Description                                                          | Handling Suggestion                                                                                                                              | Impact                                                                                                                                  |
   +=============================+====================+===========+======================================================================+==================================================================================================================================================+=========================================================================================================================================+
   | Deleting buckets            | deleteBucket       | Major     | An event is reported when a bucket deletion takes place.             | Deleted buckets cannot be recovered. If you want to reuse a deleted bucket, create a bucket with the same name again.                            | Deleting buckets may affect your services. Before deleting a bucket, make sure that your services do not depend on it.                  |
   +-----------------------------+--------------------+-----------+----------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Deleting bucket policies    | deleteBucketPolicy | Major     | An event is reported when a bucket policy deletion takes place.      | -  You can delete unwanted bucket policies.                                                                                                      | After a bucket policy is deleted, some users may fail to access the associated bucket and the objects in it.                            |
   |                             |                    |           |                                                                      | -  If you delete a bucket policy by mistake, create the bucket policy again.                                                                     |                                                                                                                                         |
   +-----------------------------+--------------------+-----------+----------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Configuring bucket ACLs     | setBucketAcl       | Minor     | An event is reported when a bucket ACL configuration takes place.    | If you do not want an account to access a bucket or the objects in it, you can delete the bucket ACL.                                            | A bucket ACL grants an account the access to the bucket and the objects in it.                                                          |
   +-----------------------------+--------------------+-----------+----------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Configuring bucket policies | setBucketPolicy    | Minor     | An event is reported when a bucket policy configuration takes place. | If you do not need a bucket policy to perform fine-grained access control over a bucket and the objects in it, you can delete the bucket policy. | A bucket policy grants an account or IAM users some operation permissions for the bucket or the objects in it under certain conditions. |
   +-----------------------------+--------------------+-----------+----------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
