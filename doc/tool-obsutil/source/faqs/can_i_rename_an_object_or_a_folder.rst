:original_name: obs_11_0084.html

.. _obs_11_0084:

Can I Rename an Object or a Folder?
===================================

Yes. You can run :ref:`the mv command <obs_11_0053>` to rename an object or a folder. The following give two examples in Windows.

-  Running **obsutil mv obs://bucket-test/key obs://bucket-test/key2** to rename object **key** to **key2**

   .. code-block::

      obsutil mv obs://bucket-test/key obs://bucket-test/key2

      Parallel:      5                   Jobs:          5
      Threshold:     50.00MB             PartSize:      auto
      CheckpointDir: xxxx

      Move successfully, 19B, obs://bucket-test/key --> obs://bucket-test/key2, cost [96], status [200], request id [xxxxxxxxx]

-  Running **obsutil mv obs://bucket-test/temp/ obs://bucket-test/temp2 -flat -f -r** to rename folder **temp** to **temp2**

   .. code-block::

      obsutil mv obs://bucket-test/temp/ obs://bucket-test/temp2/ -flat -f -r

      Parallel:      5                   Jobs:          5
      Threshold:     50.00MB             PartSize:      auto
      CheckpointDir: xxxx
      OutputDir: xxxx


      [=============================================================] 100.00% tps:0.00 2/2 174ms
      Succeed count:   5         Failed count:    0
      Metrics [max cost:298 ms, min cost:192 ms, average cost:238.00 ms, average tps:9.71, transferred size:70B]

      Task id: 0476929d-9d23-4dc5-b2f8-0a0493f027c5

   .. important::

      When renaming a folder, you must add the **-flat** parameter.
