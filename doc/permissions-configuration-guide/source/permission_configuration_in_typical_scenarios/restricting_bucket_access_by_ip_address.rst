:original_name: obs_40_0036.html

.. _obs_40_0036:

Restricting Bucket Access by IP Address
=======================================

Scenario
--------

This section describes how to restrict access to an OBS bucket from specific IP addresses. In this example, clients in the IP address range **114.115.1.0/24** are denied access to the bucket.

Recommended Configuration
-------------------------

Bucket policy

Procedure
---------

#. In the navigation pane of OBS Console, choose **Buckets**.

#. In the bucket list, click the desired bucket name to go to the **Objects** page.

#. In the navigation pane, choose **Permissions** > **Bucket Policies**.

#. On the **Bucket Policies** page, click **Create**.

#. Configure a bucket policy.


   .. figure:: /_static/images/en-us_image_0000002678229689.png
      :alt: **Figure 1** Configuring a bucket policy

      **Figure 1** Configuring a bucket policy

   .. table:: **Table 1** Parameters for configuring a bucket policy

      +-----------------------------------+------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                |
      +===================================+============================================================================================================+
      | Policy view                       | Select **Visual Editor** or **JSON** based on your own habits. **Visual Editor** is used here.             |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------+
      | Policy Name                       | Enter a policy name.                                                                                       |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------+
      | Effect                            | Select **Deny**.                                                                                           |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------+
      | Principal                         | -  Select **All accounts**.                                                                                |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------+
      | Resources                         | -  Method 1:                                                                                               |
      |                                   |                                                                                                            |
      |                                   |    -  Select **Entire bucket (including the objects in it)**.                                              |
      |                                   |                                                                                                            |
      |                                   | -  Method 2:                                                                                               |
      |                                   |                                                                                                            |
      |                                   |    -  Select **Current bucket** and **Specified objects**.                                                 |
      |                                   |    -  Set the resource path to **\*** to indicate all objects in the bucket.                               |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------+
      | Actions                           | -  Choose **Customize**.                                                                                   |
      |                                   | -  Select **\*** (indicating all actions).                                                                 |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------+
      | Conditions (Optional)             | -  **Key**: Select **SourceIp**.                                                                           |
      |                                   | -  **Condition Operator**: Select **IpAddress**                                                            |
      |                                   | -  **Value**: Enter **114.115.1.0/24**.                                                                    |
      |                                   |                                                                                                            |
      |                                   |    .. note::                                                                                               |
      |                                   |                                                                                                            |
      |                                   |       -  The IP address specified here is only for reference. Configure it based on the site requirements. |
      |                                   |       -  Use commas (,) to separate multiple IP addresses.                                                 |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------+

   .. note::

      If you want to allow clients whose IP addresses are outside the configured range to access your bucket, grant access permissions to anonymous users by referring to :ref:`Granting Permissions to Anonymous Users <obs_40_0030>`.

#. Confirm and click **Create**.

Verification
------------

Initiate an access request from an IP address within 114.115.1.0/24. The access is denied. Initiate an access request from an IP address outside 114.115.1.0/24. The access is allowed.

Related Scenarios
-----------------

-  To allow only a specified IP address to access an OBS bucket, you need to create two bucket policies:

   Policy 1: Select **Deny** for **Effect**. Set **Condition Operator** to **NotIpAddress** and specify the allowed IP address as the **Value**.

   Policy 2: Select **Allow** for **Effect**. Set **Condition Operator** to **IpAddress** and specify the allowed IP address as the **Value**.
