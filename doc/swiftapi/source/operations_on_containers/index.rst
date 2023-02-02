:original_name: obs_03_0028.html

.. _obs_03_0028:

Operations on Containers
========================

The requests that are sent by users to OBS must comply with REST specifications and contain required header parameters. If a request is successfully processed, OBS (compatible with OpenStack Swift) returns a success response. If the request cannot be processed, OBS (compatible with OpenStack Swift) returns a message that contains the cause of the error. This chapter describes REST operations on containers. Authentication is implemented based on IAM.

-  :ref:`Show Container Details and List Objects <obs_03_0029>`
-  :ref:`Create Container <obs_03_0033>`
-  :ref:`Delete Container <obs_03_0037>`
-  :ref:`Create/Update/Delete Container Metadata <obs_03_0041>`
-  :ref:`Show Container Metadata <obs_03_0045>`
-  :ref:`Batch Delete Containers <obs_03_0049>`

.. toctree::
   :maxdepth: 1
   :hidden: 

   show_container_details_and_list_objects/index
   create_container/index
   delete_container/index
   create_update_delete_container_metadata/index
   show_container_metadata/index
   batch_delete_containers/index
