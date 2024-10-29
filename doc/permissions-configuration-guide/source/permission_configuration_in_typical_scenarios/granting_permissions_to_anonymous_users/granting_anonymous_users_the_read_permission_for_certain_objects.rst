:original_name: obs_40_0033.html

.. _obs_40_0033:

Granting Anonymous Users the Read Permission for Certain Objects
================================================================

Scenario
--------

Enterprise A stores a large volume of map data in OBS, and offers the data for public query. This enterprise sets a read permission for anonymous users, and provides the data URLs on the Internet. Then all users can read or download the data through the URLs.

Procedure
---------

#. In the navigation pane of OBS Console, choose **Object Storage**.

#. In the bucket list, click the bucket to be operated. The **Overview** page of the bucket is displayed.

#. In the navigation pane, click **Objects**.

#. Click the name of the object to be operated.

#. On the **Object ACL** tab page, click the target object and click **Object ACL**.

#. In **Public Permissions** > **Anonymous User**, click **Edit** and select the object read permission for anonymous users.


   .. figure:: /_static/images/en-us_image_0000001436307565.png
      :alt: **Figure 1** Granting the public read permission on objects to anonymous users

      **Figure 1** Granting the public read permission on objects to anonymous users

#. Click **Save** to save the permission setting.

Verification
------------

After the permission is set, click the object. Its URL is displayed under **Link**. Share the URL over the Internet, so that all users can access or download the object through the Internet.
