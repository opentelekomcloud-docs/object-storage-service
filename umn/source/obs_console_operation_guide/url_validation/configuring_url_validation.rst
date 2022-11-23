:original_name: obs_03_0341.html

.. _obs_03_0341:

Configuring URL Validation
==========================

OBS blocks access requests from blacklisted URLs and allows those from whitelisted URLs.

Prerequisites
-------------

Static website hosting has been enabled.

Procedure
---------

#. In the bucket list, click the bucket to be operated. The **Overview** page of the bucket is displayed.

#. In the right **Basic Configurations** area, click **URL Validation**. The **URL Validation** page is displayed.

#. Click |image1| next to the text box of **Whitelisted Referers** or **Blacklisted Referers**, and enter the referers.

   The following describes the principles for setting **Referers**:

   -  The length of a whitelist or blacklist cannot exceed 1024 characters.
   -  Referer format:

      -  You can enter multiple referers, each in a line.
      -  The referer parameter supports asterisks (*) and question marks (?). An asterisk works as a wildcard that can replace zero or multiple characters, and a question mark (?) can replace a single character.
      -  If the referer header field contains **http** or **https** during download, the referer must contain **http** or **https**.

   -  When **Whitelisted Referers** is empty but **Blacklisted Referers** is not, all websites except specified ones in the blacklist are allowed to access data in the target bucket.
   -  When **Whitelisted Referers** is not empty and **Blacklisted Referers** is empty or not empty, only specified websites in the whitelist are allowed to access data in the target bucket.

   .. note::

      When **Whitelisted Referers** is the same as **Blacklisted Referers**, the blacklist takes effect. For example, if the fields of both **Whitelisted Referers** and **Blacklisted Referers** are set to **https://www.example.com**, access requests from this address are blocked.

   -  When **Whitelisted Referers** and **Blacklisted Referers** are empty, all websites are allowed to access data in the target bucket by default.
   -  Before determining whether a user has the four types of permissions (**Read**, **Write**, **ACL View**, and **ACL Edit**) for a bucket or objects in the bucket, check whether the user complies with the URL validation principles of the **Referers** field.

#. Click |image2| to save the settings.

.. |image1| image:: /_static/images/en-us_image_0148639849.png
.. |image2| image:: /_static/images/en-us_image_0148639851.png
