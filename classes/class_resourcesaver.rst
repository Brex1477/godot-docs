:github_url: hide

.. DO NOT EDIT THIS FILE!!!
.. Generated automatically from Godot engine sources.
.. Generator: https://github.com/godotengine/godot/tree/master/doc/tools/make_rst.py.
.. XML source: https://github.com/godotengine/godot/tree/master/doc/classes/ResourceSaver.xml.

.. _class_ResourceSaver:

ResourceSaver
=============

**Inherits:** :ref:`Object<class_Object>`

Singleton for saving Godot-specific resource types.

.. rst-class:: classref-introduction-group

Description
-----------

Singleton for saving Godot-specific resource types to the filesystem.

It uses the many :ref:`ResourceFormatSaver<class_ResourceFormatSaver>` classes registered in the engine (either built-in or from a plugin) to save engine-specific resource data to text-based (e.g. ``.tres`` or ``.tscn``) or binary files (e.g. ``.res`` or ``.scn``).

.. rst-class:: classref-reftable-group

Methods
-------

.. table::
   :widths: auto

   +---------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | void                                              | :ref:`add_resource_format_saver<class_ResourceSaver_method_add_resource_format_saver>` **(** :ref:`ResourceFormatSaver<class_ResourceFormatSaver>` format_saver, :ref:`bool<class_bool>` at_front=false **)** |
   +---------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`PackedStringArray<class_PackedStringArray>` | :ref:`get_recognized_extensions<class_ResourceSaver_method_get_recognized_extensions>` **(** :ref:`Resource<class_Resource>` type **)**                                                                       |
   +---------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | void                                              | :ref:`remove_resource_format_saver<class_ResourceSaver_method_remove_resource_format_saver>` **(** :ref:`ResourceFormatSaver<class_ResourceFormatSaver>` format_saver **)**                                   |
   +---------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Error<enum_@GlobalScope_Error>`             | :ref:`save<class_ResourceSaver_method_save>` **(** :ref:`Resource<class_Resource>` resource, :ref:`String<class_String>` path="", :ref:`SaverFlags<enum_ResourceSaver_SaverFlags>` flags=0 **)**              |
   +---------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. rst-class:: classref-section-separator

----

.. rst-class:: classref-descriptions-group

Enumerations
------------

.. _enum_ResourceSaver_SaverFlags:

.. rst-class:: classref-enumeration

flags **SaverFlags**:

.. _class_ResourceSaver_constant_FLAG_NONE:

.. rst-class:: classref-enumeration-constant

:ref:`SaverFlags<enum_ResourceSaver_SaverFlags>` **FLAG_NONE** = ``0``

No resource saving option.

.. _class_ResourceSaver_constant_FLAG_RELATIVE_PATHS:

.. rst-class:: classref-enumeration-constant

:ref:`SaverFlags<enum_ResourceSaver_SaverFlags>` **FLAG_RELATIVE_PATHS** = ``1``

Save the resource with a path relative to the scene which uses it.

.. _class_ResourceSaver_constant_FLAG_BUNDLE_RESOURCES:

.. rst-class:: classref-enumeration-constant

:ref:`SaverFlags<enum_ResourceSaver_SaverFlags>` **FLAG_BUNDLE_RESOURCES** = ``2``

Bundles external resources.

.. _class_ResourceSaver_constant_FLAG_CHANGE_PATH:

.. rst-class:: classref-enumeration-constant

:ref:`SaverFlags<enum_ResourceSaver_SaverFlags>` **FLAG_CHANGE_PATH** = ``4``

Changes the :ref:`Resource.resource_path<class_Resource_property_resource_path>` of the saved resource to match its new location.

.. _class_ResourceSaver_constant_FLAG_OMIT_EDITOR_PROPERTIES:

.. rst-class:: classref-enumeration-constant

:ref:`SaverFlags<enum_ResourceSaver_SaverFlags>` **FLAG_OMIT_EDITOR_PROPERTIES** = ``8``

Do not save editor-specific metadata (identified by their ``__editor`` prefix).

.. _class_ResourceSaver_constant_FLAG_SAVE_BIG_ENDIAN:

.. rst-class:: classref-enumeration-constant

:ref:`SaverFlags<enum_ResourceSaver_SaverFlags>` **FLAG_SAVE_BIG_ENDIAN** = ``16``

Save as big endian (see :ref:`FileAccess.big_endian<class_FileAccess_property_big_endian>`).

.. _class_ResourceSaver_constant_FLAG_COMPRESS:

.. rst-class:: classref-enumeration-constant

:ref:`SaverFlags<enum_ResourceSaver_SaverFlags>` **FLAG_COMPRESS** = ``32``

Compress the resource on save using :ref:`FileAccess.COMPRESSION_ZSTD<class_FileAccess_constant_COMPRESSION_ZSTD>`. Only available for binary resource types.

.. _class_ResourceSaver_constant_FLAG_REPLACE_SUBRESOURCE_PATHS:

.. rst-class:: classref-enumeration-constant

:ref:`SaverFlags<enum_ResourceSaver_SaverFlags>` **FLAG_REPLACE_SUBRESOURCE_PATHS** = ``64``

Take over the paths of the saved subresources (see :ref:`Resource.take_over_path<class_Resource_method_take_over_path>`).

.. rst-class:: classref-section-separator

----

.. rst-class:: classref-descriptions-group

Method Descriptions
-------------------

.. _class_ResourceSaver_method_add_resource_format_saver:

.. rst-class:: classref-method

void **add_resource_format_saver** **(** :ref:`ResourceFormatSaver<class_ResourceFormatSaver>` format_saver, :ref:`bool<class_bool>` at_front=false **)**

Registers a new :ref:`ResourceFormatSaver<class_ResourceFormatSaver>`. The ResourceSaver will use the ResourceFormatSaver as described in :ref:`save<class_ResourceSaver_method_save>`.

This method is performed implicitly for ResourceFormatSavers written in GDScript (see :ref:`ResourceFormatSaver<class_ResourceFormatSaver>` for more information).

.. rst-class:: classref-item-separator

----

.. _class_ResourceSaver_method_get_recognized_extensions:

.. rst-class:: classref-method

:ref:`PackedStringArray<class_PackedStringArray>` **get_recognized_extensions** **(** :ref:`Resource<class_Resource>` type **)**

Returns the list of extensions available for saving a resource of a given type.

.. rst-class:: classref-item-separator

----

.. _class_ResourceSaver_method_remove_resource_format_saver:

.. rst-class:: classref-method

void **remove_resource_format_saver** **(** :ref:`ResourceFormatSaver<class_ResourceFormatSaver>` format_saver **)**

Unregisters the given :ref:`ResourceFormatSaver<class_ResourceFormatSaver>`.

.. rst-class:: classref-item-separator

----

.. _class_ResourceSaver_method_save:

.. rst-class:: classref-method

:ref:`Error<enum_@GlobalScope_Error>` **save** **(** :ref:`Resource<class_Resource>` resource, :ref:`String<class_String>` path="", :ref:`SaverFlags<enum_ResourceSaver_SaverFlags>` flags=0 **)**

Saves a resource to disk to the given path, using a :ref:`ResourceFormatSaver<class_ResourceFormatSaver>` that recognizes the resource object. If ``path`` is empty, **ResourceSaver** will try to use :ref:`Resource.resource_path<class_Resource_property_resource_path>`.

The ``flags`` bitmask can be specified to customize the save behavior using :ref:`SaverFlags<enum_ResourceSaver_SaverFlags>` flags.

Returns :ref:`@GlobalScope.OK<class_@GlobalScope_constant_OK>` on success.

.. |virtual| replace:: :abbr:`virtual (This method should typically be overridden by the user to have any effect.)`
.. |const| replace:: :abbr:`const (This method has no side effects. It doesn't modify any of the instance's member variables.)`
.. |vararg| replace:: :abbr:`vararg (This method accepts any number of arguments after the ones described here.)`
.. |constructor| replace:: :abbr:`constructor (This method is used to construct a type.)`
.. |static| replace:: :abbr:`static (This method doesn't need an instance to be called, so it can be called directly using the class name.)`
.. |operator| replace:: :abbr:`operator (This method describes a valid operator to use with this type as left-hand operand.)`
