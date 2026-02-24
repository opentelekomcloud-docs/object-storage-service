:original_name: obs_11_0080.html

.. _obs_11_0080:

Why Is a Question Mark Displayed in the Batch Task Progress Bar?
================================================================

**Possible causes**:

When a batch upload or download task is being executed, if there are a large number of objects involved, obsutil needs to traverse all objects to collect the total number and size of objects in the task. During this collection process, a question mark (?) is displayed in the progress bar.

**Solution**:

After the information is collected, corresponding task details will be displayed in the progress bar.
