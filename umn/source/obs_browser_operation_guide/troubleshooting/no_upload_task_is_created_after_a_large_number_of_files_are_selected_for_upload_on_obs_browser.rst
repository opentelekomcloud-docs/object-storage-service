:original_name: obs_03_0441.html

.. _obs_03_0441:

No Upload Task Is Created After a Large Number of Files Are Selected for Upload On OBS Browser
==============================================================================================

Question
--------

Why is no upload task created and nothing displayed on the page after a large number of files are selected for upload using OBS Browser? For example, after a user logs in to OBS Browser and chooses **Upload** > **Upload File** to select a large number of files from drive C for upload, no upload task is created and nothing is displayed on the page.

Answer
------

- Check whether the total name length of all files uploaded exceed approximately 25,500 characters.

If the total name length is above this limit, OBS will stop responding to the upload request.

- Check whether the total number of files uploaded exceed 500.

OBS Browser allows a maximum of 500 files that can be uploaded at a time. To upload more files than this limit, place the files in a folder and then upload the folder to OBS.
