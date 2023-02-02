:original_name: obs_03_0009.html

.. _obs_03_0009:

Naming Rules
============

If a request contains a container name or an object name, OBS (compatible with OpenStack Swift) starts to process the request only after checking that the name conforms to the specified naming rules.

Account Naming Rules
--------------------

Account names must be:

-  Globally unique.
-  Strings of 1 to 256 characters.

.. note::

   OBS (compatible with OpenStack Swift) uses the IDs of tenants created in the IAM system as account names.

Container Naming Rules
----------------------

Container names must:

-  Be strings of 1 to 256 characters.
-  Contain only case-sensitive letters, digits, periods (.), underscores (_), and hyphens (-).
-  Use UTF-8 encoding.

.. note::

   To ensure system security, in a container name, the types of characters that are prohibited by OBS (compatible with OpenStack Swift) are more than those prohibited by OpenStack Swift.

.. _obs_03_0009__section23579102:

Object Naming Rules
-------------------

A key specifies the name of an object, and each object in a container must have a unique object key. Object names must:

-  Be strings of 1 to 1024 characters, but they can start with any character.
-  Use UTF-8 encoding.
-  Not contain spaces, question marks (?), or double quotation marks (").

Rules About Custom Metadata
---------------------------

The following rules apply to custom metadata of accounts, containers, and objects:

-  The value of a custom metadata item cannot exceed 256 bytes.
-  The name of a custom metadata item cannot exceed 128 bytes.
-  All custom metadata items (including their names and values) cannot exceed 4,096 bytes.
-  There can be no more than 90 custom metadata items.
-  The name of a custom metadata item can contain only letters, digits, and ASCII characters.
-  Custom metadata values can use UTF-8 encoding.
-  Tab or space characters appearing after the name of a custom metadata item are deleted by default.

.. note::

   In OpenStack Swift, tab and space characters before and after the name of a custom metadata item are not deleted.
