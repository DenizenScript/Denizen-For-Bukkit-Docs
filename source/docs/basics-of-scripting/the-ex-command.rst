=======================
2.2 The ``/ex`` Command
=======================

.. contents::
  :local:

Before We Start
---------------

We used the ``/ex`` command once, in :doc:`Section 2.1
</docs/basics-of-scripting/an-introduction-to-tags>`. It seems important,
doesn't it? If you expected me to say that it's not important, *you're wrong*.

1. What the ``/ex`` Command Is
------------------------------

The ``/ex`` command will be a critical part of your Denizen experience. It can
run scripts for you, let you test a command or two, and possibly save you in a
pinch (though we should probably avoid getting ourselves into sticky situations
anyways). It is one of the most powerful parts of our toolbox, so it is
important that you understand what it does and how to use it.

Simply put, it can run a Denizen command from in-game or via console. Does it
sound underwhelming? Probably. However, it is not to be underestimated.
*Permission to run the* ``/ex`` *command should not be given to any user not
trusted with virtually full control over the server*.

To give you a perspective as to how dangerous it can be in the wrong hands,
consider the following command:

.. code::
  :name: figure2_2_1

  /ex execute as_server "op <player.name>"

.. rst-class:: figurecaption

**Figure 2.2.1** A way for someone to give themselves operator status using the
``/ex`` command

This will run the command ``/op PLAYER_USERNAME`` from the console, effectively
granting the player who runs the command operator status. For most servers,
operator status is the position of full control over the whole server. This is
clearly not ideal if the player running the command is untrustworthy in any way.

Making operators powerless won't help. As long as the player has access to the
``/ex`` command, they can do anything within the limitation of Denizen. As we
mentioned in :doc:`Section 1.1: Introduction
</docs/getting-started/introduction>`, that limit can be higher than you can
see. Hopefully this demonstrates the power that the ``/ex`` command wields.

2. Afterword
------------

For the rest of Section 2, we will largely use the ``/ex`` command as a minor
utility. As you continue to advance through the varying obstacles of scripting,
the ``/ex`` command may prove to be an invaluable assistant. Don't be afraid to
stretch your imagination!

|

.. rst-class:: previous-next-table

+-------------------+-----------------+
| | Previous page:  | | Next page:    |
| | |prev-doc|      | | |next-doc|    |
+-------------------+-----------------+

.. |prev-doc| replace:: :doc:`2.1 (An Introduction to Tags)</docs/basics-of-scripting/an-introduction-to-tags>`

.. |next-doc| replace:: :doc:`2.3 (Your First Task Script)</docs/basics-of-scripting/your-first-task-script>`
