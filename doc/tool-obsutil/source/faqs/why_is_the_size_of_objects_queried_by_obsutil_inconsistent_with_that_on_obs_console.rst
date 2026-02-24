:original_name: obs_11_0077.html

.. _obs_11_0077:

Why Is the Size of Objects Queried by obsutil Inconsistent with That on OBS Console?
====================================================================================

When you use obsutil to list all objects in a bucket, the listing result contains the total size of the objects. If the total size is different from that on OBS Console or OBS Browser+, go through the following list to locate the fault:

#. To query the number of objects in a bucket and the space occupied by the objects, both OBS Browser+ and OBS Console call the API for . The results obtained by them correspond to the output by calling the **stat** command in obsutil. On OBS Browser+ and OBS Console, the bucket storage statistics are measured in the backend and are not real time. Therefore, you are advised to use obsutil to query the storage usage.
#. Check whether there are object fragments in the bucket on OBS Browser+ and OBS Console by referring to :ref:`Listing Multipart Upload Tasks <obs_11_0019>`. OBS bucket storage statistics cover the size of both objects and object fragments in a bucket, but obsutil lists only the objects in a bucket.
