:original_name: obs_03_0032.html

.. _obs_03_0032:

Configuring a User-Defined Domain Name
======================================

Procedure
---------

#. In the bucket list, click the bucket you want to operate to go to the **Objects** page.

#. In the navigation pane, choose **Domain Name Mgmt**.

#. Click **Configure User Domain Name** in the upper part of the page. Then, enter the domain name to configure, as shown in :ref:`Figure 1 <obs_03_0032__fig53010339108>`.

   The suffix of a user-defined domain name can contain 2 to 6 uppercase or lowercase letters.

   .. _obs_03_0032__fig53010339108:

   .. figure:: /_static/images/en-us_image_0000001458743966.png
      :alt: **Figure 1** Configuring a user-defined domain name

      **Figure 1** Configuring a user-defined domain name

#. Click **OK**.

#. Configure a CNAME record on the DNS, and map the user-defined domain name (for example, **example.com**) to the domain name of the bucket.

   The CNAME configuration varies depending on DNS providers. For details, contact your DNS provider.
