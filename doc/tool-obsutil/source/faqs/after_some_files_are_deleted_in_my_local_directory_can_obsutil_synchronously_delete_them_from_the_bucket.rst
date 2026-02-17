:original_name: obs_11_0075.html

.. _obs_11_0075:

After Some Files Are Deleted in My Local Directory, Can obsutil Synchronously Delete Them from the Bucket?
==========================================================================================================

No.

obsutil allows you to upload your local directory to an OBS bucket. After the synchronization, if you delete some files in the local directory and then perform an incremental upload, obsutil only checks whether there are incremental files that need to be uploaded. obsutil cannot detect the deleted files, so these files will not be deleted in the bucket.

If new files are added to your local directory during an upload, the number of objects uploaded by obsutil may be inconsistent with that in the local directory. To keep the files same in both places, run the incremental upload command after the upload is complete.
