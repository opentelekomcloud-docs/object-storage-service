:original_name: obs_03_0053.html

.. _obs_03_0053:

Operations on Objects
=====================

The requests that are sent by users to OBS (compatible with OpenStack Swift) must comply with REST specifications and contain required header parameters. If a request is successfully processed, OBS (compatible with OpenStack Swift) returns a success response. If the request cannot be processed, OBS (compatible with OpenStack Swift) returns a message that contains the cause of the error. This chapter describes REST operations on objects. Authentication is implemented based on IAM.

.. note::

   For OBS APIs, if the value of **Content-Length** in a request is not a valid numerical string, OBS (compatible with OpenStack Swift) will attempt to parse the content text and use it as the value of **Content-Length**. For example, **-H"Content-Length:26abc"** is equivalent to **-H"Content-Length:26"**. OpenStack Swift, however, returns the error code 400 (Bad Request).

-  :ref:`Get Object Content and Metadata <obs_03_0054>`
-  :ref:`Create or Replace Object <obs_03_0058>`
-  :ref:`Copy Object <obs_03_0062>`
-  :ref:`Delete Object <obs_03_0066>`
-  :ref:`Show Object Metadata <obs_03_0070>`
-  :ref:`Create/Update/Delete Object Metadata <obs_03_0074>`

.. toctree::
   :maxdepth: 1
   :hidden: 

   get_object_content_and_metadata/index
   create_or_replace_object/index
   copy_object/index
   delete_object/index
   show_object_metadata/index
   create_update_delete_object_metadata/index
