:original_name: obs_03_0031.html

.. _obs_03_0031:

User-Defined Domain Name Binding Overview
=========================================

Application Scenario
--------------------

After a file is uploaded to a bucket, you can access this file using the bucket's domain name by default. If you want to access the file using a user-defined domain name, you can bind this domain name to the bucket.

Assuming that you have a domain name **www.example.com** and there is an image **image.png** in an OBS bucket, after you bind **www.example.com** to the bucket, you can use **http://www.example.com/image.png** to access image **image.png**. The steps below describe the configurations:

#. Create a bucket on OBS and upload file **image.png** to the bucket.
#. On OBS Console, bind **www.example.com** to the created bucket.
#. On the DNS server, add a CNAME record and map **www.example.com** to the domain name of the bucket.
#. Send a request for image **image.png**. After the request for **http://www.example.com/image.png** reaches OBS, OBS finds the mapping between the **www.example.com** and the bucket's domain name, and redirects it to the **image.png** file stored in the bucket. That is, a request for **http://www.example.com/image.png** actually accesses **http://**\ *Bucket domain name*\ **/image.png**.

Limitations and Constraints
---------------------------

#. Only buckets whose version is 3.0 support user-defined domain name binding. The version number of a bucket is displayed in the **Basic Information** area.
#. Currently, user domain names bound to OBS only allow access requests over HTTP.
#. A user-defined domain name can be bound to only one bucket.
#. Currently, the suffix of a user-defined domain name can contain 2 to 6 uppercase and lowercase letters.
