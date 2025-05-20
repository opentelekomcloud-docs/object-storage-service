:original_name: obs_03_0338.html

.. _obs_03_0338:

Using a User-Defined Domain Name to Configure Static Website Hosting
====================================================================

OBS allows you to access static websites hosted by OBS using user-defined domain names. This section uses a specific scenario as an example to describe how to use a user-defined domain name to configure static website hosting. For a basic understanding of the concepts and operations about the static website hosting on OBS, see :ref:`Configuring Static Website Hosting <en-us_topic_0045853755>`.

Scenario
--------

Company **A** has a large number of files to archive but it does not want to put the time and effort into its storage resources. Therefore, the company subscribes to OBS for hosting static websites and expects that the usernames under the company account can access the static resources through a user-defined domain name. See :ref:`Figure 1 <obs_03_0338__fig4961082014460>`.

.. _obs_03_0338__fig4961082014460:

.. figure:: /_static/images/en-us_image_0129288906.png
   :alt: **Figure 1** Using a user-defined domain name to access hosted static website

   **Figure 1** Using a user-defined domain name to access hosted static website

Operation Process
-----------------

Create a bucket on OBS Console first, for storing static website resources, and enable static website hosting for this bucket. Then use DNS to create and configure domain name hosting. The procedure is as follows:

#. :ref:`Register a domain name. <obs_03_0338__li60359246145535>`
#. :ref:`Create a bucket. <obs_03_0338__li3389392914569>`
#. :ref:`Upload static website files. <obs_03_0338__li40840329145633>`
#. :ref:`Configure static website hosting on OBS. <obs_03_0338__li55012967145655>`
#. :ref:`Bind a user-defined domain name. <obs_03_0338__li1181751112130>`
#. :ref:`Create and configure domain name hosting. <obs_03_0338__li25854022145746>`
#. :ref:`Verify the configuration. <obs_03_0338__li52936006101225>`

Data Planning
-------------

:ref:`Table 1 <obs_03_0338__table519146461490>` describes the data to be planned before this configuration.

.. _obs_03_0338__table519146461490:

.. table:: **Table 1** Data planning

   +--------------------------+----------------------------------------------------------------------------------------------------+-----------------+
   | Item                     | Description                                                                                        | Example         |
   +==========================+====================================================================================================+=================+
   | User-defined domain name | Indicates user's own domain name.                                                                  | www.example.com |
   +--------------------------+----------------------------------------------------------------------------------------------------+-----------------+
   | Static website homepage  | Indicates the index page that is returned when you access a static website, that is, the homepage. | index.html      |
   +--------------------------+----------------------------------------------------------------------------------------------------+-----------------+
   | 404 error page           | When an incorrect static website path is accessed, the 404 error page is returned.                 | error.html      |
   +--------------------------+----------------------------------------------------------------------------------------------------+-----------------+

-  For example, the content of the **index.html** file is as follows:

   .. code-block::

      <html>
        <head>
            <title>Hello OBS!</title>
            <meta charset="utf-8">
        </head>
        <body>
            <p>Welcome to use OBS static website hosting.</p>
            <p>This is the homepage.</p>
        </body>
      </html>

-  For example, the content of the **error.html** file is as follows:

   .. code-block::

      <html>
        <head>
            <title>Hello OBS!</title>
            <meta charset="utf-8">
        </head>
        <body>
            <p>Welcome to use OBS static website hosting.</p>
            <p>This is the 404 error page.</p>
        </body>
      </html>

Procedure
---------

#. .. _obs_03_0338__li60359246145535:

   Register a domain name.

   If you have a registered domain name, skip this step.

   If you do not have a registered domain name, register one with a registrar of your choice. In this scenario, the example domain name **www.example.com** is used. In practice, you need to replace the domain name with the one you actually planned.

#. .. _obs_03_0338__li3389392914569:

   Create a bucket.

   There are no special requirements on bucket names. Create a bucket for storing static website files as prompted. The following example describes how to create a bucket named **example**:

   a. Log in to OBS Console.
   b. Click **Create Bucket** in the upper right corner of the page.
   c. Configure the following parameters in the dialog box that is displayed:

      -  **Region**: Select a region closest to you.
      -  **Bucket Name**: Enter **example**.
      -  **Storage Class**: It is recommended that you select **Standard**.

         .. note::

            You can also select the Warm, or Cold storage class based on the website requirements for access frequency and speed. For details about storage classes, see :ref:`Storage Classes <en-us_topic_0050937852>`.

      -  **Bucket Policy**: Select **Public Read** to allow any user to access objects in the bucket.
      -  **Server-Side Encryption**: Choose **Disable**.

   d. Click **Create Now** to complete the creation.

#. .. _obs_03_0338__li40840329145633:

   Upload static website files to the bucket.

   Prepare the static website files to be uploaded and perform the following steps to upload all static website files to bucket **example**.

   a. Click the bucket name **example** to go to the **Objects** page.

   b. Click **Upload Object**. A dialog box shown in :ref:`Figure 2 <obs_03_0338__fig18806520194814>` is displayed.

      .. _obs_03_0338__fig18806520194814:

      .. figure:: /_static/images/en-us_image_0000002275909777.png
         :alt: **Figure 2** Uploading an object

         **Figure 2** Uploading an object

   c. Drag the prepared static website files to the **Upload Object** area.

      You can also click **add file** in the **Upload Object** area to select files.

      .. note::

         -  The static website files cannot be encrypted for upload.
         -  The website home page file (**index.html**) and 404 error page (**error.html**) must be stored in the root directory of the bucket.
         -  It is recommended that you select **Standard** for the storage class. If the storage class of a static website file is Cold, you need to restore the static website file before you can access it. For details, see :ref:`Restoring an Object from Cold Storage <obs_03_0320>`.

   d. Click **Upload** to complete the upload.

#. .. _obs_03_0338__li55012967145655:

   Configure static website hosting.

   After uploading the static website files, you need to configure the static website hosting function for the bucket.

   .. note::

      You can also redirect the entire static website to another bucket or domain name. For details, see :ref:`Configuring Redirection <en-us_topic_0066088957>`.

   a. Click the bucket name **example** to go to the **Objects** page.

   b. In the navigation pane, choose **Basic Configurations** > **Static Website Hosting**. The **Static Website Hosting** page is displayed.

   c. Click **Configure Static Website Hosting**. The **Configure Static Website Hosting** dialog box is displayed.

   d. Enable **Status**.

   e. Set **Hosting By** to **Current bucket**.


      .. figure:: /_static/images/en-us_image_0145846197.png
         :alt: **Figure 3** Configuring static website hosting

         **Figure 3** Configuring static website hosting

      .. note::

         You can also configure redirection rules based on service requirements to implement website content redirection. For details, see :ref:`Configuring Static Website Hosting <en-us_topic_0045853755>`.

   f. Set the **Home Page** to **index.html** as planned, and the **404 Error Page** to **error.html**.

   g. Click **OK**.

#. .. _obs_03_0338__li1181751112130:

   Bind a user-defined domain name.

   To bind a user-defined domain name to a bucket, perform the following steps:

   a. Click the bucket name **example** to go to the **Objects** page. In the navigation pane, choose **Domain Name Mgmt**.

   b. Click **Configure User Domain Name** and set **User Domain Name** to **www.example.com**.


      .. figure:: /_static/images/en-us_image_0000001121218940.png
         :alt: **Figure 4** Configuring a user domain name

         **Figure 4** Configuring a user domain name

   c. Click **OK**. The user-defined domain name is bound to the bucket.

#. .. _obs_03_0338__li25854022145746:

   Create and configure domain name hosting.

   To facilitate unified management of your user-defined domain names and static websites and implement cloud-based services, directly manage your user-defined domain names on DNS. After the hosting is configured, you can perform subsequent management of the domain name on DNS, including managing record sets and PTR records, as well as creating wildcard DNS records.

   Alternatively, you can add a CNAME record to the DNS at the DNS registrar, mapping to the static website domain name hosted by the bucket.

   To create and configure domain name hosting on DNS, perform the following steps:

   a. Add a public zone.

      Use the root domain name **example.com** created in :ref:`Step 1 <obs_03_0338__li60359246145535>` as the name of the public zone to be created. For details about how to create a public zone, see "Step 1. Create a Public Zone" in section "Routing Internet Traffic to a Website" of the *Domain Name Service User Guide*.

   b. Add a CNAME record.

      In DNS, add a record set for the sub-domain name **www.example.com** of the hosted domain name, to map the CNAME of the sub-domain name to the static website domain name hosted by OBS. Configure the parameters as follows:

      -  **Name**: Enter **www**.
      -  **Type**: Select **CNAME-Canonical name**.
      -  **Line**: Select **Default**.
      -  **TTL (s)**: Retain the default value.
      -  **Value**: Domain name to map, that is, the static website domain name hosted by bucket **example**.

      For details, see section "Adding a CNAME Record Set" in the *Domain Name Service User Guide*.

   c. Change the DNS server address at your domain name registrar.

      At your domain name registrar, change the DNS server address in the NS record of the root domain name to the cloud DNS server address. The specific address is the NS value of the public zone in DNS.

      For details about how to change the addresses of the DNS servers, see "Step 4. Change DNS Servers of the Domain Name" in section "Routing Internet Traffic to a Website" of the *Domain Name Service User Guide*.

      .. note::

         The address change will be effective within 48 hours. The actual time taken varies depending on the domain name registrar.

#. .. _obs_03_0338__li52936006101225:

   Verify that the configuration is successful.

   -  Open **www.example.com** using a browser to verify that the default homepage can be accessed. See :ref:`Figure 5 <obs_03_0338__fig37569995102120>`.

      .. _obs_03_0338__fig37569995102120:

      .. figure:: /_static/images/en-us_image_0129289255.png
         :alt: **Figure 5** Default homepage

         **Figure 5** Default homepage

   -  Visit a static file that does not exist in the bucket, for example, opening **www.example.com/imgs** in a browser, to verify that the 404 error page can be returned. See :ref:`Figure 6 <obs_03_0338__fig117531153115316>`.

      .. _obs_03_0338__fig117531153115316:

      .. figure:: /_static/images/en-us_image_0129289469.png
         :alt: **Figure 6** 404 error page

         **Figure 6** 404 error page

   .. note::

      In some conditions, you may need to clear the browser cache before the expected results are displayed.

Website Update
--------------

If you need to update a static file, such as a picture, a piece of music, an HTML file, or a CSS file, you can re-upload the static file.

By default, if two files in a path share one name, the newly uploaded file overwrites the original one. To prevent files from being overwritten, you can enable the versioning function. Versioning allows you to keep multiple versions of a static file, so that you can retrieve and restore history versions conveniently. With versioning enabled, data can be restored rapidly when accidental operations or application faults occur. For detailed information about versioning, see chapter :ref:`Versioning Overview <en-us_topic_0045853504>`.
