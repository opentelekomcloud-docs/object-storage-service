:original_name: obs_03_100528.html

.. _obs_03_100528:

What Is the Best Practice to Delete Objects and Deal with Versioning?
=====================================================================

In OBS, buckets are containers, with their names acting as globally unique identifiers, so two buckets in the OTC can't share the same name. The objects stored in these buckets however are identified by their unique IDs, which allows overloading objects with newer versions, under the same name, if versioning has been enabled for the bucket. (For more information, see :ref:`Versioning <en-us_topic_0045853849>` and :ref:`How Do I Use Versioning? <obs_faq_0800>`)

There is no limit to the number of versions, however from experiences of running versioning in a productive environment we found that listing versioned objects can easily run into difficulties. To avoid performance issues we don't recommend to list all objects in buckets with versioning either enabled or suspended. As the OTC console depends on listing all objects as well, it is also highly recommended not to rely on it in managing versioned objects.

Some tools like OBS Browser currently also can't handle versioned objects and will only list and manipulate the current version of the object.

Right now the recommended method for managing versioned objects is using an SDK or API directly (for more information see `Request Syntax for Multi-Version Objects in the Listing Objects API <https://docs.otc.t-systems.com/object-storage-service/api-ref/apis/operations_on_buckets/listing_objects_in_a_bucket.html#request-syntax-for-multi-version-objects>`__ and `Versioning for the Downloading an Object API <https://docs.otc.t-systems.com/object-storage-service/api-ref/apis/operations_on_objects/downloading_an_object.html#obs-04-0083>`__).

Typical Use Cases
-----------------

A typical use case is recovering the latest historical version of an object by deleting the delete marker version. This operation is recommended to be performed either through API or SDK. This is a single operation based on the specific object ID. For more information see `Versioning for the Deleting an Object API <https://docs.otc.t-systems.com/object-storage-service/api-ref/apis/operations_on_objects/deleting_an_object.html#versioning>`__.

Another typical use case is deleting all versions of objects with a specific name (or even all objects from a bucket to delete the bucket). This operation however would need to be performed on multiple objects and thus can again run into difficulties based on the number of objects. It is recommended in this case to limit the batches of objects the operation runs on at the time and also the number of concurrency. For more information see `Deleting Objects <https://docs.otc.t-systems.com/object-storage-service/api-ref/apis/operations_on_objects/deleting_objects.html>`__.

Configuring Lifecycle Rule for Mass Deleting Objects
----------------------------------------------------

The best practice for mass deleting objects (regardless of versioning) is using a lifecycle rule.

To conveniently delete a large number of objects, you can configure a lifecycle rule (see :ref:`Configuring a Lifecycle Rule <obs_03_0335>`) that will remove these objects after the specified number of days - the rule will be applied either to some of the objects based on a prefix or to all objects in the bucket. In order to configure such rule:

#. In the bucket list, click the bucket you want to operate. The **Overview** page of the bucket is displayed.
#. In the **Basic Configurations** area, click **Lifecycle Rules**. The **Lifecycle Rules** page is displayed.
#. Click **Create**. The **Create Lifecycle Rule** window is displayed.
#. In the **Basic Information** section:

   -  Specify **Rule Name**.
   -  Specify **Prefix** if necessary (for example if you want to only delete files from some specific folder called **folder_name**, you can specify **folder_name/** as a prefix).
   -  If you want to delete all files from the bucket, select **Bucket** in the **Applies To** switch.

#. In the **Current Version** (for the current version of the multi-version object) and **Historical Version** (for all other versions of the object) sections:

   -  Select **Configure now** in the **Expiration Time** switch.
   -  Enter the number of days after which a file should be removed in the **Delete After** edit field (minimum value: **1** day).

#. Click **OK**.
