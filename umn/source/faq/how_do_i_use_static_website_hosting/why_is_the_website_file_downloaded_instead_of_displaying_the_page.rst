:original_name: obs_faq_static_website_hosting_content_type.html

.. _obs_faq_static_website_hosting_content_type:

Why Is the Website File Downloaded instead of Displaying the Page?
==================================================================

A web browser needs to get the correct media type to correctly handle an HTML file by opening the page instead of downloading the file. So, when uploading a website file (e.g. index.html) via **API**, you need to set its Content-Type header to the correct value: *text/html* in the case of the HTML files.
