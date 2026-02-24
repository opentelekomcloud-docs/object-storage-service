:original_name: obs_11_0055.html

.. _obs_11_0055:

Overview
========

obsutil provides multiple methods for users to locate and analyze faults. :ref:`Table 1 <obs_11_0055__table8390151719012>` details the methods. Generally, you need to combine these methods for a precise fault locating.

.. _obs_11_0055__table8390151719012:

.. table:: **Table 1** Fault locating methods

   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Method                            | Description                                                                                                                                                                                                                                     |
   +===================================+=================================================================================================================================================================================================================================================+
   | :ref:`Log Files <obs_11_0056>`    | obsutil log files include tool logs and SDK logs. The tool logs record the success information and exceptions generated during obsutil running. The SDK logs record the success information and exceptions generated during requesting for OBS. |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Result Lists <obs_11_0057>` | Result lists are generated after batch tasks complete and may include success, failure, and warning files.                                                                                                                                      |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Return Codes <obs_11_0058>` | obsutil yields different return codes based on different execution results. You can analyze and troubleshoot faults according to these return codes.                                                                                            |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
