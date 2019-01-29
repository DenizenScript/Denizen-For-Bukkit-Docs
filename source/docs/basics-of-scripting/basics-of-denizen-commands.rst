==================================
2.2 The Basics of Denizen Commands
==================================

.. contents:: Table of Contents
    :local:

Before We Start
---------------

You know that tags are a way to retrieve information about something. Now what if we want to *do* something? You know,
kill a player. Put that zombie in its place with a lightning strike. Maybe even just say hi to a player.

This all can be accomplished using something that we've been referring to and using almost nonstop since :doc:`Section
1.2 </docs/getting-started/denizen-folder>`. Commands!

Command Syntax
--------------

In Denizen, commands are incredibly straightforward. They consist of the **command name** and the **arguments**. As
covered in :doc:`Section 1.3 </docs/getting-started/dscript-format>`, the arguments in a command are separated by
spaces.

Commands can have *required* arguments and *optional* arguments. If you fail to specify any required arguments, Denizen
will throw an error. However, optional arguments can be left out.

Let's look at the :guilabel:`narrate` command as a simple example. The basic syntax is outlined below. Additional
information about the :guilabel:`narrate` command can be found `here`__.

.. __: https://one.denizenscript.com/denizen/cmds/narrate

.. code-block:: dscript

    - narrate [<text>] (targets:<player>|...) (format:<name>)

As we can see, there is one required argument and two optional arguments for the :guilabel:`narrate` command. For more
information on how to read the command documentation, refer to `the command syntax language explanation`__.

.. __: https://one.denizenscript.com/denizen/lngs/command%20syntax

Optional Arguments
------------------

What would happen if we exclude the two optional arguments? Well, we've already been doing that in :doc:`Section 1.3
</docs/getting-started/dscript-format>` and :doc:`Section 2.1 </docs/basics-of-scripting/an-introduction-to-tags>`. But
we should look at a fresher example and fully examine the command.

Consider this very simple script:

.. code-block:: dscript
    :name: figure2_2_1
    :linenos:
    :emphasize-lines: 4

    a_task_script:
        type: task
        script:
        - narrate "One argument"

.. rst-class:: figurecaption

**Figure 2.2.1** A simple :guilabel:`narrate` command


