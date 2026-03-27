:original_name: obs_11_0077.html

.. _obs_11_0077:

Why Does obsutil Show a Different Total Object Size Than OBS Console?
=====================================================================

When you use obsutil to list all objects in a bucket, the listing result includes the total size of the objects. If the total size is different from that shown on OBS Console or OBS Browser+, the mismatch usually comes from two factors:

#. OBS Browser+ and OBS Console both use the API for obtaining storage information of a bucket to check how many objects a bucket contains and how much storage they use. This is the same information returned by the **stat** command in obsutil. However, the bucket storage data on OBS Browser+ and OBS Console is measured in the backend, so it is not updated in real time. Because of this delay, the values on OBS Browser+ and OBS Console should not be used for real-time verification.
#. The data shown on OBS Browser+ and OBS Console covers the size of both objects and fragments in a bucket, but obsutil lists only the objects in a bucket. You can check whether there are fragments in the bucket on OBS Browser+ or OBS Console or by :ref:`using the obsutil command that lists multipart uploads <obs_11_0019>`.
