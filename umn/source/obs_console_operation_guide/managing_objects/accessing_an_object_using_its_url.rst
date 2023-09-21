:original_name: obs_03_0319.html

.. _obs_03_0319:

Accessing an Object Using Its URL
=================================

You can grant anonymous users the read permission for an object so they can access the object using the shared object URL.

Prerequisites
-------------

Anonymous users have the read permission for the object. For details about permission granting, see :ref:`Granting Object Access Permissions to Anonymous Users <obs_03_0132>`.

.. note::

   Encrypted objects cannot be shared.

Procedure
---------

#. In the bucket list, click the bucket you want to operate. The **Overview** page is displayed.

#. In the navigation pane, choose **Objects**.

#. Click the object to be shared. The object information is displayed on the top part of the page. The **Link** displays the shared link of the object. For details, see :ref:`Figure 1 <obs_03_0319__fig36534596192426>`.

   Anonymous users can access the object by clicking the URL. The object URL is in the format of **https://**\ *bucket name*.\ *domain name*/*directory level*/*object name*. If the object resides in the root directory of the bucket, its URL does not contain the directory level.

   .. _obs_03_0319__fig36534596192426:

   .. figure:: /_static/images/en-us_image_0129482329.png
      :alt: **Figure 1** Object link

      **Figure 1** Object link

   .. note::

      -  To allow anonymous users to access objects in Cold storage using URLs, ensure that these objects are in the **Restored** state.
      -  The method of using a browser to access objects varies depending on the object type. You can directly open **.txt** and **.html** files using a browser. However, when you open **.exe** and **.dat** files using a browser, the files are automatically downloaded to your local computer.
