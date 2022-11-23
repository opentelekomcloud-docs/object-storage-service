:original_name: obs_03_0405.html

.. _obs_03_0405:

Creating Access Keys (AK and SK)
================================

This section describes how to create access keys (AK and SK) in OBS Console. A pair of AK and SK is used to encrypt the signature of a request, ensuring that the request is secure and integral, and that identities of the request sender and receiver are correct.

Background Information
----------------------

AKs and SKs support the authentication mechanism of Identity and Access Management (IAM).

-  An Access Key ID (AK) defines a user that accesses the OBS system. An AK belongs to only one user, but one user can have multiple AKs. The OBS system recognizes the users who access the system by their AKs.
-  A Secret Access Key (SK) is the key used by users to access OBS. It is the authentication information generated based on the AK and the request header. An SK and an AK group into a pair of access keys.

Limitations and Constraints
---------------------------

Each user can create a maximum of two valid AK/SK pairs.

Prerequisites
-------------

An account has been registered and activated.

Procedure
---------

#. Log in to OBS Console.
#. On the top navigation menu, click the username and select **My Credentials**.
#. **My Credentials** page is displayed. Choose **Access Keys** > **Add Access Key**

   .. note::

      Each user can create a maximum of two valid access keys.

#. In the **Add Access Key** dialog box that is displayed, enter the password and its verification code.

   .. note::

      -  If you have not bound an email address or mobile number, enter only the password.
      -  If you have bound an email address and a mobile number, you can verify through either one.

#. Click **OK**.
#. Save the key as prompted. The key is directly saved to the default download folder of the web browser.

   .. note::

      -  To prevent the access keys from being leaked, keep them secure. If you click **Cancel** in the dialog box, the access keys will not be downloaded, and you cannot download them later. You can re-create an access key if you need to use it.
      -  The access keys (AK and SK) need to be updated regularly.

#. Open the downloaded **credentials.csv** file to obtain the access keys (AK and SK).
