:original_name: obs_03_0032.html

.. _obs_03_0032:

Binding a User-Defined Domain Name
==================================

Prerequisites
-------------

A bucket has been created and website files have been uploaded to the bucket.

Procedure
---------

#. In the bucket list, click the bucket to be operated. The **Overview** page of the bucket is displayed.

#. In the navigation pane, select **Domain Name Mgmt**.

#. Click **Bind User Domain Name** and enter the user-defined domain name to be bound, as shown in :ref:`Figure 1 <obs_03_0032__fig53010339108>`.

   Currently, the suffix of a user-defined domain name can contain 2 to 6 uppercase and lowercase letters.

   .. _obs_03_0032__fig53010339108:

   .. figure:: /_static/images/en-us_image_0000001167932237.png
      :alt: **Figure 1** Binding a user domain name

      **Figure 1** Binding a user domain name

#. Click **OK**.

#. Configure a CNAME record on the DNS, and map the user-defined domain name (for example, **example.com**) to the domain name of a bucket.

   The CNAME configuration varies according to different DNS providers. For details, contact your DNS provider.
