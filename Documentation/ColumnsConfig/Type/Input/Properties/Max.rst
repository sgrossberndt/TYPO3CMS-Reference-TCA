.. include:: /Includes.rst.txt
.. _columns-input-properties-max:

===
max
===

.. confval:: max

   :Path: $GLOBALS['TCA'][$table]['columns'][$field]['config']
   :type: integer
   :Scope: Display

   Value for the "maxlength" attribute of the :code:`<input>` field. Javascript prevents adding more than
   these number of characters.

   If the form element edits a varchar(40) field in the database you should also set this value to 40.

   .. note:: If you reduce this value and there is already content longer then :confval:`max` the input will
      be cropped without notice on saving.
