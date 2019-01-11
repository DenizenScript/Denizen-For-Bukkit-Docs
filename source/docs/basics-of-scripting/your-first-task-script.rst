==========================
2.3 Your First Task Script
==========================

This section covers the video "`Setting Up A Local Test Server and Your First
Task Script`_" by mcmonkey.

.. _Setting Up A Local Test Server and Your First Task Script:
  https://one.denizenscript.com/denizen/vids/Setting%20Up%20A%20Local%20Test%20Server%20and%20Your%20First%20Task%20Script

.. contents::
  :local:

.. note::
  
  The beginning part of the video contains outdated information. You should not
  be downloading or using Craftbukkit. Instead, use the latest Spigot builds.
  You can find out more about obtaining a Spigot JAR at
  https://www.spigotmc.org/wiki/buildtools/.

Before We Start
---------------

We've been using task scripts in every example by now. To run a task script from
in-game, you can run the command ``/ex run TASK_SCRIPT_NAME``. Now what you need
to know is how they work.

Consider the following script:

.. code-block:: dscript
  :name: figure2_3_1
  :linenos:

  myscript:
      type: task
      script:
      - narrate "Hello world!"

.. rst-class:: figurecaption

**Figure 2.3.1** A simple task script

We know that ``myscript`` is the script's container name. Therefore, all of the
indented lines underneath "``myscript``" are part of the same script. From
there, we can tell that the script container type of ``myscript`` is ``task``,
as indicated by "``type: task``". For a brief explanation on script container
names and types, refer to :doc:`Section 1.3
</docs/getting-started/dscript-format>`.

This leaves us with one last thing. The ``script`` section and all of the lines
that start with a dash ``-`` . What are they, and how do they work?

1. The "script" Section
-----------------------

For task scripts, the ``script`` section is the section that contains *all of
the script that Denizen should run*. Each line that starts with a ``-`` is a
Denizen **command**. Each command is run in the order that they are written in.
Consider the following example:

.. code-block:: dscript
  :name: figure2_3_2
  :linenos:

  myscript:
      type: task
      script:
      - narrate "This should be the first thing you see."
      - narrate "And this shall be the second thing you see."


.. rst-class:: figurecaption

**Figure 2.3.2** A task script with two commands

When you load this script to your server and run it in-game using ``/ex run
myscript``, you will see those two lines printed to your chat. The image below
shows the expected result:

.. image:: /_static/images/f2.3.3_result-of-f2.3.2.png
  :name: figure2_3_3
  :width: 90%
  :align: center
  :alt: result of figure 2.3.2

.. rst-class:: figurecaption

**Figure 2.3.3** The expected results when running the script in :ref:`Figure
2.3.2<figure2_3_2>`

As you can see, the script runs every command in order. This is true for every
type of Denizen script, not just task scripts. So don't worry about a script
suddenly running all of the commands in a script section in a completely
random order. That should never happen, ever. Very heavy emphasis on *never*.

Now we know everything that's in a task script. Great! But, despite covering all
of this, there is one thing we didn't really cover up until now. *What is a
task script?*

2. What Are Task Scripts?
-------------------------

Quite simply, task scripts are just script containers with script in it. There
is no way for a task script to run automatically. This is why you had to use
``/ex run TASK_SCRIPT_NAME`` to run the contents of each task script while
in-game. The script command equivalent is ``- run TASK_SCRIPT_NAME``.

To illustrate how useful task scripts are, let's come up with a situation where
*not* having task scripts would be painful. Imagine having to do something in
Denizen, and multiple scripts require a certain segment of script to be used
over and over again. Our first solution is to copy and paste the same 20 lines
of script over and over again.

Now, imagine that you find out that the lines of script you copied and pasted
has a bug in it. In order to fully fix the issue, you will need to find every
line where you had copied and pasted those 20 lines of script. That's just
unnecessary effort.

Task scripts make it so that instead of copying and pasting multiple lines of
script, we only ever have to copy and paste one line of script without losing
any functionality. If there is a bug in the script, you will only ever need to
edit the task script once and your issue is resolved. Nice, easy, and simple!

|

.. rst-class:: previous-next-table

+-------------------+-----------------+
| | Previous page:  | | Next page:    |
| | |prev-doc|      | | |next-doc|    |
+-------------------+-----------------+

.. |prev-doc| replace:: :doc:`2.2 (The /ex Command)</docs/basics-of-scripting/the-ex-command>`

.. |next-doc| replace:: :doc:`2.4 (The if Command)</docs/basics-of-scripting/the-if-command>`
