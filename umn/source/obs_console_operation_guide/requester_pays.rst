:original_name: obs_03_0350.html

.. _obs_03_0350:

Requester Pays
==============

Scenarios
---------

The requester-pays configuration allows the requester to pay for data transfer and API calls associated with accessing the requested OBS resources, while the bucket owner only pays for data storage. If your bucket is the source for large-scale data sharing, you can enable requester-pays for the bucket, so that the requester pays for data access in the bucket. Otherwise, you, the bucket owner, will pay for all costs associated with the bucket.

Limitations and Constraints
---------------------------

-  Only buckets of version 3.0 support the requester-pays function.

-  A requester-pays bucket does not allow access by anonymous users.

-  The **x-obs-request-payer: requester** header must be included in the request accessing a requester-pays bucket, indicating that the requester agrees to pay for the request and associated data transfer. Without this header, the identity authentication fails, and error 403 (Forbidden) is returned. The response returned by the server includes the **x-obs-request-charged: requester** header, indicating the requester is billed for this request.

   **Sample request for downloading an object by a requester**

   .. code-block:: text

      GET /ObjectName HTTP/1.1
      Host: bucketname.obs.region.example.com
      Date: date
      Authorization: authorization
      x-obs-request-payer: requester

   **Sample response**

   ::

      HTTP/1.1 status_code
      x-obs-request-charged: requester
      Content-Type: type
      Date: date
      Content-Length: length

      <Object Content>

-  If the bucket owner or an IAM user under the same account as the bucket owner accesses a requester-pays bucket, the **x-obs-request-payer: requester** header is not required. In such case, no matter whether this header is included in the request, the response does not include the header.

Configuring Requester Pays
--------------------------

#. In the bucket list, click the bucket you want to operate. The **Overview** page is displayed.

#. In the **Basic Configurations** area, click **Requester Pays**. The **Requester Pays** dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0250427066.png
      :alt: **Figure 1** Requester pays

      **Figure 1** Requester pays

#. Select **Enable**.

   -  **Enable**: The requester is charged for requests and data transfer associated with accessing the bucket, while the bucket owner is charged for data storage in the bucket.
   -  **Disable**: The bucket owner is charged for all costs associated with the bucket.

#. Click **OK**.
