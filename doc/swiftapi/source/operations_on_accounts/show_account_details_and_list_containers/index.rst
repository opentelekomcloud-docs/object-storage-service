:original_name: obs_03_0016.html

.. _obs_03_0016:

Show Account Details and List Containers
========================================

This operation obtains account metadata and the list of containers in the account.

In the container list, container names are sorted in ascending order based on ASCII code.

.. note::

   OBS (compatible with OpenStack Swift) employs a mechanism that automatically deletes accounts and their data in the background. There is no account deletion status corresponding to OpenStack Swift.

   The specific differences are as follows:

   Account metadata does not include the X-Account-Status.

   Showing account details does not involve the 410 Gone return code.

-  :ref:`Request <obs_03_0017>`
-  :ref:`Response <obs_03_0018>`
-  :ref:`Examples <obs_03_0019>`

.. toctree::
   :maxdepth: 1
   :hidden: 

   request
   response
   examples
