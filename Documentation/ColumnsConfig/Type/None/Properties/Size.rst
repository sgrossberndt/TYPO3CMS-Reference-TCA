.. include:: /Includes.rst.txt
.. _columns-none-properties-size:

====
size
====

.. confval:: size (type => none)

   :Path: $GLOBALS['TCA'][$table]['columns'][$field]['config']
   :type: integer
   :Scope: Display

   The :ref:`cols <columns-none-properties-cols>` value is used to set the width of the field,
   and if :code:`cols` is not found, then this value is used.

   Value for the width of the :code:`<input>` field. To set the input field to the full width of
   the form area, use the value 50. Default is 30.


.. deprecated:: 12.0
   The TCA type `none` had two option keys for the same functionality: `cols` and
   `size`. In order to simplify the available configuration, `cols` has been
   dropped in favour of `size`.

Migration
=========

Rename the option `cols` to `size`.

Before:

.. code-block:: php

    'columns' => [
        'aColumn' => [
            'config' => [
                'type' => 'none',
                'cols' => 20,
            ],
        ],
    ],

After:

.. code-block:: php

    'columns' => [
        'aColumn' => [
            'config' => [
                'type' => 'none',
                'size' => 20,
            ],
        ],
    ],
