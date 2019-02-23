# Contribution Guidelines

Thank you for considering contributing to the Denizen text tutorials!

suspic (@MusicScore) is currently heading the project, under the supervision of mcmonkey (@mcmonkey4eva). It's a good
idea to refer to either of them if you have any specific questions that are not covered by this contribution guideline
document.

suspic (@MusicScore) will mainly be reviewing any pull requests made for clarity, purpose, and precision. Be mindful of
suggested edits, but don't be afraid of providing an explanation as to why you wrote something a certain way. Refusing
an explanation or creating confusing pull requests with no attempt at justifying questionable behavior will result in
the closing of your pull request.

Contents:

1. [General Rules](#1-general-rules)
2. [rST](#2-rst)
3. [General Formatting](#3-general-formatting)
4. [Headers](#4-headers)
5. [Tables](#5-tables)
6. [Figures](#6-figures)
7. [Links](#7-links)

**NOTE:** If more concerns are brought up during the development of the text documentation, this guideline will update
to reflect any new changes new contributors should know.

## 1) General Rules

1. **Keep your text formatting as simple as possible.** Don't try to do too many fancy things in the source when a
    simpler version would suffice. However, do not avoid using rST features and do not sacrifice backend readability.

2. **Maintain a consistent conversational tone.** This is not a textbook or an academic paper. A formal tone is not
    required at all. Most of the text tutorials should be written in a casual tone, without losing any explanation or
    authority.

3. **Be sure to explain ideas, concepts, and tools with as much depth as possible** with respect to the user's expected
    literacy in Denizen scripting. For example, any subsection of Section 2 (Basics of Scripting) should have a very
    in-depth explanation regarding the topics that are being introduced to the user. For more advanced sections,
    explanation of basic concepts can be ignored.

4. **Use proper grammar and spelling.** When contributing to the docs in English, always capitalize and use sane
    sentence structure. For documentation contributions in other languages, discuss on the Discord server before making
    commits.

5. **Obey conventional dScript language syntax.** Do not use shorthands, keep variable names clean and concise, use
    quotes sparingly, and use commands and tags that will quickly accomplish the goal. Avoid overengineering
    overcomplication, or over-optimization of script. Remember that this is a *public text tutorial*. We should be
    encouraging proper script writing. The user can decide for themselves if they want to do black magic with their
    scripts.

    If you're unclear as to how to format or write your contributed script, ask on the Discord server.

6. **Keep figures and examples short and concise.** In the earlier sections, use of a full script example and images may
    be necessary. As the reader advances, they will not require as many full script examples or images except for
    absolutely necessary clarification of certain principles.

7. **Use full example scripts whenever possible.** Unless the focus of a figure/example is on a few particular lines of
    a very long script, the entire script should be displayed so the user has a grasp as to where they are in the
    script. If you are displaying a script snippet from a larger script, be sure to also include context around the
    highlighted lines so that users can more easily track where they should be.

8. **Keep each section and subsection on-topic.** Covering details not relevant to a section is not allowed at all.
    Don't try to cover too much under a single header. Split a subsection into smaller sections if you need to.

9. **Name and write sections with care.** Make sure that each subsection is specific enough so that it actually warrants
    its own section on a page. Name each subsection appropriately. An extremely generic name or an all-in-one page
    is strongly discouraged.

10. **Avoid altering CSS, HTML, or JavaScript components without prior approval.** Discussion on the Discord server
    should be done before any edits to the CSS/HTML/JavaScript are considered.

11. **Always include a toctree in each `index.rst` file.** Each page should inevitably link back to the main `index.rst`
    file through toctrees. Be sure to properly link pages together and ensure proper navigation.

Notes:

- suspic (@MusicScore) personally prefers that all variable names (definition names, flag names, YAML IDs, etc.) be
    kept lowercase, with optional underscores. Denizen is case insensitive for such things, so it's better to encourage
    use of clear and unique naming. For example, `<def[helloWORLD]>` and `<def[HELLOworld]>` are considered the same
    definition, so `<def[hello_world]>` or `<def[helloworld]>` would make more sense.

- mcmonkey (@mcmonkey4eva) said on Discord to avoid overuse of dObject notation in example scripts.

- When referencing a value from a Java enum, such as a sound name, try to keep the entire enum string as all
    uppercase. Even though status effects are technically not Java enums, it is best to keep the names of status effects
    all uppercase as well.

- When contributing to Sections 2 and 3, remember that the expected audience has *no idea what they're doing*. They are
    just getting into Denizen. Keep your explanations sufficiently long such that all of the concepts behind what is
    being taught is conveyed to the reader. Since Section 4 is a transition from beginner's basics to more advanced
    concepts, an in-depth explanation would not be required except for cases where a user should not be reasonably
    expected to know how something works.

[To Top](#contribution-guidelines)

## 2) rST

rST is the main markup language used to create the documentation. It is highly recommended to know about the following
topics before continuing:

- Directives
- Roles
- Hyperlink references and hyperlink targets
- Anonymous hyperlinking
- Numbering and automatic numbering
- Footnotes and automatic footnotes
- Grid tables
- Headers
- Comments

Most of this information can be derived from viewing and comparing the displayed webpage and the raw source files of
this site: <https://sphinx-rtd-theme.readthedocs.io/en/stable/>.

Other syntactical things include in-line literals (` ``text`` `), italicizing (`*text*`), and boldface (`**text**`).
Substitutions *may* be used, but it will most likely not be necessary.

There are some Sphinx-specific directives and roles that will be used throughout, such as `:ref:` and `:doc:`

[To Top](#contribution-guidelines)

## 3) General Formatting

### Char Limit

For all paragraphs, visible text sections, and tables, you should obey a 120-character-visible line limit. That is, each
line should only ever have a maximum of 120 visible characters, including whitespace between each visible character. Any
trailing whitespace does not count, and leading whitespace should not exist.

For example:

```
[Beginning of line]               ....             [120-char limit]
V                                                                 V

Lorem ipsum dolor sit amet,       ....     metus suscipit faucibus.
Donec tincidunt risus libero,     ....     Sed ac pulvinar risus.
Nam porttitor metus quis leo      ....     congue ac congue id,
vulputate rutrum risus.           ....     varius ac mauris in,

+----------------------------              -----------------------+
| Table header                    ....                            |
+============================              =======================+
| value                           ....                            |
+----------------------------              -----------------------+
```

Notice how the `V` tick is directly aligned with the last visible character of the first line and the last line of the
table, and how each line that does not have exactly 120 total visible characters (including whitespace between
words/characters) ends at less than the 120th column of the text file. No one line of text that is visible for frontend users exceeds 120 characters.

For directives or targets that are usually hidden, the line can exceed 120 characters to preserve the integrity of the
expected input. For example, a URL may exceed 120 characters. The hyperlink target can then ignore the 120-char limit.

This is to ensure readability in the source files while allowing each file to remain at a more reasonable length. The
historically used 80-char limit could barely fit many valuable tables and figures, so I made the decision (with some
encouragement from mcmonkey) to use 120 characters instead.

### Headers

Never use special characters or text formatting in headers. Use of untypable characters, boldface, italics, literals,
etc., will not be allowed.

### Simplicity and Readability

All text should be kept readable and simple. Overuse of obscure or extravagant words is strongly discouraged.

Overuse of complicated rST features that can be replicated with simpler rST markup will result in the pull request being
denied. Anything done to the source files that results in the raw text files being unreadable will result in the pull
request being denied.

Maintaining the conventions outlined in this contributor's guide will greatly help with readability. The more consistent
the source files, the easier it is for contributors to add onto the existing contents.

### Literals and Terminology

When a term is meant to be an excerpt from a script, is a term specific to dScript, or is a tag, use literals, like so:
` ``term`` `.

When a command name is being used, use the `:guilabel:` role. For example: ``:guilabel:`repeat` ``.

Use a non-figure code block directive to display command syntax. For example:
```
.. code-block:: dscript

    - narrate [<text>] (targets:<player>|...) (format:<name>)

```

[To Top](#contribution-guidelines)

## 4) Headers and Filenames

### Header Formatting

The highest level header should be the section number and name. For most pages, it will most likely look like this:

```
========================
10.4 The Art of Slapping
========================
```

Every header to denote a subsection of the page should use the second level header. If the subsection covers an
important topic, broad topic, or has substantial information in it, it should be numbered. For example:

```
1. Raising Your Hand
--------------------

content content content

2. Bringing the Hand Down on Your Enemies
-----------------------------------------

even more content
```

**NOTE** If the page only has one important subsection, numbering the subsection header is not required.

If the subsection is a preface of some sort, there are a few acceptable ways to name the section. Acceptable names
include, but are not limited to,

- Before We Start
- Introduction
- Preface

The preface and afterword of a section should not be numbered.

<br>

If you have a subsection of a subsection, it should be numbered as `<#><CHAR>`, where `<#>` is the subsection's number
and `<CHAR>` is a letter to identify the sub-subsection. For example:

```
3. Savoring Your Victory
------------------------

.. contents::
    :local:

3A. Enjoying Your Dominance
~~~~~~~~~~~~~~~~~~~~~~~~~~~

content content content

3B. If They Retaliate
~~~~~~~~~~~~~~~~~~~~~

content content content
```

### Filenames

For folders, the folders' names should be identical or similar to the major section's name. For example, the folder
name for Section 10 may be `proper-physical-expressions` if Section 10 was named "Proper Physical Expressions".

<br>

All "table of content" files for each major section should be named `index.rst`. There are no exceptions.

<br>

For documentation files, the files' names should be identical or similar to the section's name. For example, the file
name for Section 10.4 would be `the-art-of-slapping.rst`.

In cases where a filename may become too large or inconvenient, dropping unnecessary words may be allowed. For example,
`art-of-slapping.rst` is an acceptable alternative to `the-art-of-slapping.rst`. However, `art-slapping.rst` is not an
acceptable alternative, as the file's name does not sufficiently match or describe the section's name.

To clarify the above, consider these possible meanings one can derive from "`art-slapping`":

1. Creating a painting by slapping the canvas with paint-covered hands
2. An instruction set on how to slap
3. How to slap someone or something as an expression of art

[To Top](#contribution-guidelines)

## 5) Tables

All tables should have a header section and meaningful data. Tables without a header or tables with simple data should
not be created without proper justification.

Most tables should be displaying information. For those tables, apply the `table-info-display` class to the table by
using the `rst-class` directive. For example:

```
.. rst-class:: table-info-display

+---------------------------+--
| Super Important Info      |       ...
+===========================+==
| term                      |       ...
+---------------------------+--
| | a sentence with         |       ...
|   multiple lines          |       ...
+---------------------------+--
```

In cases where a cell may have more than a few words, use line blocks to enforce consistent text styles between cells
along the same column.

If you wish to create a table with a different purpose or formatting (for example, a two-way table), please properly
justify why the addition is necessary.

**DO NOT** use simple tables or any table directive! Grid tables are much more clear on what cells belong to which cell
and column.

[To Top](#contribution-guidelines)

## 6) Figures

All images should be considered figures. All code blocks with any significant bit of code/script should be considered
figures. Any code block used to display syntax should generally not be considered figures.

When you create a figure, you must create a reference link back to the figure, regardless of if the figure will be
linked in the future or not. You must include a figure caption underneath a figure.

**DO NOT USE THE FIGURE DIRECTIVE**. We already have a reliable way to display and link back to `figure`-type code
blocks and images. There is no point in using the `figure` directive, and any use of it will result in requests to
remove the figure directive and replace it with an appropriate `code-block` or `image` directive.

### Code Block Figures

Generally speaking, the following is the ideal way to formulate a `code-block` figure:

```
.. code-block:: <CODE_LANG>
    :name: <FIGURE_ID>
    [:linenos:/:linenos-start: <#>]
    (:emphasize-lines: <LINES>)

    <CODE>

.. rst-class:: figurecaption

**Figure <FIGURE_NUM>** <description>
```

The `<CODE_LANG>` should almost always be `dscript`, unless you really need to use another language's syntax
highlighting for some purpose.

The `<FIGURE_ID>` should **ALWAYS** be formatted as `figure#_#_#`. The first `#` represents the major section, the
second `#` represents the subsection, and the last `#` represents the ID of the figure. Technically speaking, each
figure should be named in increasing numerical order. For example, three figures in Section 10.4 will have their names
set to `figure10_4_1`, `figure10_4_2`, and `figure10_4_3`, in order.

If the code block should start at line 1, you can simply use the `:linenos:` option. If the code block must start at a
line that is not the first line, you can instead just use `:linenos-start: <#>`, where `<#>` is the line number. For
example, if a figure is expected to show only lines 6 to 10 of the script, you would use `:linenos-start: 6` and only
write 5 lines of script.

The `<LINES>` denotes which lines should be highlighted, if any. It can be formatted as `#` (one line), `#-#` (multiple
lines), and `#-` (from that line to the end). You can use a comma separated list for multiple line specifiers. For
example, `1,5-10,50-` will highlight line 1, then highlight lines 5 to 10, the highlight every line from 50 onwards.

The `:emphasize-lines:` option is *optional*. It should not be included if the reader is not expected to be looking at
a specific line or lines from the code block.

The `<FIGURE_NUM>` should be formatted as `#.#.#`. The three numbers used should match the three numbers used for the
`<FIGURE_ID>` part. For example, a figure named `figure10_4_3` will have a figure number of `10.4.3`.

The `<description>` should be a brief description of the figure.

The following is a full example of what a figure may look like:

```
... code-block:: dscript
    :name: figure10_4_3
    :linenos:
    :emphasize-lines: 6

    task_script:
        type: task
        debug: false
        script:
        - narrate "oof!"
        - narrate "even stronger oof!"
        - narrate "weak oof"

.. rst-class:: figurecaption

**Figure 10.4.3** A task script with three narrates
```

Notes:

- The `:name:` option denotes the link used to reference to the figure.
- The `rst-class` directive implements a class to the next paragraph, and the CSS styling associated with that class
    will be applied. The `figurecaption` class will automatically center the caption text and make the caption text
    slightly larger.
- The description should be concise. It does not have to be a complete sentence. Do not end a figure caption with
    punctuation unless the punctuation is necessary.

### Image Figures

Generally speaking, the following is the ideal way to formulate an `image` figure:

```
.. image:: <ABS_FILEPATH>
    :name: <FIGURE_ID>
    :width: <WIDTH>
    :align: center
    :alt: <ALTERNATE>

.. rst-class:: figurecaption

**Figure <FIGURE_NUM>** <description>
```

The `<ABS_FILEPATH>` should be the absolute filepath leading to the image. Typically, since all images should be stored
in the `/source/_static/images/` folder, the image filepath should look like `/_static/images/IMAGE_FILE`. Please name
the image file something reasonable, and make sure that the image file name can easily be related to the figure. As a
suggestion, consider using `f#.#.#_DESCRIPTION` as the file name, where `#.#.#` is the figure number and `DESCRIPTION`
is a short description of the image's purpose.

The `<FIGURE_ID>` should **ALWAYS** be formatted as `figure#_#_#`. The first `#` represents the major section, the
second `#` represents the subsection, and the last `#` represents the ID of the figure. Technically speaking, each
figure should be named in increasing numerical order. For example, three figures in Section 10.4 will have their names
set to `figure10_4_1`, `figure10_4_2`, and `figure10_4_3`, in order.

The `<WIDTH>` should be adjusted so that on a sufficiently large screen, the image does not stretch to take up the
page. Most images should be able to use `90%` width with reasonable results.

The `:align:` option **must always be `center`**. Any other option is unacceptable without prior discussion on the
Discord server, preferably with suspic (@MusicScore) or mcmonkey.

The `<ALTERNATE>` should be a brief phrase that sufficiently describes what the image's purpose is, should it fail to
load for any particular user. The phrase does not require proper capitalization or punctuation.

The `<FIGURE_NUM>` should be formatted as `#.#.#`. The three numbers used should match the three numbers used for the
`<FIGURE_ID>` part. For example, a figure named `figure10_4_3` will have a figure number of `10.4.3`.

The `<description>` should be a brief description of the figure.

The following is a full example of what a figure may look like:

```
... image:: /_static/images/f10.4.1_bad_comedy.png
    :name: figure10_4_1
    :width: 90%
    :align: center
    :alt: a bad example of humor

.. rst-class:: figurecaption

**Figure 10.4.1** An attempt at humor with poor delivery
```

Notes:

- The `:name:` option denotes the link used to reference to the figure.
- The `rst-class` directive implements a class to the next paragraph, and the CSS styling associated with that class
    will be applied. The `figurecaption` class will automatically center the caption text and make the caption text
    slightly larger.
- The description should be concise. It does not have to be a complete sentence. Do not end a figure caption with
    punctuation unless the punctuation is necessary.

[To Top](#contribution-guidelines)

## 7) Links

There are four types of hyperlinking you should be most aware of.

### Inter-document Links

To link to another page, use the custom Sphinx role `:doc:`. The syntax is:

```:doc:`DISPLAY_TEXT <FILEPATH>` ```

The `DISPLAY_TEXT` should directly name the section by its numbers (for example, "Section 10.4"). You may add the
section name *after* the linked text, though this shouldn't be absolutely necessary.

Since the `FILEPATH` should always be absolute, it must always start at `/docs/`, unless you are referencing the first
page (`/index`).

For example:

```
:doc:`Section 10.4.3 </docs/proper-physical-expressions/the-art-of-slapping>`
```

### Reference Links

To link to a specific place in a document with a reference, use the custom Sphinx role `:ref:`. The syntax is:

```:ref:`DISPLAY_TEXT <REFERENCE>` ```

The `DISPLAY_TEXT` should some text that clearly refers to the referenced section/figure/paragraph. Most often, you can
simply use the title of the section (e.g. `Learning the Art of Slapping`), figure number (e.g. `Figure 10.4.3`), or a
short description of what the referenced paragraph is (e.g. `an explanation on how to slap`).

The `REFERENCE` should be the name of the reference.

For example:

```
.. my-reference:

A link back to :ref:`this same paragraph <my-reference>`
```

### rST Hyperlinks

For simpler hyperlinks, a reference link is not needed. Simply use the standard rST hyperlinking method. However,
overuse of named hyperlinks can create unnecessary complications.

### Anonymous hyperlinks

Anonymous hyperlinks are simply unnamed hyperlink references. They are most useful when a paragraph has exactly one
link that you will not need to reference again for the rest of the document.

[To Top](#contribution-guidelines)
