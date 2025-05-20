:original_name: obs_03_0318.html

.. _obs_03_0318:

Searching for an Object or Folder
=================================

On OBS Console, you can search for files or folders by storage class, last modification time, or object name prefix.

Procedure
---------

#. In the bucket list, click the bucket you want to operate to go to the **Objects** page.

#. **Search for objects by storage class**:

   a. Click the search box above the object list and choose **Storage Class** from the drop-down list.
   b. Select your desired option, or enter a keyword and then select the option displayed.
   c. Click **OK**. The searched objects are displayed in the object list.

   Suppose you want to search for objects in the Standard storage class. Click the search box and choose **Storage Class** from the drop-down list. Then, select **Standard**, or enter **standard** in the search box and select the option displayed. After that, click **OK**. Objects in the Standard storage class will be displayed in the object list.


   .. figure:: /_static/images/en-us_image_0000002112799428.png
      :alt: **Figure 1** Searching for objects by storage class

      **Figure 1** Searching for objects by storage class

#. **Search for objects by last modification time**:

   a. Click the search box above the object list and choose **Last Modified** from the drop-down list.
   b. Select a start date or an end date.

      .. note::

         The time can be accurate to seconds.

         Either start date or end date must be specified.

   c. Click **OK**. The objects last modified within the specified time range are displayed in the object list.

   Suppose you want to search for objects uploaded from 13:00:00 on October 10, 2023. Click the search box and choose **Last Modified** from the drop-down list. Then, click the text box for **Start Date**, specify the time (13:00:00 on October 10, 2023) and click **OK**. Objects uploaded from 13:00:00 on October 10, 2023 will be displayed in the object list.


   .. figure:: /_static/images/en-us_image_0000002112961384.png
      :alt: **Figure 2** Searching for objects by last modification time

      **Figure 2** Searching for objects by last modification time

#. **Search for objects by object name prefix**:

   a. Click the search box above the object list and choose **Object Name Prefix** from the drop-down list.
   b. In the search box, enter the name prefix of the files or folders you want to search for.

      .. note::

         The object name prefix is case sensitive.

   c. Press **Enter**. The searched objects are displayed in the object list.

   Suppose you want to search for objects whose prefix is **te**. Click the search box and choose **Object Name Prefix** from the drop-down list box. Then, enter **te**, and press **Enter**. Objects with the **te** prefix will be displayed in the object list.


   .. figure:: /_static/images/en-us_image_0000002112804116.png
      :alt: **Figure 3** Searching for objects by object name prefix

      **Figure 3** Searching for objects by object name prefix

   .. note::

      To search for objects within a folder, use either of the following methods:

      -  In the root directory, click the search box above the object list and choose **Object Name Prefix** from the drop-down list. Then, enter *Folder path*\ **/**\ *Prefix* in the search box. For example, if you enter **abc/123/example**, all files and folders with the **example** prefix in the **abc/123** folder will be displayed.
      -  Open the folder, and enter the object name prefix in the search box. For example, after you open the **abc/123** folder and enter **example** in the search box, all files and folders with the **example** prefix in the **abc/123** folder will be displayed.

#. Search for objects by entering a storage class keyword or an object name prefix in the search box above the object list.

   -  Enter a storage class keyword and click a required criterion from those that are automatically displayed. All matched objects will be displayed in the object list.

      Suppose you enter **stan** in the search box. The system will then display the **Standard** storage class. After you click this storage class, all objects whose storage class is Standard will be displayed in the object list.


      .. figure:: /_static/images/en-us_image_0000002148446593.png
         :alt: **Figure 4** Searching for objects by storage class keyword

         **Figure 4** Searching for objects by storage class keyword

   -  Enter an object name prefix and press **Enter**. All files and folders with the specified prefix will be displayed in the object list.

      Suppose you want to search for objects with the **te** prefix. Enter **te** in the search box and press **Enter**. Then, all objects with the **te** prefix will be displayed in the object list.


      .. figure:: /_static/images/en-us_image_0000002148572577.png
         :alt: **Figure 5** Searching for objects by object name prefix

         **Figure 5** Searching for objects by object name prefix

   .. note::

      You can search for objects based on a combination of different filter criteria.

      -  If the filter criteria are of different types, they are in intersection logic. For example, if you select storage class **Standard** and object name prefix **te** as two criteria, objects whose storage class is Standard and prefix is **te** will be displayed in the object list.
      -  If the filter criteria are of the same type, they are in union logic. For example, if you select storage class **Standard** and then **Warm** as two criteria, objects in both Standard and Warm storage classes will be displayed in the object list.

Related Operations
------------------

In the object list, click |image1| next to the size or last modified time to sort objects.

.. |image1| image:: /_static/images/en-us_image_0000001627960406.png
