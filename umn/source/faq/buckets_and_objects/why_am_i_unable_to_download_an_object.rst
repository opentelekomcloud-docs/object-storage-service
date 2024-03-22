:original_name: obs_faq_0135.html

.. _obs_faq_0135:

Why Am I Unable to Download an Object?
======================================

-  Check whether the network connectivity between the local computer and OBS is normal. If the network is down, restore the network connection.
-  Check whether the account is in arrears or the account balance is insufficient. If this is the case, pay off the outstanding balance or top up the account.
-  Check whether the account has the permissions needed to download objects from the bucket. This check should cover IAM policies, bucket policies, object policies, bucket ACLs, and object ACLs. If the account does not have the required permissions, grant the permissions first.
-  Check whether the current object is encrypted with KMS. If yes, downloading the object from OBS Console or OBS Browser will fail. To download an encrypted object using the SDK or API, a decryption key is required.
-  Check whether the object is in the Cold storage class. If it is and the status is **Unrestored**, restore the object first.
-  If the fault persists, contact customer service.
