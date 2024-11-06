:original_name: obs_03_0416.html

.. _obs_03_0416:

Accessing an Object Using Its Object URL
========================================

The object uniform resource locator (URL) (object sharing) function allows anonymous users to access object data using object URLs.

Prerequisites
-------------

An anonymous user has been assigned with the permission to read the specified object. For details, see :ref:`Configuring an Object ACL <en-us_topic_0045853821>`.

Procedure
---------

#. Log in to OBS Browser.

#. Click the bucket to be operated.

#. Click the bucket for which you want to configure the object URL function, and click |image1| next to the object to be shared to view the object URL. For details, see :ref:`Figure 1 <obs_03_0416__fe095887a5e664d6aa0dd30456edda8b1>`.

   .. _obs_03_0416__fe095887a5e664d6aa0dd30456edda8b1:

   .. figure:: /_static/images/en-us_image_0129829000.png
      :alt: **Figure 1** Object properties

      **Figure 1** Object properties

   -  If you select **Other object storage services** when logging in to OBS Browser, the object URL is in the format of https://*storage server IP address* or *domain name*/*bucket name*/*directory level*/*object name*. If the object is in the root directory of the bucket, its URL does not contain any directory level.
   -  If you select **OBS** when logging in to OBS Browser, the object URL is in the format of https://*bucket name.domain name*/*directory level*/*object name.* If the object is in the root directory of the bucket, its URL does not contain any directory level.

   .. note::

      To allow anonymous users to access objects stored in a bucket of Cold storage class using the URL, ensure that the objects are in the **Restored** state.

      The method of using a browser to access objects varies depending on the object type. You can directly open **.txt** and **.html** files using a browser. However, when you open **.exe** and **.dat** files using a browser, the files are automatically downloaded to your local computer.

#. Click **Copy** to copy the URL of the object.

#. In the displayed dialog box, click **Close** to close the dialog box.

#. Paste the object URL in the address box of a web browser. Press **Enter**, and then you can access the object.

.. |image1| image:: /_static/images/en-us_image_0237534488.png
