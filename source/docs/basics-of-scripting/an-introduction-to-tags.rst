===========================
2.1 An Introduction to Tags
===========================

This section covers the video "`Your First Tags`_" by mcmonkey4eva.

.. _Your First Tags: https://one.denizenscript.com/denizen/vids/Your%20First%20Tags

.. contents::
  :local:

Before We Start
---------------

You were already exposed to tags in :doc:`Section 1.3
</docs/getting-started/dscript-format>`, as all of the examples there used tags.
However, we never quite clarified what they are and what they do. And of course,
your question by now should be "*What are tags, and what can they do?*"

First, let's prepare for the upcoming example. Start your server and log in.
When you're in your server and are ready to do some live Denizen testing, come
back here and continue this tutorial.

For now, let's look at this example:

.. code-block:: dscript
  :name: figure2_1_1
  :linenos:

  myscript:
      type: task
      script:
      - narrate "Hello world!"
      - narrate "Hello, player!"

.. rst-class:: figurecaption

**Figure 2.1.1** A simple task script

Put this script in the ``./scripts/`` folder and load it by using the command
``/denizen reload scripts``. With that, you can run this script quickly and
simply by using the command ``/ex run myscript`` in-game.

If you followed the steps above, you would probably get "Hello world!" and
"Hello, player!" in your chat. But what if we wanted to replace "player" with
your username instead? Would that not be great (and also a really basic feature
of any scripting language made for Minecraft servers)? You know the answer to
this question already: *Use tags*!

Using Tags
----------

Tags are defined by relevant text between the less than symbol ``<`` and the
greater than symbol ``>`` (we'll refer to these two symbols as *tag marks*). For
example, ``<player.name>`` is a tag that returns some player's name. In the
context of our example, it will return your username.

But nothing's worth believing without seeing, so let's put it to the test. You
can use this example:

.. code-block:: dscript
  :name: figure2_1_2
  :linenos:
  :emphasize-lines: 5

  myscript:
      type: task
      script:
      - narrate "Hello world!"
      - narrate "Hello, <player.name>!"

.. rst-class:: figurecaption

**Figure 2.1.2** A simple task script that uses a tag

When you put this in your ``./scripts/`` folder and run the script, you should
get "Hello world!" and "Hello, *YOUR_USERNAME*!" It worked, thanks to tags!

Tags are a way to automatically fill in information in a script. As mentioned
above, ``<player.name>`` is filled in with the player's name (in the context of
the example, your username). But tags can do much more than just give back some
unchanging bit of text. For example, let's say we want a random number from 1 to
5. How can we accomplish this?

We can use the tag ``<util.random.int[1].to[5]>``. If you doubt it, we can
always test it! Let's use this script as our example:

.. code-block:: dscript
  :name: figure2_1_3
  :linenos:
  :emphasize-lines: 6

  myscript:
      type: task
      script:
      - narrate "Hello world!"
      - narrate "Hello, <player.name>!"
      - narrate "Your lucky number is <util.random.int[1].to[5]>"

.. rst-class:: figurecaption

**Figure 2.1.3** A simple task script with a random number tag

If you load this script into your server, you should get random selected numbers
from 1 to 5 each time you run the script. Hurrah!

In [TODO: ADD SECTION REFERENCE], we will cover more on how tags are read. If
you want to look up a full list of tags, you can hop on over to our Discord
server and start by using ``!t SEARCH_TERM`` (for example, ``!t player.name``).
Alternatively, you can see the full list of tags at the `official documentation
site\'s tag page`_.

.. _official documentation site\'s tag page: https://one.denizenscript.com/denizen/tags

|

.. rst-class:: previous-next-table

+------+-----------------+
|      | | Next page:    |
|      | | |next-doc|    |
+------+-----------------+

.. |next-doc| replace:: :doc:`2.2 (The /ex Command)</docs/basics-of-scripting/the-ex-command>`
