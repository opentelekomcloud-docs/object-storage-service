:original_name: obs_03_0440.html

.. _obs_03_0440:

Login Page of OBS Browser Does Not Respond upon User Login
==========================================================

Question
--------

When a user attempts to log in to OBS Browser, the login page does not respond.

Answer
------

Delete the **obs** folder in the **AppData\\Local** directory on the C drive to clear OBS Browser related data. Then log in to OBS Browser again and reconfigure required information. If you want to retain the account information, save the **accounts**, **setting**, and **temp files** in the **obs** folder before deleting the folder. Start OBS Browser again and overwrite the three files in the **obs** folder.
