:original_name: obs_faq_0139.html

.. _obs_faq_0139:

Lifecyle Policy as Best Practice to Delete Objects and to Deal with Versioning
====================================

In OBS buckets are containers, with their names acting as globally unique identifiers, thus two buckets in the OTC can't share the same name.
The objects stored in these buckets however are identified by their unique IDs, which allows overloading objects with newer versions, under the same name, if versioning has been enabled for the bucket.
(for more information about versioning see: https://docs.otc.t-systems.com/object-storage-service/umn/obs_console_operation_guide/versioning/index.html, https://docs.otc.t-systems.com/object-storage-service/umn/faqs/how_do_i_use_versioning/index.html#obs-faq-0800).
 
There is no limit to the number of versions, however from experiences of running versioning in a productive environment we found that listing versioned objects can easily run into difficulties.
To avoid performance issues we don't recommend to list all objects in buckets with versioning either enabled or suspended.
As the OTC console depends on listing all objects as well, it is also highly recommended not to rely on it in managing versioned objects.
 
Some tools like OBS browser currently also can't handle versioned objects and will only list and manipulate the current version of the object.

Right now the recommended method for managing versioned objects is using SDK or API directly.

A typical use case is recovering the latest historical version of an object by deleting the deletemarker version. This operation is recommended to be performed either through API or SDK. This is a single operation based on the specific object ID.
Another typical use case is deleting all versions of objects with a specific name (or even all objects from a bucket to delete the bucket). This operation however would by its nature need to be performed on multiple objects and thus can again run into difficulties based on the number of objects. It is recommended in this case to limit the batches of objects the operation runs on at the time and also the number of concurrency.

But best practice for mass deleting objects (regardless of versioning) is using lifecylce policy.
