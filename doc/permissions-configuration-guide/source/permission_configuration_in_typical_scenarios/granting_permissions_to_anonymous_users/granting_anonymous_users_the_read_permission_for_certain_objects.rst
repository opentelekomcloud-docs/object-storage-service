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

#. In the bucket list, click the bucket name you want to go to the **Objects** page.

#. In the navigation pane, choose **Permissions** > **Bucket Policies**.

#. On the **Bucket Policies** page, click **Create**.

#. Configure a bucket policy.


   .. figure:: /_static/images/en-us_image_0000002142681682.png
      :alt: **Figure 1** Configuring a bucket policy

      **Figure 1** Configuring a bucket policy

   .. table:: **Table 1** Parameters for configuring a bucket policy

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                        |
      +===================================+====================================================================================================================+
      | Policy view                       | Select **Visual Editor** or **JSON** based on your own habits. **Visual Editor** is used here.                     |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------+
      | Policy Name                       | Enter a policy name.                                                                                               |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------+
      | Effect                            | Select **Allow**.                                                                                                  |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------+
      | Principal                         | -  Select **All accounts**.                                                                                        |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------+
      | Resources                         | -  Select **Specified objects**.                                                                                   |
      |                                   | -  Enter an object name prefix for the resource path.                                                              |
      |                                   |                                                                                                                    |
      |                                   |    .. note::                                                                                                       |
      |                                   |                                                                                                                    |
      |                                   |       a. You can click **Add** to specify multiple resource paths.                                                 |
      |                                   |                                                                                                                    |
      |                                   |       b. You can specify a specific object or an object set. **\*** indicates all objects in the bucket.           |
      |                                   |                                                                                                                    |
      |                                   |          For one object, enter *object name*.                                                                      |
      |                                   |                                                                                                                    |
      |                                   |          To specify a set of objects, enter *Object name prefix*\ **\***, **\***\ *Object name suffix*, or **\***. |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------+
      | Actions                           | -  Choose **Use a template**.                                                                                      |
      |                                   | -  Select **Object Read-Only**.                                                                                    |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------+

#. Confirm and click **Create**.

Verification
------------

After the permission is set, click the object. Its URL is displayed under **Link**. Share the URL over the Internet, so that all users can access or download the object through the Internet.
