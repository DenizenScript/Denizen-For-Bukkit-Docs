=================================
2.6 Memory: Flags and Definitions
=================================

This section covers the video "`Memory (Flags and Definitions)`__" by mcmonkey.

.. __: https://one.denizenscript.com/denizen/vids/Memory%20(Flags%20and%20Definitions)

.. contents:: Table of Contents
    :local:

.. warning::

    This section is incomplete!

.. admonition:: Syntax Updated

    The video uses the term "``global``". All references to "``global``" flags and tags are now deprecated. You should
    use "``server``" instead. We will still use the example found in the video, but corrected to reflect this change.

Before We Start
---------------

Most formal coding lessons would normally start with a concept called "**variables**" before they jump into the
:guilabel:`if` statement/command. Naturally, most programs cannot be made if there were no way to store all sorts of
information, from numbers to lists to full virtual objects (or references to said objects). Variables achieve that.

Some variables are designed to be *temporary*, and will eventually be automatically deleted. Others are designed to do
the opposite: *stay until you manually delete it*. Of course, Denizen provides a similar concept in the form of
definitions and flags. **Definitions** are equivalent to temporary/local variables, and **flags** are equivalent to
permanent/global variables.

1. Definitions
--------------

Let's say that you generate a random number and want to reuse that number in your script multiple times. If we used the
tag ``<util.random.int[1].to[5]>`` over and over, each new time we use that tag will result in a different random
number.

To illustrate what I mean, consider this script:

.. code-block:: dscript
    :name: figure2_6_1
    :linenos:
    :emphasize-lines: 5

    script2:
        type: world
        events:
            on player breaks sand:
            - narrate "<util.random.int[1].to[5]> <util.random.int[1].to[5]>"
            - determine cancelled

.. rst-class:: figurecaption

**Figure 2.5.1** Using multiple ``<util.random.int[1].to[5]>`` tags

Whenever you break a sand block, you will see *two different randomly chosen numbers* in your chat. What if we want both
of them to display the same exact number? By recording that number somewhere, of course. But that leads to another
question. *How* can we store that number?

The answer is definitions. **Definitions** will take a value and successfully return its stored value every time it's
called. To store a value, you need to use the :guilabel:`define` command. The syntax is:

.. code-block:: dscript
  
    - define [<id>] [<value>]

To get the value of a definition, you would use the tag:

.. code-block:: dscript

    <definition[<id>]>

It's a bit of a pain to write "definition" out every time we want to get a definition, so we'll use the shorthand
version of the tag, ``<def[<id>]>``.

.. caution::

    Some of the older scripts use the ``%<id>%`` form of definitions. This is deprecated syntax! Use the modern
    ``<def[<id>]>`` syntax instead!

To demonstrate how the :guilabel:`define` command and ``<def[<id>]>`` work, we will revise :ref:`Figure 2.6.1
<figure2_6_1>` a bit. Consider this edit:

.. code-block:: dscript
    :name: figure2_6_2
    :linenos:
    :emphasize-lines: 5

    script2:
        type: world
        events:
            on player breaks sand:
            - define random <util.random.int[1].to[5]>
            - narrate "<def[random]> <def[random]>"
            - determine cancelled

.. rst-class:: figurecaption

**Figure 2.6.2** Using definitions to store a random integer

Every time you break your sand block, you should notice an interesting phenomenon. The two numbers you get are now
exactly the same number. The :guilabel:`define` command on line 5 took the result of the given tag and stored that
result to the definition ``random``. That's pretty neat, isn't it?

If you don't believe me, you can run as many :guilabel:`narrate` or :guilabel:`announce` commands as you want. The
``<def[random]>`` tag will only produce a new random number every time you break a sand block.

Well, what if we wanted to access that definition after the script has finished running? Well... we can't.

Every time you break a block, the script block is run. When the script block has finished running, *the definition is
deleted*. For programmers, this is why definitions are analogous to temporary local variables.

Let's ask a better question. What if we wanted to have a number that counts how many times you've tried to break a sand
block? Definitions definitely can't help us here. We need a more permanent sort of way to store values. We need *flags*.

2. Flags
--------

**Flags** also store values, though it has a few of its own quirks. To do basic scripting, you won't need to know most
of the things you can do with it. We will instead cover some very basic information about flags.

.. contents:: Contents
    :local:

2A. Flags and Storing Data
~~~~~~~~~~~~~~~~~~~~~~~~~~

As we have already alluded to, flags are a *method of which to store persistent data*. That is, you can get the value
stored to your flag, even after a script has finished running. That's real convenient, isn't it?

To store any value to a flag, you must use the :guilabel:`flag` command. The syntax is:

.. code-block:: dscript
    :name: flag_cmd_syntax

    - flag ({player}/npc/server/<entity>) [<name>([<#>])](:<action>)[:<value>] (duration:<value>)

That's quite a lot to swallow, isn't it? However, we're only dealing with the *basics* of flags in this section. We can
ignore a lot of those arguments and just focus on a few. This section will deal with the :guilabel:`flag` command as if
this were its syntax:

.. code-block:: dscript
    :name: flag_cmd_syntax_simple

    - flag ({player}/server) [<name>](:<action>)[:<value>]

So now we know about the flag command and the extent to which we'll cover it. What about getting the value of a flag?
Well, there *are* tags for that. It's just... a little more complicated to explain. For now, we'll focus on what a flag
is before we jump into those particular details.

As mentioned before, flags are a way to store values that persist over multiple scripts. That is, the value of the flag
can be freely accessed and modified from any script. They are not localized in the same way that definitions are.

To clarify what I mean, let's demonstrate the difference between flags versus definitions. Consider this script:

.. code-block:: dscript
    :name: figure2_6_3
    :linenos:
    :emphasize-lines: 5-6

    script2:
        type: world
        events:
            on player breaks sand:
            - define string "I am a definition!"
            - flag server "string:I am a flag!"
            - determine cancelled

.. rst-class:: figurecaption

**Figure 2.6.3** A :guilabel:`define` and :guilabel:`flag` command

If you were to break a block of sand, three things should happen. First, the :guilabel:`define` command will create a
definition with the name ``string`` and store the sentence ``I am a definition!`` to the definition ``string``. Then,
the :guilabel:`flag` command will create a flag with the name ``flag_string`` and store the sentence ``I am a flag!`` to
the flag ``flag_string``. Finally, the :guilabel:`determine` command will run.

.. note::

    Notice how in the :guilabel:`flag` command, the quotes go around the entire third argument. The quotes do not go
    around just the sentence. Reread :doc:`Section 1.3 </docs/getting-started/dscript-format>` for more information.

If you need a refresher on what this :guilabel:`determine` command is used for, refer to :ref:`Figure 2.5.1
<figure2_5_1>` of :doc:`Section 2.5 </docs/basics-of-scripting/the-if-command>`.

If you remember from :doc:`Section 2.3 </docs/basics-of-scripting/the-ex-command>`, the ``/ex`` command can run any
Denizen command. Well, why don't we put it to good use? We'll use it to perform two separate :guilabel:`narrate`
commands.

After you have broken a sand block, attempt to run the following commands in-game:

.. code::
    
    /ex narrate <def[string]>
    /ex narrate <server.flag[string]>

If you run those two commands in that exact order, you can expect to see something similar to what's depicted below.

.. image:: /_static/images/f2.6.4_result-of-f2.6.3.png
    :name: figure2_6_4
    :width: 90%
    :align: center
    :alt: result of figure 2.6.3

.. rst-class:: figurecaption

**Figure 2.6.4** The expected results when narrating the definition and flag from :ref:`Figure 2.6.3 <figure2_6_3>`

Notice how the definition is invalid (and returns a null value), while the flag returns a number. If you break a sand
block again, the definition will remain invalid while the flag will still return a number. Now why is that?

Remember that definitions are synonymous to *local, temporary variables*. They exist only in the script they're in.
Flags are not affected by this limitation. You can get the value of a flag, even after a script has finished running.
Useful, isn't it?

Of course, you can do a bit more with flags than you can with definitions.

2B. Math With Flags
~~~~~~~~~~~~~~~~~~~



2C. Server vs. Player
~~~~~~~~~~~~~~~~~~~~~



2D. Flag Tags
~~~~~~~~~~~~~



2E. Removing a Flag
~~~~~~~~~~~~~~~~~~~



Afterword
---------


