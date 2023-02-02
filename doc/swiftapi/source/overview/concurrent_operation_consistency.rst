:original_name: obs_03_0004.html

.. _obs_03_0004:

Concurrent Operation Consistency
================================

After a success message is returned in response to a client's write or deletion request, the client can obtain the latest data. If the client that initiated a write request times out while waiting for a response, or the server returns HTTP response status code 500 or 503, the subsequent read operations may fail. If such an error occurs, check whether the data was successfully uploaded to the server. If the data was not uploaded successfully, upload it again.

If multiple clients simultaneously upload, query, or delete the same object or container, these operations may reach the system at different points in time and experience different internal processing latency periods, and different results may be returned. For example, if multiple clients simultaneously upload the same object, the latest upload request received by the system will replace the previous one. If you want to prevent an object from being accessed in parallel, you must use a lock mechanism in upper-layer applications.

Concurrent Operation Examples
-----------------------------

1. When client 1 is uploading an object v1, client 2 is uploading an object v2 with the same name. After the successful uploads, both client 1 and client 2 can access the latest object data v2, as shown in :ref:`Figure 1 <obs_03_0004__fig119911824133416>`.

.. _obs_03_0004__fig119911824133416:

.. figure:: /_static/images/en-us_image_0138437473.png
   :alt: **Figure 1** Concurrent upload of the same object

   **Figure 1** Concurrent upload of the same object

2. When client 1 is uploading an object v1 and object metadata is not written yet, client 2 deletes an object with the same name. In this scenario, the upload operation of client 1 is still successful, and both client 1 and client 2 can access data object v1, as shown in :ref:`Figure 2 <obs_03_0004__fig18399247153517>`.

.. _obs_03_0004__fig18399247153517:

.. figure:: /_static/images/en-us_image_0138437574.png
   :alt: **Figure 2** Concurrent upload and deletion of the same object (1)

   **Figure 2** Concurrent upload and deletion of the same object (1)

3. When client 1 has successfully uploaded an object v1 and object metadata is still being written, client 2 deletes an object with the same name. In this scenario, the upload operation of client 1 is still successful. However, when client 1 and client 2 attempt to download Object1, they may be able to access data object v1, or an error may be returned indicating that the object does not exist, as shown in :ref:`Figure 3 <obs_03_0004__fig1972203713617>`.

.. _obs_03_0004__fig1972203713617:

.. figure:: /_static/images/en-us_image_0138437668.png
   :alt: **Figure 3** Concurrent upload and deletion of the same object (2)

   **Figure 3** Concurrent upload and deletion of the same object (2)

4. When client 1 is downloading an object, client 2 deletes an object with the same name. In this scenario, client 1 may have downloaded a full copy or only part of the object data. After a deletion success message is returned to client2, an attempt to download the object will fail, and an error will be returned indicating that the object does not exist, as shown in :ref:`Figure 4 <obs_03_0004__fig7637151312371>`.

.. _obs_03_0004__fig7637151312371:

.. figure:: /_static/images/en-us_image_0138437619.png
   :alt: **Figure 4** Concurrent download and deletion of the same object

   **Figure 4** Concurrent download and deletion of the same object

5. When client 1 is downloading an object, client 2 is updating an object with the same name. In this scenario, client 1 may have downloaded a full copy or only part of the object data. After an update success message is returned to client 2, an attempt to download the object will succeed, and the latest data will be returned, as shown in :ref:`Figure 5 <obs_03_0004__fig1934764718375>`.

.. _obs_03_0004__fig1934764718375:

.. figure:: /_static/images/en-us_image_0138437827.png
   :alt: **Figure 5** Concurrent download and update of the same object

   **Figure 5** Concurrent download and update of the same object
