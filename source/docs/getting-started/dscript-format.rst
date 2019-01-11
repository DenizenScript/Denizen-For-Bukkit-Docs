==================
1.3 dScript Format
==================

When scripting, it is important to follow the dScript format as closely as
possible to avoid parsing errors, unintended behaviors, or other mishaps that
may arise.

.. contents::
  :local:

1. Basic Script Structure
-------------------------

A script is composed of multiple key parts. The first is the "**script container
name**", and the second is the "**script container type**". All other parts of
the script vary depending on the container type.

The **container name** is simply what the script is called. For example, we may
wish to create a script and name it "``a_task_script``".

The **container type** is the type of script that the container will be. For
example, we may want to make our script "``a_task_script``" a ``task`` type
script.

Putting this together, we get the following:

.. code-block:: dscript
  :name: figure1_3_1
  :linenos:

  a_task_script:
      type: task
      script:
      - define nothing "This script does absolutely nothing!"

.. rst-class:: figurecaption

**Figure 1.3.1** A task script that does nothing

You will learn more about each script container type and their various parts
later.

2. Arguments and Quotes
-----------------------

There may be times when you have a command or a tag that has a space inside of
it. We have an example script below:

.. code-block:: dscript
  :name: figure1_3_2
  :linenos:
  :emphasize-lines: 4

  a_narrate_command:
      type: task
      script:
      - narrate My whole sentence is great, isn't it <player.name>!

.. rst-class:: figurecaption

**Figure 1.3.2** An improperly written ``narrate`` command

When you put this script in your ``./scripts/`` folder and attempt to run it,
you will just see "``My``" in your chat, and probably a couple of weird things
in the debug printed to your console. But we wanted it to say out "``My whole
sentence is great, isn't it YOUR_USERNAME!``" Why didn't it do what we wanted it
to do?

Each space is considered a "separator" between multiple arguments. The narrate
command only needs one argument (it can take a second argument, but that
argument has a special prefix so we can ignore it for now).

To Denizen, we've given it 7 different arguments and an open quote! It reads the
first "argument" properly, but every "argument" afterwards is ignored and seen
as weird. The single quote character ``'`` in the word ``isn't`` is seen as the
start of an argument, is invalid, and will cause parsing errors. Is there a way
to get the whole sentence to be considered one argument, and to get the single
quote to not cause strange behaviors?

Luckily, there is. If you encase something in quotes, Denizen will automatically
consider the entire quoted segment as one argument. For example, ``Put me in
quotes`` is considered 4 arguments while ``"Put me in quotes"`` is seen as only
one! Below are two acceptable ways to quote an argument.

.. code-block:: dscript
  :name: figure1_3_3
  :linenos:
  :emphasize-lines: 4-5

  a_narrate_command:
      type: task
      script:
      - narrate "My whole sentence is great, isn't it <player.name>!"
      - narrate 'My whole sentence is great, isn<&sq>t it <player.name>!'

.. rst-class:: figurecaption

**Figure 1.3.3** Two ways to quote arguments in a command

Note that when single quotes are used to quote an argument, the ``'`` symbol in
the word ``isn't`` is replaced with ``<&sq>``. This is to prevent Denizen from
prematurely ending the argument mid-sentence and from causing any parsing errors
that may come from the ``'`` at the end of the sentence. Always remember to
escape quote characters inside of a quoted argument (use ``<&dq>`` for double
quotes and ``<&sq>`` for single quotes).

3. Indentation
--------------

One of the most important aspect of writing in dScript is consistent
indentation. Remember to keep a reasonable and consistent indentation pattern.
The indents can be formed using TAB or any even amount of spaces. We strongly
recommend that spaces are used to indent lines rather than TABs.

The example script below demonstrates these conventions well:

.. code-block:: dscript
  :name: _figure1_3_4
  :linenos:

  a_task_script:
      type: task
      script:
      - narrate "Hello, <player.world.name>!"

  another_task_script:
      type: task
      script:
      - narrate "Goodnight, <player.world.name>!"

.. rst-class:: figurecaption

**Figure 1.3.4** An indentation demonstration

In this example, there are **two task scripts** (we will cover what task scripts
are in :doc:`Section 2.3</docs/basics-of-scripting/your-first-task-script>`). If
you were to highlight each script, you would see that each indentation is formed
using 4 spaces.

Indentation clearly tells Denizen which are script containers (the lines that
are not indented) and what belongs to each script container (the lines that are
indented). Indentation will also serve to clearly differentiate sections of
script associated with particular relevant commands (for example, ``if`` and
``foreach``).

.. note::

  You don't always have to use 4 spaces! Indentation using 2, 6, or even 8
  spaces are all perfectly acceptable (indentations using an odd number of
  spaces are not)! Just remember to be consistent and organize your script well.

Always be careful when writing in dScript! If you're not sure if a particular
style of formatting works, it is recommended to test the script on a private
dev server.

|

.. rst-class:: previous-next-table

+-------------------+--------------------+
| | Previous page:  | | Next section:    |
| | |prev-doc|      | | |next-doc|       |
+-------------------+--------------------+

.. |prev-doc| replace:: :doc:`1.2 (The Denizen Folder)</docs/getting-started/denizen-folder>`

.. |next-doc| replace:: :doc:`Section 2 (The Basics of Scripting)</docs/basics-of-scripting/index>`

