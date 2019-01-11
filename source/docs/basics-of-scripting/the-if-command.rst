==================
2.4 The If Command
==================

This section covers the video "`Alternative\/Dynamic Actions\: The If Command`_" by mcmonkey.

.. _Alternative\/Dynamic Actions\: The If Command:
  https://one.denizenscript.com/denizen/vids/Alternate/Dynamic%20Actions:%20The%20If%20Command

.. contents::
  :local:

.. note::
  
  The video uses the old, deprecated braced syntax. The modern syntax uses
  colons and proper indentation. We will still use the example found in the
  video, but corrected to reflect the new modern syntax.

.. note::

  At the time the video was made, grouping of logical expressions was not
  available in Denizen. Currently, grouping *is* available to use. That is
  covered by this guide, in the third part of :ref:`Part 5: Complex "if"/"else
  if" Conditions <2-4-5_complex-if-else-if-conditions>`.

Before We Start
---------------

If you've seen, written, or studied code at all, one of the first things you
learned was the ``if`` statement. If you haven't, the question you should have
now is, "What if I want this script to run conditionally? What if I want my
script to be dynamic, and *not* do the same thing over and over again?"

To anyone starting Denizen, this is the opportunity of the lifetime. A surefire
fan favorite, the ``if`` command will help us accomplish what has already been
accomplished in countless programs.

1. A First Look at the ``if`` Command
-------------------------------------

The ``if`` command allows our script to react in dynamic ways. Essentially, it
will run its associated script block *only if certain conditions are met*. If
the conditions are not met, then the associated script block won't run. Simple,
isn't it?

If you've coded before, you can guess that there is another sort of command that
should come with the ``if`` command. If you haven't coded before, then you're in
for a nice treat.

This other command is the ``else`` command. Any script block associated with the
``else`` command will run if and only if *every condition in its associated*
``if`` *command fails*.

Wait. Not only are we using the word "if" way too much for four short
paragraphs, we're talking about making the ``if`` and ``else`` commands run
certain blocks of script. How can we assign lines of script to these two
commands? How can Denizen know which blocks of script to run and not to run?
Answering these questions will require an example.

To take a break from task scripts, we'll use a new script type: the world
script. Don't fret! We'll cover that in the :doc:`next section
</docs/basics-of-scripting/your-first-world-script>`, :doc:`Section 2.4
</docs/basics-of-scripting/your-first-world-script>`.

Consider the following world script:

.. code-block:: dscript
  :name: figure2_4_1
  :linenos:
  :emphasize-lines: 5-8

  script2:
      type: world
      events:
          on player breaks sand:
          - if true:
              - narrate pass
          - else:
              - narrate fail
          - narrate "a b c d e f g"
          - determine cancelled

.. rst-class:: figurecaption

**Figure 2.4.1** A world script using ``if``/``else`` commands

Unlike our previous examples, this script can be tested without using ``/ex run
SCRIPT_CONTAINER_NAME``. This script will automatically run whenever you break a
sand block. And don't worry about running out of sand blocks. The ``- determine
cancelled`` at the end will prevent you from actually breaking the sand block.
So you can go ham on that block, but stay with us.

When you break a sand block, you should expect to see something like this:

.. image:: /_static/images/f2.4.2_result-of-f2.4.1.png
  :name: figure2_4_2
  :width: 90%
  :align: center
  :alt: result of figure 2.4.1

.. rst-class:: figurecaption

**Figure 2.4.2** The expected results when running the script in :ref:`Figure
2.4.1<figure2_4_1>`

There's something missing, isn't there? You should notice that ``- narrate
fail`` never ran. Why is that? We specifically wrote that in there, so why did
it do nothing? Did I just trick you into a useless switch scenario? ... Yes I
did, but let me explain.

Take a look closer at our script in :ref:`Figure 2.4.1<figure2_4_1>`. The ``if``
command has the argument "``true``". This is a **boolean** value. Every ``if``
command's arguments must eventually resolve into a boolean value, which can be
either **true** or **false**. If the conditions in the ``if`` command eventually
resolve to ``true``, then anything in the script block associated with that
``if`` command runs. Otherwise, that script block doesn't run, and Denizen moves
on to the next unindented command.

In :ref:`Figure 2.4.1<figure2_4_1>`, our ``if`` command is given the boolean
value ``true``, so it runs its script block. Then Denizen reaches the ``else``
command. Remember what we said about the ``else`` command and when it runs. Did
the ``if`` command's arguments resolve to ``false``? No. Since every condition
did not fail, the ``else`` command's script block cannot run.

If you feel so inclined, you can replace the ``true`` with a ``false`` and
re-run the script. Then, you will see that the ``if`` command's script block
does not run while the ``else`` command's script block runs.

Of course, the unindented ``narrate`` and ``determine`` commands are not
associated with either the ``if`` or ``else`` commands, so they run regardless
of the result of either the ``if`` or ``else`` command.

2. How to Write an ``if``/``else`` Block
----------------------------------------

As you were looking back at :ref:`Figure 2.4.1<figure2_4_1>`, you should have
noticed three things.

1. Indentation is used to indicate which lines of script are associated with the
   ``if`` and ``else`` commands.
#. The ``else`` command is placed directly underneath the ``if`` command's
   script block.
#. The ``if`` command takes an argument, while the ``else`` command does not.

**The first point** is self-explanatory. As mentioned in :doc:`Section 1.3
</docs/getting-started/dscript-format>`, indentation is primarily used as a way
to associate things with each other. Extra indentation in a script block causes
those lines to become associated with the command immediately above the indented
block. Of course, it doesn't make sense that this works with *every* command.
You'll learn about more commands that use indented script blocks later.

**The second point** is a little more subtle. The ``else`` command relies on the
idea that for it to run, there has to be an ``if`` condition that fails first.
There cannot be any extra unindented lines of script in between the ``else`` and
``if``, as that will cause the ``else`` command to have no ``if`` command to
depend upon. To make this a little more clear, let's look at the following
script snippet:

.. code-block:: dscript
  :name: figure2_4_3
  :linenos:
  :emphasize-lines: 3

  - if false:
      - narrate pass
  - announce "You thought there would be an else here, but it was me!"
  - else:
      - narrate fail
  - narrate "a b c d e f g"

.. rst-class:: figurecaption

**Figure 2.4.3** A malformed ``if``/``else`` block

When the ``else`` command is run in the above example, it looks for the very
first command above itself that has the same indentation. That very first
command would be the ``announce`` command. So where's the thing that lets the
``else`` command say "A condition failed, so we'll run this other bit of
script"? According to Denizen, nowhere. So it throws an error.

As a human, you would point to the ``if`` command above that ``announce``
command and say, "Isn't that the ``if`` command you're looking for?". Denizen
doesn't see that. All it sees is an ``else`` command without an ``if`` command.
So be careful, and make sure that you don't have any commands that break up an
``if``/``else`` chain.

**The third point** is also self-explanatory. As we have mentioned twice now,
the ``else`` command runs its script block only if every condition in its
associated ``if`` command fails. Why does it need an argument? It'll run when
everything else in its ``if`` command fails.

But what if we *don't* want it to do that? What if we want an additional
condition after the ``if`` command? What if we want a more complex chain of
script blocks that run based on a variety of conditions? Putting ``if``/``else``
commands inside of other ``if``/``else`` commands seems like a pain. So... let's
put the two commands together!

3. The Middle Ground: ``else if``
---------------------------------

If you thought we were going to introduce another command, you're wrong. We're
going to reuse the ``else`` command and transform it into its middle ground,
an ``else if``. The ``else if`` does rely on an ``if`` command, but it has a
unique function. It will run when the ``if`` command's conditions fails, but
has its own conditions to check. Only after every ``if`` and ``else if`` fail
will the ``else`` command run.

We're going to modify :ref:`Figure 2.4.1<figure2_4_1>` a bit. Consider this
edit:

.. code-block:: dscript
  :name: figure2_4_4
  :linenos:
  :emphasize-lines: 5,7-8

  script2:
      type: world
      events:
          on player breaks sand:
          - if false:
              - narrate pass
          - else if true:
              - narrate wee
          - else:
              - narrate fail
          - narrate "a b c d e f g"
          - determine cancelled

.. rst-class:: figurecaption

**Figure 2.4.4** A world script using an ``if``/``else if``/``else`` chain

We know that the ``if`` command fails, since its condition resolves to
``false``. The next command read is the ``else if`` command. Notice how it also
takes a boolean argument, just like a standard ``if`` command. In this case, the
``else if`` command's condition resolves to ``true``, so it runs its script
block.

And finally, our last ``else`` command. We know that the ``else`` command's
script block only runs if all of its associated ``if`` command's conditions
fail. So how does this tie in with the ``else if``?

Quite simply, the ``else`` command's script block won't run. Because of the
introduction of the ``else if`` command, all of the ``if`` **and** ``else if``
commands' conditions must fail before the ``else`` command's script block can
run. If any of the ``if`` or ``else if`` commands' conditions resolve to
``true``, the ``else`` command won't run its script block.

4. Variations on the ``if``/``else if``/``else`` Chain
------------------------------------------------------

There are many ways to write an ``if``/``else if``/``else`` chain. You can have
as many ``else if`` commands as you want, from zero to a few hundred thousand
(but you should probably avoid having that many ``else if`` commands). You can
have an ``if``/``else if`` chain without an ``else`` command. You can just have
an ``if`` command all by itself!

The following figures demonstrate this well.

.. code-block:: dscript
  :name: figure2_4_5
  :linenos:
  
  no_else_or_else_ifs:
      type: task
      script:
      - if true:
          - narrate pass

.. rst-class:: figurecaption

**Figure 2.4.5** An ``if`` command by itself

.. code-block:: dscript
  :name: figure2_4_6
  :linenos:
  
  no_else_ifs:
      type: task
      script:
      - if true:
          - narrate pass
      - else:
          - narrate fail

.. rst-class:: figurecaption

**Figure 2.4.6** An ``if``/``else`` chain

.. code-block:: dscript
  :name: figure2_4_7
  :linenos:
  
  no_else:
      type: task
      script:
      - if false:
          - narrate pass
      - else if true:
          - narrate wee

.. rst-class:: figurecaption

**Figure 2.4.7** An ``if``/``else if`` chain

.. code-block:: dscript
  :name: figure2_4_8
  :linenos:
  
  many_else_ifs_no_else:
      type: task
      script:
      - if false:
          - narrate pass
      - else if false:
          - narrate wee
      - else if false:
          - narrate oopsies
      - else if true:
          - narrate *crash*
      - else if false:
          - narrate ouchies

.. rst-class:: figurecaption

**Figure 2.4.8** An ``if``/``else if`` chain with multiple ``else if`` commands
  
.. code-block:: dscript
  :name: figure2_4_9
  :linenos:
  
  many_else_ifs:
      type: task
      script:
      - if false:
          - narrate pass
      - else if false:
          - narrate wee
      - else if false:
          - narrate oopsies
      - else:
          - narrate fail

.. rst-class:: figurecaption

**Figure 2.4.9** An ``if``/``else if``/``else`` chain with multiple ``else if``
commands

Note that in all of the examples, each ``if``/``else if``/``else`` chain only
ever has a maximum of one ``if`` and one ``else`` command.

.. _2-4-5_complex-if-else-if-conditions:

5. Complex ``if``/``else if`` Conditions
----------------------------------------

When all's said and done, we still haven't really covered something important.
I said that the arguments of the ``if`` and ``else if`` commands must
*eventually resolve into a boolean value* of either ``true`` or ``false``. We've
only been explicitly writing out "``true``" and "``false``" so far. Can this
possibly get more complex?

But of course it can!

.. contents::
  :local:

Comparing Two Values to Each Other
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In general, there are two ways to write a condition for the ``if`` command. It
can either be one value that resolves to ``true`` or ``false``, or a value
being compared to another.

Consider this modification on :ref:`Figure 2.4.1<figure2_4_1>`:

.. code-block:: dscript
  :name: figure2_4_10
  :linenos:
  :emphasize-lines: 5

  script2:
      type: world
      events:
          on player breaks sand:
          - if <util.random.int[1].to[5]> == 3:
              - narrate pass
          - else:
              - narrate fail
          - narrate "a b c d e f g"
          - determine cancelled
  
.. rst-class:: figurecaption

**Figure 2.4.10** An ``if`` command comparing a tag to a number

If you recall from :doc:`Section 2.1
</docs/basics-of-scripting/an-introduction-to-tags>`, the
``<util.random.int[1].to[5]>`` tag returns a random integer from 1 to 5. So
every time you break a sand block, a number from 1 to 5 is chosen.

The entire ``<util.random.int[1].to[5]> == 3`` part is a **logical expression**.
Logical expressions *eventually resolve to a boolean value*, depending on the
operator used. In this case, the logical expression ``<util.random.int[1].to[5]>
== 3`` directly compares the result of ``<util.random.int[1].to[5]>`` to ``3``.
If the comparison succeeds, the expression will evaluate to ``true``. Otherwise,
it evaluates to ``false``.

.. note::

  Not all logical expressions are comparisons! Sometimes, it can be a single
  value (such as "``true``") or a single tag.

The ``==`` symbol is a type of **comparison operator**. This specific operator
compares two values and sees if they exactly match each other. In this case, the
``if`` command is seeing if the randomly chosen number exactly matches ``3``.

Below is a quick table displaying the different types of comparison operators.
Additional information can be found in the :doc:`Glossary</docs/glossary>`.

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
| ``MATCHES`` | none        | | Checks to see if the given value is of a       |
|             |             |   particular type.                               |
|             |             | | Available types can be found                   |
|             |             |   `here`__.                                      |
+-------------+-------------+--------------------------------------------------+

.. __: https://one.denizenscript.com/denizen/lngs/operator

|

Combining Two or More Expressions
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Cool beans. Now we have an impressive arsenal of comparisons at our disposal.
But... what if we want to do *multiple comparisons at once*? Well, you're in
luck. That can be accomplished using **logical operators**!

Consider this modification on :ref:`Figure 2.4.10<figure2_4_10>`:

.. code-block:: dscript
  :name: figure2_4_11
  :linenos:
  :emphasize-lines: 5

  script2:
      type: world
      events:
          on player breaks sand:
          - if 3 == 3 && 4 == 4:
              - narrate pass
          - else:
              - narrate fail
          - narrate "a b c d e f g"
          - determine cancelled
  
.. rst-class:: figurecaption

**Figure 2.4.11** An ``if`` command using a logical operator

We have two comparisons here. We are seeing if ``3`` is exactly equal to ``3``,
and if ``4`` is exactly equal to ``4``. So what is the ``&&`` doing? Well, go
back to the second sentence of this paragraph and look at the word after the
comma. Spoilers, I'm talking about the word "*and*".

The logical operator ``&&`` *combines the result of the expressions* ``3 == 3``
*and* ``4 == 4``. If both expressions evaluate to ``true``, then the entire
logical expression ``3 == 3 && 4 == 4`` evaluates to true. However, if either or
both of them evaluate to ``false``, then the entire logical expression evaluates
to ``false``.

.. note::

  One of the three logical operators does not combine two or more logical
  expressions.

  The ``!`` logical operator inverts the result of a boolean value. So if our
  theoretical tag ``<some_random_boolean>`` returns ``true``, then
  ``!<some_random_boolean>`` returns ``false``.

Below is a quick table displaying the different types of logical operators.
Additional information can be found in the :doc:`Glossary</docs/glossary>`.

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

|

Grouping Expressions Together
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You are probably tired of me saying "What if", but *what if we wanted to use*
``&&`` *and* ``||`` *at the same time*?

We absolutely can! But with what we know right now, that isn't possible.
Consider the following script snippet:

.. code-block:: dscript
  :name: figure2_4_12
  :linenos:
  
  - if true && true || false:
      - narrate "Well what am I supposed to do now?"

.. rst-class:: figurecaption

**Figure 2.4.12** An illegal logical expression

What is Denizen supposed to do? We have two logical operators that act in
completely opposite ways. We might say, "Just go left to right!" But Denizen
doesn't do that. It evaluates the entire expression, not individual parts. So,
what can we do?

If we can combine multiple logical expressions into one using logical operators,
would it not make sense if we could *separate the entire logical expression into
multiple parts*? That's what grouping does. It separates the expression into
subparts that are evaluated first.

We're going to have our way with :ref:`Figure 2.4.1<figure2_4_1>` just one more
time. Consider this edit:

.. code-block:: dscript
  :name: figure2_4_13
  :linenos:
  :emphasize-lines: 5

  grouping_example:
      type: world
      events:
          on player breaks sand:
          - if true && ( true || false ):
              - narrate pass
          - else:
              - narrate fail
          - narrate "a b c d e f g"
          - determine cancelled

.. rst-class:: figurecaption

**Figure 2.4.13** Grouping a logical expression together

When Denizen parses this script, it will see that the logical expression ``true
|| false`` should be evaluated first. The following is an approximate depiction
of how grouping works:

1. Given the expression ``true && ( true || false )``, Denizen sees that there
   is a group ``( true || false )``. It will evaluate the expression in that
   group first.
#. The expression ``true || false`` evaluates to ``true`` (see `Combining Two or
   More Expressions`_ for more information).
#. Denizen replaces the group ``( true || false )`` with the result of its
   encapsulated expression. Therefore, ``( true || false )`` is replaced with
   ``true``.
#. Denizen looks at the whole expression again. ``true && ( true || false )`` is
   equivalent to ``true && true``. This new expression evaluates to ``true``.

Afterword
---------

So now you know everything you need to know about the ``if`` and ``else``
commands. You know about how to write them, what logical expressions are, what
operators you can use, and what grouping is. With this, you have the tools to
create a dynamic bit of script that can react differently depending on the
situation. You can make your script as complex or simple as you want!

We're ready to brave a new (newer?) frontier!

|

.. rst-class:: previous-next-table

+-------------------+-----------------+
| | Previous page:  | | Next page:    |
| | |prev-doc|      | | |next-doc|    |
+-------------------+-----------------+

.. |prev-doc| replace:: :doc:`2.3 (Your First Task Script)</docs/basics-of-scripting/your-first-task-script>`

.. |next-doc| replace:: :doc:`2.5 (Your First World Script)</docs/basics-of-scripting/your-first-world-script>`
