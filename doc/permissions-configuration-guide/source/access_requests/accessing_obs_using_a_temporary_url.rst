:original_name: obs_40_0009.html

.. _obs_40_0009:

Accessing OBS Using a Temporary URL
===================================

You can share a temporary URL to allow other users to access OBS to create buckets and upload and download objects. This section describes how to share a temporary URL to allow other users to temporarily access objects.

Sharing Objects
---------------

You can share a temporary URL to allow other users to access objects (files or folders) for only a specified period of time.

**Sharing a file**

All URLs generated during file sharing are temporary and remain valid for a specified period of time.

A temporary URL uses V4 temporarily authorized requests. The following is an example:

.. code-block::

   https://bucketname.oss.regionid.example.region.com/objectname?X-Amz-Algorithm=xxx&X-Amz-Credential=xxx&X-Amz-Date=xxx&X-Amz-Expires=900&X-Amz-Signature=xxx&X-Amz-SignedHeaders=xxx&response-content-disposition=xxx

For details about the temporary authentication and parameters, see `V4 Temporarily Authorized Request <https://docs.otc.t-systems.com/en-us/api_obs/obs/en-us_topic_0125560420.html>`__ in the *Object Storage Service API Reference*. A temporary URL also contains the **response-content-disposition** parameter that defines whether an object is to be downloaded or previewed in a browser. The browser obtains the value of **response-content-disposition** based on the **Content-Type** of the shared object.

After you share an object by choosing **More** > **Copy Object URL** on OBS Console, the system will generate a URL that contains the temporary authentication information, valid for 900 seconds since its generation by default. Each time you click **Copy Object URL**, OBS will obtain the authentication information again to generate a new sharing URL whose validity period is reset.

Limitations and Constraints
---------------------------

-  The validity period of files shared through OBS Console is fixed at 900s. If you want to allow permanent access to a file, you can configure `a bucket policy or an object policy <https://docs.otc.t-systems.com/usermanual/obs/en-us_topic_0045853745.html>`__.
-  Only buckets of version 3.0 support file and folder sharing. You can view the bucket version in the **Basic Information** area on the **Overview** page of a bucket.
-  To share a cold object, restore it first.
