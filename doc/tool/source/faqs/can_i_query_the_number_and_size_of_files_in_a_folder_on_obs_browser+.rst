:original_name: obs_03_1038.html

.. _obs_03_1038:

Can I Query the Number and Size of Files in a Folder on OBS Browser+?
=====================================================================

No. OBS Browser+ does not provide APIs for directly obtaining the number and size of objects prefixed with a certain folder. If you want to query the number and size of objects under that folder, use OBS SDKs or call APIs to list objects under that folder and then traverse the objects to calculate their total size.
