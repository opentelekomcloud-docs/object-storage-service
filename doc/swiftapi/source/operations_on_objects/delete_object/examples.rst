:original_name: obs_03_0069.html

.. _obs_03_0069:

Examples
========

Delete Object
-------------

Delete the **goodbye** object from the **janeausten** container:

.. code-block:: text

   curl -i http://172.28.54.12:80/v1/AUTH_4b34aa268d8c45879cf4da16443d3f95/janeausten/goodbye -H "X-Auth-Token:74565091b56b4783818430cecb283e7f"  -X DELETE

.. code-block::

   HTTP/1.1 204 No Content
   X-Trans-Id: tx000001513cb0b434370c1-82374dd941
   Content-Length: 0
   Content-Type: text/html;charset=UTF-8
   Date: Wed, 25 Nov 2015 03:29:52 GMT

Delete Non-Existing Object
--------------------------

Delete the non-existing **goodbye** object from the **janeausten** container:

.. code-block:: text

   curl -i http://172.28.54.12:80/v1/AUTH_4b34aa268d8c45879cf4da16443d3f95/janeausten/goodbye -H "X-Auth-Token:74565091b56b4783818430cecb283e7f"  -X DELETE

.. code-block::

   HTTP/1.1 404 Not Found
   X-Trans-Id: tx000001513cb1e9c6370c1-4c3eaf057d
   Content-Type: text/html;charset=UTF-8
   Date: Wed, 25 Nov 2015 03:31:11 GMT
   Content-Length: 70

   <html><h1>Not Found</h1><p>The resource could not be found.</p></html>
