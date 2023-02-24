:original_name: en-us_topic_0045853821.html

.. _en-us_topic_0045853821:

Configuring an Object ACL
=========================

Prerequisites
-------------

You are the object owner or you have the permission to write the object ACL.

An object owner is the account that uploads the object, but may not be the owner of the bucket that stores the object. For example, account **B** is granted the permission to access a bucket of account **A**, and account **B** uploads a file to the bucket. In that case, account **B**, instead of the bucket owner account **A**, is the owner of the object. By default, account A is not allowed to access this object and cannot read or modify the object ACL.

Procedure
---------

#. In the bucket list, click the bucket you want to operate. The **Overview** page of the bucket is displayed.

#. In the navigation pane, click **Objects**.

#. Click the object to be operated.

#. On the **Object ACL** tab, click **Edit** to set ACL permissions of the **Owner**, **Registered User**, and **Anonymous User** for the target object.

   .. note::

      If the object is encrypted, the ACL permission cannot be configured for registered users and anonymous users.

#. Click **Add** to set the ACL permissions of a specific account. For details, see :ref:`Figure 1 <en-us_topic_0045853821__fig3474335195326>`.

   Enter an account ID or account name and set ACL permissions for the account. You can obtain the account ID or account name on the **My Credentials** page. The account ID and account name correspond to the **Domain ID** and **Domain Name** respectively on the **My Credentials** page.

   .. _en-us_topic_0045853821__fig3474335195326:

   .. figure:: /_static/images/en-us_image_0168396382.png
      :alt: **Figure 1** Adding ACL permissions for objects

      **Figure 1** Adding ACL permissions for objects

#. Click **Save**.
