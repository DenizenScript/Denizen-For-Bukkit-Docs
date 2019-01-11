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

Comparison operators **compare two values**. An expression that uses a
comparison operator returns the boolean value ``true`` if the comparison
succeeds. Otherwise, the expression returns ``false``.

All comparison operator information can also be found `here`__. Below is a quick
list of commonly used operators.

.. __: https://one.denizenscript.com/denizen/lngs/operator

.. rst-class:: table-info-display

+-------------+-------------+--------------------------------------------------+
| Operator    | Alternative | Description                                      |
|             | Version     |                                                  |
+=============+=============+==================================================+
| ``==``      | ``EQUALS``  | Checks to see if two values are **completely     |
|             |             | equal** to each other.                           |
+-------------+-------------+--------------------------------------------------+
| ``!=``      | ``!EQUALS`` | Checks to see if two values are **not equal** to |
|             |             | each other.                                      |
+-------------+-------------+--------------------------------------------------+
| ``<``       | ``LESS``    | Checks to see if one value is **less than** the  |
|             |             | other.                                           |
+-------------+-------------+--------------------------------------------------+
| ``<=``      | ``OR_LESS`` | Checks to see if one value is **less than or     |
|             |             | equal to** the other.                            |
+-------------+-------------+--------------------------------------------------+
| ``>``       | ``MORE``    | Checks to see if one value is **greater than**   |
|             |             | the other.                                       |
+-------------+-------------+--------------------------------------------------+
| ``>=``      | ``OR_MORE`` | Checks to see if one value is **greater than or  |
|             |             | equal to** the other.                            |
+-------------+-------------+--------------------------------------------------+
| ``MATCHES`` | none        | Checks to see if the given value is of a         |
|             |             | particular type.                                 |
+-------------+-------------+--------------------------------------------------+

.. note::
  
  The ``==``, ``!=``, ``<``, ``<=``, ``>``, and ``>=`` operators can compare any
  two numbers.

  The ``==`` and ``!=`` operators can compare any two numbers and text.

  The ``MATCHES`` operator can only take a specific compared value, which
  specifies a type. The list of types can be found `here`__. 

.. __: https://one.denizenscript.com/denizen/lngs/operator

`To Top of Page`_

Logical Operators
~~~~~~~~~~~~~~~~~

Logical operators **takes the result of one or more logical expressions** and
evaluates the combined expression to a boolean value.

.. rst-class:: table-info-display

+-----------+------------------------------------------------------------------+
| Operator  | Description                                                      |
+===========+==================================================================+
| ``&&``    | | Checks if every conditional expression evaluates to ``true``.  |
|           | | If even one condition evaluates to ``false``, then the entire  |
|           |   expression is evaluated as ``false``.                          |
+-----------+------------------------------------------------------------------+
| ``||``    | | Checks if at least one conditional expression evaluates to     |
|           |   ``true``.                                                      |
|           | | If all conditions evaluate to ``false``, then the entire       |
|           |   expression is evaluated as ``false``.                          |
+-----------+------------------------------------------------------------------+
| ``!``     | | Takes a boolean value and returns the opposite boolean value.  |
|           | | ``!true`` evaluates to ``false``.                              |
|           | | ``!false`` evaluates to ``true``.                              |
+-----------+------------------------------------------------------------------+

.. note::
  
  A single combination of expressions can only use one type of logical operator.
  Using a mix of both logical operators requires grouping.

`To Top of Page`_

Grouping
~~~~~~~~

In conditional expressions, grouping can be used to ensure that multiple
conditions are evaluated together.

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

.. note::

  There *must* be a space separating the parentheses from the other arguments
  for Denizen to recognize the grouping.

`To Top of Page`_

Script Types
------------

Task Scripts
~~~~~~~~~~~~

A **task script** is a script container that holds script blocks. The script
blocks do not run unless explicitly made to through the ``run`` or ``inject``
command.

`To Top of Page`_

Tags
----

General Definition
~~~~~~~~~~~~~~~~~~

**Tags** are a way to retrieve modified or unmodified data without changing the
object the data originates from.

For example, ``<player.name>`` returns the attached player's username without
changing it.

Note that some tags do not rely on a specific object and act as utilities.

For example, |tag-rnd-int| returns a random number between two numbers, where
``<FIRST_NUMBER>`` and ``<SECOND_NUMBER>`` are replaced with a lower and upper
bound.

.. |tag-rnd-int| replace:: ``<util.random.int[<FIRST_NUMBER>].to[<SECOND_NUMBER>]>``

`To Top of Page`_

Tag Marks
~~~~~~~~~

**Tag marks** are the ``<`` and ``>`` characters wrapped around a string of text
that can be interpreted as a tag.

For example, ``<player.name>`` is a tag, and Denizen recognizes it as such
because it begins with a ``<`` tag mark and ends with a ``>`` tag mark.

`To Top of Page`_
