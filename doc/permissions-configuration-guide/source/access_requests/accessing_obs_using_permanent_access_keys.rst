:original_name: obs_40_0007.html

.. _obs_40_0007:

Accessing OBS Using Permanent Access Keys
=========================================

OBS REST APIs support authenticated requests and anonymous requests. Anonymous requests are typically used for public access, such as accessing hosted static websites. In most cases, authenticated requests are required for accessing OBS resources. An authenticated request contains a signature value that is calculated based on the requester's access keys (AK and SK) and the specific information carried in the request body. You only need to prepare the access keys for the SDK. The SDK will then automatically calculate the signature for you. However, if a client uses REST APIs to develop a program to access OBS, the client needs to calculate the signature based on the signature algorithm defined by OBS and add the signature to the request.

Users can create permanent access keys (a pair of AK and SK) on the **My Credentials** page.

-  AK: a unique ID of the secret access key (SK). An AK is used together with an SK to encrypt and sign a request. For details, see `User Signature Authentication <https://docs.otc.t-systems.com/object-storage-service/api-ref/calling_apis/authentication/user_signature_authentication.html>`__.
-  SK: a secret access key used together with its AK to verify a request sender and prevent the request from being tampered with.

An AK can also identify an IAM user. OBS identifies an IAM user by their AK and SK, and then checks whether they have the permissions to access the resources they are requesting.

For details about how to obtain the permanent access keys, see `Where Can I Obtain Access Keys (AK and SK)? <https://docs.otc.t-systems.com/en-us/browsertg/obs/obs_03_1007.html>`__
