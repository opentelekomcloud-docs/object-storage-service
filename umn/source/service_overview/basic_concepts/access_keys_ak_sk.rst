:original_name: obs_03_0208.html

.. _obs_03_0208:

Access Keys (AK/SK)
===================

OBS supports AK/SK authentication. The AK/SK encryption method is used to authenticate a request sender. When you use OBS APIs for secondary development and use the AK and SK for authentication, the signature must be computed based on the algorithm defined by OBS and added to the request.

OBS supports authentication using a permanent AK/SK pair, or using a temporary AK/SK pair and a security token.

**Permanent AK/SK Pair**

You can create a pair of permanent AK and SK on the **My Credentials** page.

-  Access key ID (AK): indicates the ID of the access key. It is the unique ID associated with the SK. The AK and SK are used together to obtain an encrypted signature for a request.
-  Secret access key (SK): indicates the private key used together with its associated AK to cryptographically sign requests. The AK and SK are used together to identify a request sender to prevent the request from being modified.

**Temporary AK/SK Pair**

A temporary AK/SK pair and the security token are temporary access tokens granted by the system to users. The validity period of the tokens ranges from 15 minutes to 24 hours. After the tokens expire, you need to obtain the tokens again. A temporary AK/SK pair and the security token comply with the least privilege principle and can only be used to temporarily access OBS. A 403 error will be returned if the security token is not available.

-  Temporary AK: indicates the ID of a temporary access key. It is the unique ID associated with the SK. The AK and SK are used together to obtain an encrypted signature for a request.
-  Temporary SK: indicates the temporary private key used together with its associated temporary AK. The AK and SK are used together to identify a request sender to prevent the request from being modified.
-  Security token: indicates the token used together with the temporary AK and SK to access all resources of a specified account.

When using the following tools to access OBS resources, you need to use the AK/SK pair for security authentication.

.. table:: **Table 1** OBS resource management tools

   +-------------+-----------------------------------------------------------------+
   | Tool        | AK/SK Configuration                                             |
   +=============+=================================================================+
   | OBS Browser | Configure the AK and SK during account configuration.           |
   +-------------+-----------------------------------------------------------------+
   | SDKs        | Configure the AK and SK in the initialization phase.            |
   +-------------+-----------------------------------------------------------------+
   | APIs        | Add the AK/SK pair to the request when computing the signature. |
   +-------------+-----------------------------------------------------------------+

References
----------

For details about how to obtain a permanent AK/SK pair, see :ref:`Creating Access Keys (AK and SK) <obs_03_0405>`.

For details about how to obtain a temporary AK/SK pair and security token, see `Obtaining a Temporary AK/SK <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0097949518.html>`__.
