.. include:: /Includes.rst.txt
.. _columns-inline-properties-appearance:

==========
appearance
==========

.. confval:: appearance (type => inline)

   :Path: $GLOBALS['TCA'][$table]['columns'][$field]['config']
   :type: array
   :Scope: Display

   Has information about the appearance of child-records, namely:

   collapseAll (boolean)
      Show all child-records collapsed (if false, all are expanded)

   expandSingle (boolean)
      Show only one child-record expanded each time. If a collapsed record is clicked, the currently
      open one collapses and the clicked one expands.

   newRecordLinkAddTitle (boolean)
      Adds the title of the :ref:`foreign_table <columns-inline-properties-foreign-table>` to the "New record" link.

      false
       "Create new"
      true
       "Create new <title of foreign\_table>", e.g. "Create new address"

   newRecordLinkTitle (string or LLL reference)
      Overrides the title of the "New record" link with a localised string. This will work only if
      :code:`newRecordLinkAddTitle` is **not** set to true.

      Example::

         'newRecordLinkTitle' => 'LLL:EXT:myext/Resources/Private/Language/locallang_db.xlf:my_new_record_label'

   createNewRelationLinkTitle (string or LLL reference)
      Overrides the link text and title of the "Create new relation" button with a localised string.
      Only useful, if the element browser is enabled. This is usually used together with FAL relations to change it to "Add file" or similar.

   levelLinksPosition (string)
      Values: 'top' (default), 'bottom', 'both', 'none'. Defines where to show the "New record" link in relation
      to the child records.

   useCombination (boolean)
      This is only useful on bidirectional relations using an intermediate table with attributes. In a "combination" it
      is possible to edit the attributes AND the related child record itself. If using a
      :ref:`foreign_selector <columns-inline-properties-foreign-selector>` in such a case, the
      :ref:`foreign_unique <columns-inline-properties-foreign-unique>` property  **must** be set to the same field as
      the :ref:`foreign_selector <columns-inline-properties-foreign-selector>`.

   suppressCombinationWarning (boolean)
      Suppresses the warning FlashMessage that will be displayed when using **useCombination**.
      You can also override the message with your own message using the example below.

      Example::

         $GLOBALS['TCA']['tx_demo_domain_model_demoinline']['columns']['irre_records']['config'] = [
             'appearance' => [
               'overwriteCombinationWarningMessage' => 'LLL:EXT:demo/Resources/Private/Language/locallang_db.xlf:tx_demo_domain_model_demoinline.irre_records.useCombinationWarning',
               'useCombination' => TRUE
             ],
         ],

   useSortable (boolean)
      Activate drag & drop.

   showPossibleLocalizationRecords (boolean)
      Show unlocalized records which are in the original language, but not yet localized.

   showAllLocalizationLink (boolean)
      Defines whether to show the "localize all records" link to fetch untranslated records from the original language.

   showSynchronizationLink (boolean)
      Defines whether to show a "synchronize" link to update to a 1:1 translation with the original language.

   enabledControls (array)
      Associative array with the keys 'info', 'new', 'dragdrop', 'sort', 'hide', 'delete', 'localize'. If the accordant
      values are set to a boolean value (true or false), the control is shown or hidden in the header of each record.

   showPossibleRecordsSelector (boolean)
      Can be used to hide the foreign record selector from the interface, even if you have a
      :ref:`foreign_selector <columns-inline-properties-foreign-selector>` configured. This can be used to keep the
      technical functionality of the :ref:`foreign_selector <columns-inline-properties-foreign-selector>` but is useful
      if you want to replace it with your own implementation using a custom control,
      see :ref:`customControls <columns-inline-properties-customcontrols>`.

   headerThumbnail (array)
      Defines whether a thumbnail should be rendered in the inline elements' header. This is used by the File
      Abstraction Layer to render a preview of the related image. Can contain image processing instructions like `width` and `height`.

      field (required)
         The table column name, which contains the uid of the image reference. Usually this is :sql:`uid_local`.
      width
         The width of the thumbnail.
      height
         The height of the thumbnail.

   fileUploadAllowed (boolean)
      Defines whether the button "Select & upload file" should be rendered. This can be used for file fields to directly
      upload files and create a reference to the file. The button is limited to file fields using File Abstraction Layer.
      It will only appear to backend users which have write access to the user upload folder. By default this folder is
      :file:`fileadmin/user_upload` but it can be changed in User TSconfig using :typoscript:`options.defaultUploadFolder`.
      See the :ref:`TSconfig reference <t3tsconfig:useroptions>`.

      The button is shown by default unless this option is set to :php:`false`.

   fileByUrlAllowed (boolean)
       Defines whether the button "Add media by URL" should be rendered. This button is used to include media
       URLs from e.g. Vimeo or YouTube. In addition to this, a valid online media identifier must be listed
       in the allowed list of :ref:`elementBrowserAllowed <columns-group-properties-appearance>`.

   elementBrowserEnabled (boolean)
      Hides or displays the element browser button in inline records
