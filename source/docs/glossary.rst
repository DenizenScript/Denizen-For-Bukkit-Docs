========
Glossary
========

.. _To Top of Page: `Glossary`_

.. contents::
    :local:

Boolean Logic
-------------

Comparison Operators
~~~~~~~~~~~~~~~~~~~~

Comparison operators **compare two values**. An expression that uses a comparison operator returns the boolean value
``true`` if the comparison succeeds. Otherwise, the expression returns ``false``.

All comparison operator information can also be found `here`__. Below is a quick list of commonly used operators.

.. __: https://one.denizenscript.com/denizen/lngs/operator

.. rst-class:: table-info-display

+-------------+-------------+------------------------------------------------------------------------------------------+
| Operator    | Alternative | Description                                                                              |
+=============+=============+==========================================================================================+
| ``==``      | ``EQUALS``  | Checks to see if two values are **completely equal** to each other.                      |
+-------------+-------------+------------------------------------------------------------------------------------------+
| ``!=``      | ``!EQUALS`` | Checks to see if two values are **not equal** to each other.                             |
+-------------+-------------+------------------------------------------------------------------------------------------+
| ``<``       | ``LESS``    | Checks to see if one value is **less than** the other.                                   |
+-------------+-------------+------------------------------------------------------------------------------------------+
| ``<=``      | ``OR_LESS`` | Checks to see if one value is **less than or equal to** the other.                       |
+-------------+-------------+------------------------------------------------------------------------------------------+
| ``>``       | ``MORE``    | Checks to see if one value is **greater than** the other.                                |
+-------------+-------------+------------------------------------------------------------------------------------------+
| ``>=``      | ``OR_MORE`` | Checks to see if one value is **greater than or equal to** the other.                    |
+-------------+-------------+------------------------------------------------------------------------------------------+
| ``MATCHES`` | none        | Checks to see if the given value is of a particular type.                                |
+-------------+-------------+------------------------------------------------------------------------------------------+

.. note::

    The ``==``, ``!=``, ``<``, ``<=``, ``>``, and ``>=`` operators can compare any two numbers.

    The ``==`` and ``!=`` operators can compare any two numbers and text.

    The ``MATCHES`` operator can only take a specific compared value, which specifies a type. The list of types can be
    found `here`__.

.. __: https://one.denizenscript.com/denizen/lngs/operator

`To Top of Page`_

Logical Operators
~~~~~~~~~~~~~~~~~

Logical operators **takes the result of one or more logical expressions** and evaluates the combined expression to a
boolean value.

A single combination of expressions can only use one type of logical operator. Using a mix of both logical operators
requires grouping.

.. rst-class:: table-info-display

+-----------+---------+------------------------------------------------------------------------------------------------+
| Operator  | Name    | Description                                                                                    |
+===========+=========+================================================================================================+
| ``&&``    | ``AND`` | | Checks if every conditional expression evaluates to ``true``.                                |
|           |         | | If even one condition evaluates to ``false``, then the entire expression is evaluated as     |
|           |         |   ``false``.                                                                                   |
+-----------+---------+------------------------------------------------------------------------------------------------+
| ``||``    | ``OR``  | | Checks if at least one conditional expression evaluates to ``true``.                         |
|           |         | | If all conditions evaluate to ``false``, then the entire expression is evaluated as          |
|           |         |   ``false``.                                                                                   |
+-----------+---------+------------------------------------------------------------------------------------------------+
| ``!``     | ``NOT`` | | Takes a boolean value and returns the opposite boolean value.                                |
|           |         | | ``!true`` evaluates to ``false``.                                                            |
|           |         | | ``!false`` evaluates to ``true``.                                                            |
+-----------+---------+------------------------------------------------------------------------------------------------+

`To Top of Page`_

Grouping
~~~~~~~~

In conditional expressions, grouping can be used to ensure that multiple conditions are evaluated together.

Grouping can be achieved using parentheses. Example:

.. code-block:: yaml
    :linenos:

    task_script:
        type: task
        script:
        - if ( true && true ) || false:
            - narrate pass
        - else:
            - narrate fail

A grouping can be negated. For example, ``!( false || false )`` would be evaluated as ``true``.

.. important::

    There *must* be a space separating the parentheses from the other arguments for Denizen to recognize the grouping.

`To Top of Page`_

Flags
-----

General Definition
~~~~~~~~~~~~~~~~~~

**Flags** are persistent data that survives server restarts, provided the server is properly shut down. They can be
assigned to a player, NPC, entity, or the server.

Flag Structure
~~~~~~~~~~~~~~

.. warning::

    The following information regarding the structure of the flag relies on a legacy system. Please refrain from using
    this symbol ``.`` in your flag names, as the legacy system should not be actively used.

Due to its current reliance on a legacy system, flags follow the YAML key structure, i.e. flags may have parent keys and
child keys. For example, a flag with the name ``my_flag.sub_flag`` is a flag whose parent key is ``my_flag``, and child
key is ``sub_flag``. A flag with the name ``my_flag.2nd_sub_flag`` is a flag that shares the same parent key
``my_flag``, but has a child key ``2nd_sub_flag``.

The structure of ``my_flag.sub_flag``, ``my_flag.sub_flag.another_child``, ``my_flag.sub_flag.more_children``, and
``my_flag.2nd_sub_flag`` may be visually seen like this:

.. code::

    my_flag
    |--- sub_flag
    |    |--- another_child (can have value)
    |    |--- more_children (can have value)
    |
    |--- 2nd_sub_flag (can have value)

.. note::

    If any given key acts as the parent key to a child key, then that key cannot have its value changed, set, or
    deleted. Directly changing the value of a parent key will delete all of the child keys.

`To Top of Page`_

Actions
~~~~~~~

**Flag actions** are additional modifiers that determine how the flag command treats the input value in relation to the
flag's current value.

Below is a quick list of flag actions and a brief description of what each does.

.. rst-class:: table-info-display

+----------+---------+-------------+-----------------------------------------------------------------------------------+
| Actions  | Value?  | Indexable?  | Description                                                                       |
+==========+=========+=============+===================================================================================+
| none     | Yes     | Yes         | | Sets the value of the flag.                                                     |
|          |         |             | | If no value is specified, the flag's value will default to ``true``.            |
+----------+---------+-------------+-----------------------------------------------------------------------------------+
| ``!``    | No      | No          | | Deletes the whole flag.                                                         |
|          |         |             | | If the deleted flag is the parent key of other flags, then all flags that are   |
|          |         |             |   the children of the parent flag will also be deleted.                           |
+----------+---------+-------------+-----------------------------------------------------------------------------------+
| ``+``    | Yes     | Yes         | | Increases the flag's value by the specified amount.                             |
|          |         |             | | If a nonexistent flag is specified, the flag's value is treated as zero before  |
|          |         |             |   the addition is performed.                                                      |
+----------+---------+-------------+-----------------------------------------------------------------------------------+
| ``++``   | No      | Yes         | | Increases the flag's value by 1.                                                |
|          |         |             | | If a nonexistent flag is specified, the flag's value is treated as zero before  |
|          |         |             |   the addition is performed.                                                      |
+----------+---------+-------------+-----------------------------------------------------------------------------------+
| ``-``    | Yes     | Yes         | | Decreases the flag's value by the specified amount.                             |
|          |         |             | | If a nonexistent flag is specified, the flag's value is treated as zero before  |
|          |         |             |   the subtraction is performed.                                                   |
+----------+---------+-------------+-----------------------------------------------------------------------------------+
| ``--``   | No      | Yes         | | Decreases the flag's value by 1.                                                |
|          |         |             | | If a nonexistent flag is specified, the flag's value is treated as zero before  |
|          |         |             |   the subtraction is performed.                                                   |
+----------+---------+-------------+-----------------------------------------------------------------------------------+
| ``*``    | Yes     | Yes         | | Multiplies the flag's value by the specified amount.                            |
+----------+---------+-------------+-----------------------------------------------------------------------------------+
| ``/``    | Yes     | Yes         | | Divides the flag's value by the specified amount.                               |
+----------+---------+-------------+-----------------------------------------------------------------------------------+
| ``->``   | Yes     | No          | | Adds the value to the flag list.                                                |
|          |         |             | | If a nonexistent flag is specified, a new flag is created as a list with the    |
|          |         |             |   value as the flag's first entry.                                                |
+----------+---------+-------------+-----------------------------------------------------------------------------------+
| ``<-``   | Yes     | Yes         | | Removes the value from the flag list.                                           |
|          |         |             | | If an index is specified, then the entry at the specified flag list index will  |
|          |         |             |   be removed, regardless of the specified value.                                  |
+----------+---------+-------------+-----------------------------------------------------------------------------------+
| ``|``    | Yes     | No          | | Adds every entry of the specified value to the flag list without overwriting    |
|          |         |             |   the flag list's previous values.                                                |
|          |         |             | | The value is treated as a dList.                                                |
+----------+---------+-------------+-----------------------------------------------------------------------------------+
| ``!|``   | Yes     | No          | | Overwites the flag with the specified value.                                    |
|          |         |             | | The value is treated as a dList.                                                |
+----------+---------+-------------+-----------------------------------------------------------------------------------+

.. note::

    These actions can also be applied to the :guilabel:`yaml` command.

`To Top of Page`_

Indexable Actions
~~~~~~~~~~~~~~~~~

Indexable actions are simply actions that can act on a particular index of a flag list.

The ``<-`` action as an indexed action is special in that it does not use a value. The ``<-`` indexed action will simply
remove the value that is at the specified index of the flag list.

For example, if a flag ``<server.flag[my_list]>`` is a flag list that returns ``1|2|3|4|5``, then ``- flag server
my_list[4]:<-`` will remove the fourth value of the flag list. The new returned value of ``<server.flag[my_list]>`` will
be ``1|2|3|5``.

`To Top of Page`_

Script Types
------------

Task Scripts
~~~~~~~~~~~~

A **task script** is a script container that holds script blocks. The script blocks do not run unless explicitly made to
through the ``run`` or ``inject`` command.

`To Top of Page`_

World Scripts
~~~~~~~~~~~~~

A **world script** is a script container that runs script blocks when a certain event happens. When applicable, the
script block is able to alter the result of the event that fires it.

`To Top of Page`_

Tags
----

General Definition
~~~~~~~~~~~~~~~~~~

**Tags** are a way to retrieve modified or unmodified data without directly changing the object the data originates
from.

For example, if a definition ``my_list`` contains the dList ``li@one|two|three|four``, then
``<def[my_list].remove[last]>`` will return ``li@one|two|three`` *without directly changing the value of the*
``my_list`` *definition*. To change the definition's value, you would need to assign the returned dList to the
definition.

.. note::

    Some tags do not rely on a specific object and act as utilities.

    For example, |tag-rnd-int| returns a random number between two numbers, where ``<FIRST_NUMBER>`` and
    ``<SECOND_NUMBER>`` are replaced with a lower and upper bound.

.. |tag-rnd-int| replace:: ``<util.random.int[<FIRST_NUMBER>].to[<SECOND_NUMBER>]>``

`To Top of Page`_

Tag Marks
~~~~~~~~~

**Tag marks** are the ``<`` and ``>`` characters wrapped around a string of text that can be interpreted as a tag.

For example, ``<player.name>`` is a tag, and Denizen recognizes it as such because it begins with a ``<`` tag mark and
ends with a ``>`` tag mark.

`To Top of Page`_

Tag Structure
~~~~~~~~~~~~~

When constructing a tag, recall that a single tag should be encapsulated by one set of tag marks. For most applications,
``<<object.property>.sub_property>`` is illegal. Such a tag should be written as ``<object.property.sub_property>``, as
Denizen will parse the properties sequentially.

Note that the tag must be operating on an applicable object. For example, ``<player.add[1]>`` is completely illegal, as
the ``<el@element.add[<#>]>`` tag only works for an Element object that is a number.

When a tag requires an input, for example ``<util.random.int[<#>].to[<#>]>``, a tag may be used as the input. As the
general rule, this should be the only time you would see a tag within a tag.

However, there are certain special-case tags. The ternary tag, for example, may accept input like so:

.. code-block:: dscript

    <tern[<tag_that_returns_boolean_value>]:<value_when_true>||<value_when_false>>

In this case, ``<tag_that_returns_boolean_value>``, ``<value_when_true>``, and ``<value_when_false>`` may all be tags,
and Denizen will correctly parse the whole ternary tag.

Additional special-case tags are the ``<parse:<element/tag>>`` and ``<math:<element/tag>>``. Note that of the three,
you will almost never have to use ``<parse:<element/tag>>`` or ``<math:<element/tag>>`` due to the vast amount of other
tags and methods that can accomplish the same goal.

Fallbacks
~~~~~~~~~

A **fallback** is the value that the tag will use, if the tag itself is invalid. For example, ``<invalid tag||null>``
will return ``null`` since ``<invalid tag>`` is not a tag that Denizen can parse without throwing an error.

Note that a fallback can be another tag, e.g. ``<invalid tag||<player.name>>``.

`To Top of Page`_
