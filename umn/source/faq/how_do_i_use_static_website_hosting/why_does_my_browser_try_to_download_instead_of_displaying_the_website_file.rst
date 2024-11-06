:original_name: obs_faq_101704.html

.. _obs_faq_101704:

Why Does My Browser Try to Download Instead of Displaying the Website File?
===========================================================================

A web browser needs to get the correct media type to correctly handle an HTML file by opening the page instead of downloading the file. So, when uploading a website file (for example, **index.html**) via an API, you need to set its **Content-Type** header to the correct value **text/html** in the case of the HTML files.
