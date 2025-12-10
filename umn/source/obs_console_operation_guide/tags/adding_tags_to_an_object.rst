:original_name: obs_41_0054.html

.. _obs_41_0054:

Adding Tags to an Object
========================

Tag Rules
---------

Tags can be added to objects to categorize storage. You can add tags to new objects when you upload them or add them to existing objects.

An object tag is a key-value pair. To use tags, follow the rules below:

-  An object can have up to 10 tags.
-  Tag key constraints:

   -  If there are multiple tags specified for an object, each tag key must be unique.
   -  A tag key must contain 1 to 36 characters and be case sensitive.
   -  A tag key can't start or end with a space or contain the following characters: ``,/|<>=*\``

-  Tag value constraints:

   -  A tag value can contain 0 to 43 characters and must be case sensitive.
   -  A tag value can't contain the following characters: ``,/|<>=*\``

Important Notes
---------------

-  To read or write object tags, you must have required permissions. Such permissions can be granted using bucket policies. By default, only the object owner can read or write the object's tags.
-  During cross-region replication, tags of source objects are not copied.
-  Tags cannot be added to files in parallel file systems.

Scenarios
---------

**Specifying object tags in a lifecycle rule**

In a lifecycle configuration, you can specify filter conditions to identify the objects which the lifecycle rule applies to. A filter can be defined based on an object name prefix, an object tag, or both. The following rule deletes objects with the **texta/** prefix and with tags **key1/value1** and **key2/value2** 120 days after their creation.

.. code-block::

   <LifecycleConfiguration>
       <Rule>
           <ID>sample-rule</ID>
           <Filter>
               <And>
                   <Prefix>texta/</Prefix>
                   <Tag>
                       <Key>key1</Key>
                       <Value>value1</Value>
                   </Tag>
                   <Tag>
                       <Key>key2</Key>
                       <Value>value2</Value>
                   </Tag>
               </And>
           </Filter>
           <Status>Enabled</Status>
           <Expiration>
               <Days>120</Days>
           </Expiration>
       </Rule>
   </LifecycleConfiguration>

Configuring Object Tags
-----------------------

On OBS Console, you can add tags to an object when uploading it (see :ref:`Procedure <en-us_topic_0045853663__section64292661113931>`). You can also add tags to an existing object, as described in the following:

#. In the bucket list, click the bucket you want to operate. The **Objects** page is displayed.
#. In the object list, click the name of the object you want to add tags to.
#. Click the **Tags** tab. Then, click **Add Tag** in the upper left corner.
#. In the **Add Tag** dialog box, enter a tag key and a tag value.

   .. table:: **Table 1** Parameter description

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                            |
      +===================================+========================================================================================================================+
      | Tag key                           | The key of an object must be unique and cannot be left blank. You can customize a tag or choose one predefined on TMS. |
      |                                   |                                                                                                                        |
      |                                   | -  Tag key constraints:                                                                                                |
      |                                   |                                                                                                                        |
      |                                   |    -  If there are multiple tags specified for an object, each tag key must be unique.                                 |
      |                                   |    -  A tag key must contain 1 to 36 characters and be case sensitive.                                                 |
      |                                   |    -  A tag key can't start or end with a space or contain the following characters: ``,/|<>=*\``                      |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------+
      | Tag value                         | A tag value can be repetitive or left blank.                                                                           |
      |                                   |                                                                                                                        |
      |                                   | -  Tag value constraints:                                                                                              |
      |                                   |                                                                                                                        |
      |                                   |    -  A tag value can contain 0 to 43 characters and must be case sensitive.                                           |
      |                                   |    -  A tag value can't contain the following characters: ``,/|<>=*\``                                                 |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

Related Operations
------------------

In the tag list, click **Edit** to change the tag value or click **Delete** to remove the tag.
