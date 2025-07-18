:original_name: obs_faq_0014.html

.. _obs_faq_0014:

Does OBS Support Resumable Transfer?
====================================

The following table describes the resumable transfer support across OBS tools.

.. table:: **Table 1** Resumable transfer support across OBS tools

   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OBS Tool                          | Resumable Transfer                                                                                                                                                                                                                                                    |
   +===================================+=======================================================================================================================================================================================================================================================================+
   | OBS Console                       | Not supported                                                                                                                                                                                                                                                         |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OBS Browser                       | Supported                                                                                                                                                                                                                                                             |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | SDKs                              | Supported                                                                                                                                                                                                                                                             |
   |                                   |                                                                                                                                                                                                                                                                       |
   |                                   | Before using SDK for resumable transfer, you must enable the resumable transfer option. Only in this way, can the progress of the last upload be read when you continue the transfer process again. For the setting details, see the corresponding SDK documentation. |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | APIs                              | Not supported                                                                                                                                                                                                                                                         |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
