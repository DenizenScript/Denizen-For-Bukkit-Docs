======================
1.2 The Denizen Folder
======================

When you first start (or restart) your server with Denizen installed, the
Denizen folder should be created under ``./plugins/``. When you open your 
``./plugins/Denizen/`` folder, you should see something similar to this:

.. image:: /_static/images/denizen-directory-1.png
  :name: figure1_2_1
  :scale: 60
  :align: center
  :alt: A depiction of the Denizen plugin's directory.

.. rst-class:: figurecaption

**Figure 1.2.1** The ``plugins/Denizen/`` folder

The ``entities.yml``, ``maps.yml``, ``notables.yml``, ``saves.yml``, and
``scoreboards.yml`` files all hold various bits of data directly related to a
variety of commands in Denizen. It is *not recommended to manually edit the
values of any of these files*. All relevant data should be handled through a
script.

You can drag and drop ``.schematic`` files into the ``./schematics/`` folder and
``.mid`` files into the ``./midi/`` folder. The files in those folders are
directly used by the ``schematic`` and ``midi`` commands, where the
``schematic`` command can save and load ``.schematic`` files to the
``./schematics/`` folder and the ``midi`` command can play ``.mid`` files
directly from the ``./midi/`` folder.

And finally, the most important folder of all: ``./scripts/``! This folder is
where you put all of your scripts, and is the first folder Denizen checks for
all related scripts. You can create multiple script files in it, along with
additional subfolders to organize your scripts. Denizen will check every single
folder and ``.yml`` file in ``./scripts/`` to load all scripts possible!

|

.. rst-class:: previous-next-table

+-------------------+-----------------+
| | Previous page:  | | Next page:    |
| | |prev-doc|      | | |next-doc|    |
+-------------------+-----------------+

.. |prev-doc| replace:: :doc:`1.1 (Introduction)</docs/getting-started/introduction>`

.. |next-doc| replace:: :doc:`1.3 (dScript Format)</docs/getting-started/dscript-format>`
