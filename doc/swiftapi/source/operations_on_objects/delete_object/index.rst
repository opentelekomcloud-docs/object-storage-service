:original_name: obs_03_0066.html

.. _obs_03_0066:

Delete Object
=============

The **DELETE** command is used to delete a specified object. After an object is deleted, any subsequent GET, HEAD, POST, or DELETE operations return a **404 Not Found** error code.

For static large objects, you can add the **multipart-manifest=delete** query parameter. This operation deletes the segment objects and if all deletions succeed, this operation deletes the manifest object.

Normally the DELETE operation does not return a response body. However, with the **multipart-manifest=delete** query parameter, the response body contains a list of manifest and segment objects and the status of their delete operations.

-  :ref:`Request <obs_03_0067>`
-  :ref:`Response <obs_03_0068>`
-  :ref:`Examples <obs_03_0069>`

.. toctree::
   :maxdepth: 1
   :hidden: 

   request
   response
   examples
