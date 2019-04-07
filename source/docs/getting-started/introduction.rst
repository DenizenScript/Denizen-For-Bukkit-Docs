=================
1.1. Introduction
=================

Denizen [#footnote-platform]_ is a Spigot plugin that gives you an entire scripting language (**dScript**) to use to
customize your Minecraft server experience. You can add custom behavior to NPCs, create custom commands and items, react
based on events in the world, create a full interactive experience, and more! It can be used for an RPG experience or
simple housekeeping tasks. Your imagination is the limit!

So, what exactly is a script? How should it look? What can we expect of it? What can they do? Will writing a script be
harder than dealing with the pain of having or removing wisdom teeth?

A script is essentially a *section of text that Denizen reads and converts to code*. It grants almost all of the
benefits of coding in Java without the unnecessary complexity and has tools that streamline the scripting process.

Scripts are entirely capable of doing anything within the bounds of Minecraft and can replace a variety of plugins. In
fact, it extends beyond the limits of the Spigot API and therefore can do more than the standard Spigot plugin. It's
lenient to both beginners and developers. Consider it the Swiss army knife of Minecraft servers.

Surprisingly, scripting using Denizen is incredibly painless. It eliminates much of the hassle that comes from coding in
Java and provides an equally competent way of adding new content to your server without additional plugins or mods. Many
others have claimed that scripting in Denizen is significantly faster than writing code that does similar things in
Java. Nice!

All script files follow the dScript format, which shares some features with YAML. For example, indentation is key. Clear
and consistent naming is highly recommended. We will cover more of this in :doc:`Section 1.3 (dScript Format)
<dscript-format>`.

For now, we will assume that you already have a server ready for scripting. If you don't, consider setting up a local
server. You can download BuildTools and view instructions on how to build your own Spigot JAR file on the official
`BuildTools`__ wiki page.

.. __: https://www.spigotmc.org/wiki/buildtools/

.. rubric:: Footnotes

.. [#footnote-platform] "Denizen" throughout this website is used to refer to Denizen 1.x for Bukkit/Spigot. There are
    other versions of Denizen, including Denizen 2.x, which works as a desktop console program and as well on the Sponge
    minecraft server platform. If you use Sponge, see the `Denizen 2 Meta Docs`__ for information on that.

.. __: https://meta.denizenscript.com/
