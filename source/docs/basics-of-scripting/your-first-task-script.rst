.. _basics-of-scripting your-first-task-script:

=========================
2. Your First Task Script
=========================

This section covers the video “`Setting Up A Local Test Server and Your First
Task Script <https://one.denizenscript.com/denizen/vids/Setting%20Up%20A%20Local%20Test%20Server%20and%20 Your%20First%20Task%20Script>`_”
[#]_ by mcmonkey.

.. note::
  
  The beginning part of the video contains outdated information. You should not
  be downloading or using Craftbukkit. Instead, use the latest Spigot builds
  You can find out more about obtaining a Spigot JAR at
  https://www.spigotmc.org/wiki/buildtools/.

We’ve been using task scripts in every example by now. You know that you can run
them by using the command ``/ex run TASK_SCRIPT_NAME`` in-game. Now what you
need to know is how they work.

Consider the following script:

.. code:: yaml
  :name: figure2_2_1
  :number-lines:

  myscript:
      type: task
      script:
      - narrate "Hello world!"

.. rst-class:: figurecaption

Figure 2.2.1: A simple task script

We know that ``myscript`` is the script’s container name. Therefore, all of the
indented lines underneath “``myscript``” are part of the same script. From
there, we can tell that the script type of ``myscript`` is ``task``, as
indicated by “``type: task``”. For a brief explanation on script container names
and types, refer to :ref:`Section 1.3 (dScript Format)<getting-started
dscript-format>`.

This leaves us with one last thing. The ``script`` section and all of the lines
that start with a dash ``-`` . What are they, and how do they work?

.. todo
  Finish this section

.. [#] https://one.denizenscript.com/denizen/vids/Setting%20Up%20A%20Local%20Test%20Server%20and%20 Your%20First%20Task%20Script
