:original_name: en-us_topic_0045853514.html

.. _en-us_topic_0045853514:

Managing Fragments
==================

Background Information
----------------------

Data can be uploaded to OBS using multipart uploads. Fragments are generated, if a multipart upload fails because of the following reasons (included but not limited to):

-  The network is in poor conditions, and the connection to the OBS server is interrupted frequently.
-  The upload task is manually suspended.
-  The device is faulty.
-  The device is powered off suddenly.

On OBS Console, storage used by fragments is charged. Clear fragments when they are not needed. If a file upload task fails, upload the file again.

.. important::

   Generated fragments take up storage space that is billable.

Procedure
---------

#. In the bucket list, click the bucket you want to operate. The **Overview** page is displayed.

#. In the navigation pane, choose **Objects**.

#. Click **Fragments**, select the fragment that you want to delete, and then click **Delete** on the right of the fragment.

   You can also select multiple fragments and click **Delete** above fragment list to batch delete them.

#. Click **Yes** to confirm the deletion.
