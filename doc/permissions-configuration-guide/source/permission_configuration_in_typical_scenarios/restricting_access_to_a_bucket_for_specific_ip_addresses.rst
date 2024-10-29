:original_name: obs_40_0036.html

.. _obs_40_0036:

Restricting Access to a Bucket for Specific IP Addresses
========================================================

Scenario
--------

This case describes how to restrict the source IP addresses that can access an OBS bucket. The following shows how to deny a client access whose source IP address is within the range of 114.115.1.0/24.

Recommended Configuration
-------------------------

Bucket policy

Procedure
---------

#. In the navigation pane of OBS Console, choose **Object Storage**.

#. In the bucket list, click the bucket name you want to go to the **Overview** page.

#. In the navigation pane, choose **Permissions**.

#. On the **Bucket Policies** page, click **Create Bucket Policy** under **Custom Bucket Policies**.

#. Configure a bucket policy.


   .. figure:: /_static/images/en-us_image_0000001386029478.png
      :alt: **Figure 1** Configuring a bucket policy

      **Figure 1** Configuring a bucket policy

   .. table:: **Table 1** Parameters for creating a bucket policy

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                  |
      +===================================+==============================================================================================================================+
      | Policy Mode                       | Select **Customized**.                                                                                                       |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | Effect                            | Select **Deny**.                                                                                                             |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | Principal                         | -  Choose **Include** > **Cloud service user**.                                                                              |
      |                                   | -  **Account ID**: Enter **\***, which indicates that the setting takes effect for all registered users and anonymous users. |
      |                                   | -  **User ID**: Leave the user ID blank.                                                                                     |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | Resources                         | Select **Include** > **Entire bucket**.                                                                                      |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | Actions                           | -  **Include**                                                                                                               |
      |                                   | -  Action Name: Select **\***, which indicates all permissions.                                                              |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | Conditions                        | -  **Conditional Operator**: **IpAddress**                                                                                   |
      |                                   | -  **Key**: Select **SourceIp**.                                                                                             |
      |                                   | -  **Value**: Enter **114.115.1.0/24**.                                                                                      |
      |                                   |                                                                                                                              |
      |                                   |    .. note::                                                                                                                 |
      |                                   |                                                                                                                              |
      |                                   |       Use commas (,) to separate multiple IP addresses.                                                                      |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      If you want to allow clients whose IP addresses are outside the configured range to access your bucket, grant access permissions to anonymous users by referring to :ref:`Granting Permissions to Anonymous Users <obs_40_0030>`.

#. Click **OK**.

Verification
------------

Initiate an access request from an IP address within 114.115.1.0/24. The access is denied. Initiate an access request from an IP address outside 114.115.1.0/24. The access is allowed.

Related Scenarios
-----------------

-  To allow only a specified IP address to access the OBS bucket, set **Condition Operator** to **NotIpAddress** and specify the allowed IP address as the **Value**.
