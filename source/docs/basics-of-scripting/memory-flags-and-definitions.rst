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
