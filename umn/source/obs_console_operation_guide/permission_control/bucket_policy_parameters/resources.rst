:original_name: obs_03_0118.html

.. _obs_03_0118:

Resources
=========

The resource can be the current entire bucket, an object, or a set of objects in the bucket.

Resources can be specified in either of the following ways:

-  **Include**: Indicates that the policy takes effect only on the specified OBS resources.
-  **Exclude**: Indicates that the bucket policy takes effect on all OBS resources except the specified ones.

Specifying Bucket Resources
---------------------------

To specify the current bucket as the resource, keep the resource text box empty. When configuring actions for the policy, select bucket related actions.

Specifying Object Resources
---------------------------

When objects in the bucket are specified as the resources, actions configured in the bucket policy must be object related actions. The following are examples of how to specify objects as resources.

-  For an object, enter the object name (including its folder name if any). For example, if the specified resource is the **example.jpg** file in the **imgs-folder** folder in the bucket, enter the following content in the resource text box:

   imgs-folder/example.jpg

-  For an object set, the wildcard asterisk (*) should be used. The asterisk \* indicates an empty string or any combination of multiple characters. The format rules are as follows:

   -  Use only one asterisk (*) to indicate all objects in a bucket.

   -  Use *Object name prefix*\ \* to indicate objects starting with this prefix in a bucket. For example,

      imgs\*

   -  Use \*\ *Object name suffix* to indicate objects ending with this suffix in a bucket. For example,

      \*.jpg

.. note::

   Use commas (,) to separate one object (or object set) from another.
