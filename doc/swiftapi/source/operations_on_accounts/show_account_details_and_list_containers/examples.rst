:original_name: obs_03_0019.html

.. _obs_03_0019:

Examples
========

Show Account Details and List Containers (Asking for a Plain Response)
----------------------------------------------------------------------

Show account details and list containers. Do not set a query parameter. Use the default plain response format.

.. code-block:: text

   curl -i -H "X-auth-token:b8b574e33b0a4f74a1961bed1b4784b8" "http://172.28.5.30:80/v1/AUTH_0ce042a9be6140769b12c1001d41bcf9" -X GET

.. code-block::

   HTTP/1.1 200 OK
   X-Trans-Id: tx19cbb9377b2eb8a164ac8-c40e979e9b
   Accept-Ranges: bytes
   Content-Type: text/plain;charset=UTF-8
   Date: Wed, 16 Sep 2015 07:10:18 GMT
   X-Account-Bytes-Used: 0
   X-Account-Container-Count: 3
   X-Account-Object-Count: 0
   X-Account-Project-Domain-Id: default
   X-Timestamp: 1442371465.946
   Content-Length: 23

   [23 Byte data content]

Show Account Details and List Containers (Asking for an XML Response)
---------------------------------------------------------------------

Show account details and list containers. Use the **prefix=abc** query parameter, and set the response format to **xml**.

.. code-block:: text

   curl -i -H "X-auth-token:b8b574e33b0a4f74a1961bed1b4784b8" "http://172.28.5.30:80/v1/AUTH_0ce042a9be6140769b12c1001d41bcf9?format=xml&prefix=abc"      -X GET

.. code-block::

   HTTP/1.1 200 OK
   X-Trans-Id: tx200c074b35f50910061e7-067ab2f1d4
   Accept-Ranges: bytes
   Content-Type: application/xml;charset=UTF-8
   Date: Wed, 16 Sep 2015 07:12:09 GMT
   X-Account-Bytes-Used: 0
   X-Account-Container-Count: 3
   X-Account-Object-Count: 0
   X-Account-Project-Domain-Id: default
   X-timestamp: 1442371465.946
   Content-Length: 256

   <?xml version="1.0" encoding="UTF-8"?>
   <account name="AUTH_0ce042a9be6140769b12c1001d41bcf9">
   <container><name>abcc122</name><count>0</count><bytes>0</bytes></container>
   <container><name>abcd123</name><count>0</count><bytes>0</bytes></container>
   </account>
