===================================
2.2. The Basics of Denizen Commands
===================================

.. contents:: Table of Contents
    :local:

Before We Start
---------------

You know that tags are a way to retrieve information about something. Now what if we want to *do* something? You know,
kill a player. Put that zombie in its place with a lightning strike. Maybe even just say hi to a player.

This all can be accomplished using something that we've been referring to and using almost nonstop since :doc:`Section
1.2 </docs/getting-started/denizen-folder>`. Commands!

1. Command Syntax
-----------------

In Denizen, commands are incredibly straightforward. They consist of the **command name** and the **arguments**. For
more information regarding what is considered an argument, refer to :doc:`Section 1.3
</docs/getting-started/dscript-format>`.

Let's look at the :guilabel:`give` command as a simple example. The basic syntax is outlined below. Additional
information about the :guilabel:`give` command can be found `here`__.

.. __: https://one.denizenscript.com/denizen/cmds/give

.. code-block:: dscript

    - give [money/xp/<item>|...] (quantity:<#>) (engrave) (unlimit_stack_size) (to:<inventory>) (slot:<slot>)

The first part of any Denizen command is the *command name*. This command's name is, of course, ":guilabel:`give`". Each
new bit of text after the command name are the *arguments*.

Commands can have *required* arguments and *optional* arguments. If you fail to specify all of the required arguments,
Denizen will throw an error. Optional arguments can be left out.

As we can see, there is one required argument and multiple optional arguments for the :guilabel:`give` command. For more
information on how to read the command documentation, refer to `the command syntax language explanation`__.

.. __: https://one.denizenscript.com/denizen/lngs/command%20syntax

2. Command Arguments
--------------------

When we write a command, what happens when we exclude certain arguments? What will Denizen do if we don't tell it to
do certain things? Not to worry, it won't start throwing errors everywhere.

Consider this very simple script:

.. code-block:: dscript
    :name: figure2_2_1
    :linenos:
    :emphasize-lines: 4

    task_script:
        type: task
        script:
        - give i@diamond

.. rst-class:: figurecaption

**Figure 2.2.1** A simple :guilabel:`give` command

As you can see, there is only one argument given to the :guilabel:`give` command. In plain terms, this :guilabel:`give`
command gives you one diamond item, provided that you are playing on your server and are running this script using ``/ex
run task_script``.

What if we started including the other optional arguments? For example, the ``quantity`` argument?

Consider this edit of :ref:`Figure 2.2.1 <figure2_2_1>`:

.. code-block:: dscript
    :name: figure2_2_2
    :linenos:
    :emphasize-lines: 4

    task_script:
        type: task
        script:
        - give i@diamond quantity:10

.. rst-class:: figurecaption

**Figure 2.2.2** A simple :guilabel:`give` command with a ``quantity`` argument

This give command will, in plain language, give us ten diamonds. When we didn't specify a quantity, we only got one
diamond.

When the optional arguments are left unspecified, Denizen will fill in the gaps for you. Specifying the optional
arguments will allow you to further customize your experience. Neat, isn't it?

In some cases, the default behavior may not be very clear. In that case, the Denizen command documentation will
explicitly note which value is considered the default value of a particular optional argument. A good example of a
command that has such behavior is the :guilabel:`title` command (documentation can be found `here`__).

.. __: https://one.denizenscript.com/denizen/cmds/title

Afterword
---------

With this, you know of the two most fundamental parts of a script block: tags and commands. We can finally start
learning about unique script containers, how to use them, and what to do with them.
