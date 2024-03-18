:original_name: obs_03_0132.html

.. _obs_03_0132:

Granting Anonymous Users Permission to Access Objects
=====================================================

An enterprise stores a large volume of map data in OBS, and offers the data for public query. This enterprise sets a read permission for anonymous users, and provides the data URLs on the Internet. Then all users can read or download the data through the URLs.

Procedure
---------

#. Log in to OBS Console and click **Create Bucket** to create a bucket.

#. In the bucket list, click the name of the newly created bucket. On the displayed object management page, upload the map data to the new bucket. The map data is stored as an object.

#. Click the object name. The object details page is displayed.

#. Under **Object ACL** > **Public Permissions**, click **Edit** to grant the object read permission for anonymous users, as shown in :ref:`Figure 1 <obs_03_0132__fig58496641194012>`.

   .. _obs_03_0132__fig58496641194012:

   .. figure:: /_static/images/en-us_image_0168390495.png
      :alt: **Figure 1** Granting the object read permission to anonymous users

      **Figure 1** Granting the object read permission to anonymous users

#. Click **Save** to save the permission setting.

Verification
------------

#. Click the object. Its URL is displayed under **Link**. Share the URL over the Internet, so that all users can access or download the object through the Internet.
#. An anonymous user can view the object by copying the URL of the object to the web browser.
