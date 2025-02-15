.. include:: /Includes.rst.txt
.. _columns-flex-properties-ds:

===================
Data structure (ds)
===================

.. confval:: ds

   :Path: $GLOBALS['TCA'][$table]['columns'][$field]['config']
   :type: array
   :Scope: Display  / Proc.

   Data Structure(s) defined in an array.

   Each key is a value that can be pointed to by :ref:`ds_pointerField <columns-flex-properties-ds-pointerfield>`.
   Default key is "default" which is what you should use if you do not have a :code:`ds_pointerField` value of course.

   If you specified more than one :code:`ds_pointerField`, the keys in this "ds" array should contain comma-separated
   value pairs where the asterisk \* matches all values (see the example below). If you don't need to switch for the
   second ds\_pointerField, it's also possible to use only the first :code:`ds_pointerField`'s value as a key in
   the "ds" array without necessarily suffixing it with ",\*" for a catch-all on the second :code:`ds_pointerField`.

   For each value in the array there are two options:

   -  Either enter XML directly

   -  Make a reference to an external XML file

Examples
========

Example with XML directly entered
---------------------------------

.. code-block:: php

   'config' => [
      'type' => 'flex',
      'ds_pointerField' => 'list_type',
      'ds' => [
         'default' => '
            <T3DataStructure>
               <ROOT>
                  <type>array</type>
                  <el>
                     <xmlTitle>
                        <TCEforms>
                           <label>The Title:</label>
                           <config>
                              <type>input</type>
                           </config>
                        </TCEforms>
                     </xmlTitle>
                  </el>
               </ROOT>
            </T3DataStructure>
         ',
      ],
   ],

Example with XML in external file
---------------------------------

.. code-block:: php

   'config' => [
      'type' => 'flex',
      'ds_pointerField' => 'list_type',
      'ds' => [
         'default' => 'FILE:EXT:mininews/Configuration/FlexForms/Mininews.xml',
      ],
   ],
