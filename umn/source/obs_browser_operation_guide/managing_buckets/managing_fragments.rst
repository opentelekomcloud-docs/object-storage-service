:original_name: en-us_topic_0045853710.html

.. _en-us_topic_0045853710:

Managing Fragments
==================

Background Information
----------------------

Data can be uploaded to OBS using multipart uploads. Fragments are generated, if a multipart upload fails because of the following reasons (included but not limited to):

-  The network is in poor condition, and connection to the OBS server is frequently interrupted.
-  The upload task is manually suspended.
-  The device is faulty.
-  The device is powered off suddenly.

If a file fails to be uploaded or the upload task is suspended, fragments are generated and stored in OBS. You can resume the upload through task management. After the resumable upload completes, the fragments will be cleared automatically.

You can also use the fragment management function to clear fragments. If you resume an upload task after clearing the fragments, the upload progress will be lost and the task needs to be re-uploaded.

.. important::

   The fragment storage in OBS is billed.

Procedure
---------

#. Log in to OBS Browser.

#. Click the blank area in the row of the bucket and choose **More** > **Manage Fragment**.

#. In the **Manage Fragment** dialog box, click **Check** to refresh the fragment list. Select a fragment and click |image1| on the right to delete it.

   You can click **Delete All** above the fragment list to delete all the fragments.

#. In the dialog box that is displayed, confirm the information and click **Yes**.

#. In the displayed dialog box, click **Close** to close the dialog box.

#. In the **Manage Fragment** dialog box, click **Close** to close the dialog box and return to the OBS Browser home page.

.. |image1| image:: /_static/images/en-us_image_0237534487.png
