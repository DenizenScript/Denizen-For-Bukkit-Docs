==================================
2.2 The Basics of Denizen Commands
==================================

.. contents:: Table of Contents
  :local:

.. warning::

  This section is incomplete!

Before We Start
---------------

You know that tags are a way to retrieve information about something. Now what
if we want to *do* something? You know, kill a player. Put that zombie in its
place with a lightning strike. Maybe even just say hi to a player.

This all can be accomplished using something that we've been referring to and
using almost nonstop since :doc:`Section 1.2
</docs/getting-started/denizen-folder>`. Commands!

In Denizen, commands are incredibly straightforward. They consist of the
**command name** and the **arguments**. As covered in :doc:`Section 1.3
</docs/getting-started/dscript-format>`, the arguments in a command are
separated by spaces.

Commands can have *required* arguments and *optional* arguments. If you fail to
specify any required arguments, Denizen will throw an error. However, optional
arguments can be left out.

Let's look at the :guilabel:`narrate` command as a simple example.

For example, let's look at a :guilabel:`narrate` command:

.. code-block:: dscript
  :name: figure2_2_1
  :linenos:
  :emphasize-lines: 4

  a_task_script:
      type: task
      script:
      - narrate wee

.. rst-class:: figurecaption

**Figure 2.2.1** A simple :guilabel:`narrate` command
