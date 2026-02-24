:original_name: obs_11_0034.html

.. _obs_11_0034:

Configuring Scheduled Tasks Using the Crontab Command
=====================================================

Scenario
--------

Go to the **/root** directory at 21:30 every day and upload the **/src/src1** folder to bucket **obs://bucket-test** in the incremental mode.

Prerequisites
-------------

You have properly enabled the scheduled crond service in the Linux OS.

.. note::

   Run the **service crond status** command to check whether the service is enabled.

Procedure
---------

#. Run the **crontab -e** command to open the configuration file for setting a scheduled task.

#. Enter the Insert mode to edit the configuration file.

   .. code-block::

      30 21 * * * cd /root && nohup ./obsutil cp /src/src1 obs://bucket-test -r -f -u &>obsutil_crond.log &

   .. note::

      Assume that the obsutil tool is in the **/root** directory. The preceding configuration is described as follows: Go to the **/root** directory at 21:30 every day, upload the **/src/src1** folder to bucket **obs://bucket-test** in incremental mode, and redirect the command output to the **obsutil_crond.log** file in the **/root** directory.

#. Press **Esc** to exit the Insert mode. Then input **:wq** and press **Enter** to save the configuration and exit.

#. Run the **crontab -l** command to check whether the scheduled task is configured successfully.

FAQs
----

#. How do I determine whether a scheduled task is being executed?

   -  Run the **tail /var/log/cron** command to view the latest scheduled task execution records.
   -  Run the **ps -ef \| grep obsutil** command to check whether obsutil is being executed.

#. How do I forcibly stop an ongoing scheduled task?

   a. Run the **ps -ef \| grep obsutil** command to check the process of obsutil.
   b. Run the **kill -9** *PID* command to forcibly stop the process, where *PID* indicates the queried process ID.
