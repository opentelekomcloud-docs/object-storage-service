:original_name: obs_40_0007.html

.. _obs_40_0007:

Accessing OBS Using Permanent Access Keys
=========================================

OBS provides REST APIs that supports authenticated requests and anonymous requests. Anonymous requests are typically used for scenarios that require public access, such as accessing a hosted static website. In most scenarios, accessing OBS resources require authenticated requests. An authenticated request contains a signature value. The signature value is calculated based on the requester's access keys (a pair of AK and SK) as the encryption factor and the specific information carried by the request body. The signature calculation process is included in the SDK. You only need to prepare the access keys when initializing the SDK. Then the signature calculation is implemented automatically. However, if a client uses the REST APIs to develop a program to access OBS, the client needs to calculate the signature based on the signature algorithm defined by the OBS and add the signature to the request.

Users can create permanent access keys (a pair of AK and SK) on the **My Credentials** page.

-  AK stands for the access key ID. It is the unique ID associated with the secret access key (SK). An AK is used together with an SK to encrypt and sign a request.
-  They can identify a request sender and prevent the request from being modified.

An AK is also the unique identifier of an IAM user. OBS identifies a user based on its AK and SK, and then checks the permissions.

For details about how to obtain the permanent access keys, see `Where Can I Obtain Access Keys (AK and SK)? <https://docs.otc.t-systems.com/en-us/browsertg/obs/obs_03_1007.html>`__
