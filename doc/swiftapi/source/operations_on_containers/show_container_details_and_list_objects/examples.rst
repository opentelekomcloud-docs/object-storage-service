:original_name: obs_03_0032.html

.. _obs_03_0032:

Examples
========

Show Container Details: Plain Format
------------------------------------

Show metadata of the **testcontainer** container and list objects. Do not set a query parameter. Use the default plain response format.

.. code-block:: text

   curl -i http://172.28.54.10:80/v1/AUTH_4b34aa268d8c45879cf4da16443d3f95/testcontainer -H "x-auth-token:c1f21a34cce442efbd4957018263cc2c" -X GET

.. code-block::

   HTTP/1.1 200 OK
   X-Trans-Id: tx0000015133a73737370a1-35e31d5be7
   Accept-Ranges: bytes
   Content-Length: 10
   Content-Type: text/plain;charset=UTF-8
   Date: Mon, 23 Nov 2015 09:22:58 GMT
   X-Container-Bytes-Used: 5027
   X-Container-Object-Count: 2
   X-Timestamp: 1448270495.79460

   [10 Byte data content]

Show Container Details: JSON Format
-----------------------------------

Show metadata of the **testcontainer** container and list objects. Specify the JSON response format.

.. code-block:: text

   curl -i http://172.28.54.10:80/v1/AUTH_4b34aa268d8c45879cf4da16443d3f95/testcontainer?format=json -H "x-auth-token:c1f21a34cce442efbd4957018263cc2c" -X GET

A JSON response is returned. The response body contains object information such as **hash**, **bytes**, and **content_type**.

.. code-block::

   HTTP/1.1 200 OK
   X-Trans-Id: tx0000015133aa2422370a1-13b8629ff1
   Accept-Ranges: bytes
   Content-Length: 335
   Content-Type: application/json;charset=UTF-8
   Date: Mon, 23 Nov 2015 09:26:09 GMT
   X-Container-Bytes-Used: 5027
   X-Container-Object-Count: 2
   X-Timestamp: 1448270495.79460

   [
       {
           "hash": "0481164fe6931fb86ca4d8e8b3689efb",
           "bytes": 4337,
           "content_type": "application/octet-stream",
           "last_modified": "2015-11-23T09:22:22.859650",
           "name": "jack"
       },
       {
           "hash": "1e5d213baf0069e26805f5d4efc900fe",
           "bytes": 690,
           "content_type": "application/octet-stream",
           "last_modified": "2015-11-23T09:22:44.748920",
           "name": "rose"
       }
   ]
