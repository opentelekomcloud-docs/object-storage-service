:original_name: obs_03_1007.html

.. _obs_03_1007:

Where Can I Obtain Access Keys (AK and SK)?
===========================================

When using OBS Browser+ to access OBS, you do not need to provide the account or IAM user login information. Instead, you use the access keys (a pair of AK and SK) of the account or IAM user for authentication. Therefore, you need to obtain the access keys in advance.

-  Access key ID (AK) is a unique identifier used in conjunction with a secret access key (SK) to sign requests cryptographically. AK is used together with SK to obtain an encrypted signature for a request.
-  SK is used in conjunction with an AK to sign requests cryptographically. It identifies a request sender and prevents the request from being modified.

Procedure
---------

#. Log in to OBS Console.

#. Move the mouse pointer over the username in the upper right corner and select **My Credentials** from the drop-down list.

#. In the navigation pane on the left, select **Access Keys**.

#. Click **Create Access Key**.

#. On the **Create Access Key** page, enter the login password. Enter the verification code sent to your email or mobile phone.

   Note: For IAM users, if no email address or mobile number is specified when creating the user, use the login password for authentication.

#. Click **OK** to download the credential file.

   .. note::

      -  The web browser automatically downloads the **credentials.csv** file. In the file, the value of **Access Key Id** is the AK, and the value of **Secret Access Key** is the SK.
      -  To prevent the access keys from being leaked, keep them secure.
