:original_name: obs_03_0062.html

.. _obs_03_0062:

Copy Object
===========

You can copy an object to a new object with the same name.

You can copy objects using PUT or COPY:

-  Use PUT method and add the **X-Copy-From** request header.
-  Use the COPY method.

Both methods have the same effect.

The COPY operation always creates a new object. If you use this operation on an existing object, replace the existing object and metadata.

If you use this operation to copy a manifest object, the new object is a normal object and not a copy of the manifest. Instead it is a concatenation of all the segment objects. This means that you cannot copy objects larger than 5 GB.

-  :ref:`Request <obs_03_0063>`
-  :ref:`Response <obs_03_0064>`
-  :ref:`Examples <obs_03_0065>`

.. toctree::
   :maxdepth: 1
   :hidden: 

   request
   response
   examples
