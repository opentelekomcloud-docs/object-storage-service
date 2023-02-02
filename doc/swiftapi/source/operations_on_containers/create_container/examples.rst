:original_name: obs_03_0036.html

.. _obs_03_0036:

Examples
========

Create Container
----------------

Create a container named **marktwain**:

.. code-block:: text

   curl -i -H "X-Auth-token:caf12eeaae6b45b1afcb7ad1d6588a4f" "http://172.28.5.30:80/v1/AUTH_0ce042a9be6140769b12c1001d41bcf9/marktwain" -X PUT

.. code-block::

   HTTP/1.1 201 Created
   X-Trans-Id: tx568a5d33add18d5f73757-b6dc185e91
   Content-Type: text/html;charset=UTF-8
   Date: Fri, 18 Sep 2015 01:58:51 GMT
   Content-Length: 0

Create Existing Container
-------------------------

Container **marktwain** exists. Create it again.

.. code-block:: text

   curl -i -H "X-Auth-token:caf12eeaae6b45b1afcb7ad1d6588a4f" "http://172.28.5.30:80/v1/AUTH_0ce042a9be6140769b12c1001d41bcf9/marktwain" -X PUT

.. code-block::

   HTTP/1.1 202 Accepted
   X-Trans-Id: txed4fe8ffb3219cd0db230-cbe125775d
   Content-Type: text/html;charset=UTF-8
   Date: Fri, 18 Sep 2015 01:59:01 GMT
   Content-Length: 76
   <html><h1>Accepted</h1><p>The request is accepted for processing.</p></html>

Create Container (with a Read ACL Specified)
--------------------------------------------

Create a container and specify the **X-Container-Read** metadata.

.. code-block:: text

   curl -i http://172.28.54.10:80/v1/AUTH_4b34aa268d8c45879cf4da16443d3f95/ruanman -H"x-auth-token:c1f21a34cce442efbd4957018263cc2c" -H"x-container-read:.r:*" -X PUT

.. code-block::

   HTTP/1.1 201 Created
   X-Trans-Id: tx000001513752eba4370a5-4f8cd5e885
   Content-Length: 0
   Content-Type: text/html;charset=UTF-8
   Date: Tue, 24 Nov 2015 02:29:24 GMT
