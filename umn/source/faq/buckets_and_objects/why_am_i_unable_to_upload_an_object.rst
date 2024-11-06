:original_name: obs_faq_0134.html

.. _obs_faq_0134:

Why Am I Unable to Upload an Object?
====================================

-  Check whether the network connectivity between the local computer and OBS is normal. If the network is faulty, restore the network connection.

-  If a message indicating "service unavailable" is displayed when objects are being uploaded, try again later.

-  Check whether the account is in arrears or the account balance is insufficient. If this is the case, pay off the outstanding balance or top up the account.

-  Check whether the account has the permissions required to upload objects. This check should cover the IAM policies, bucket policies, and bucket ACLs. If the account does not have the required permissions, grant the permissions first.

-  For OBS Browser, a disordered database can cause uploads to fail. You can empty the database and upload the file again.

   Delete all files in the :ref:`database path <obs_03_0443>`.

-  If the fault persists, contact customer service.
