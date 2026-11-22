<!-- Source: https://create.roblox.com/docs/studio/output -->

Output | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/studio/output.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Studio](/docs/en-us/studio)

# Output

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/studio/output.md)

The Output  window, accessible from Studio's Window  menu or Script  tab toolbar, displays errors captured from running scripts, messages from Roblox Engine, messages from calls to print() , and errors from calls to warn() .

Plugins can interact with the Output  window through [LogService](/docs/reference/engine/classes/LogService)  which can record and clear the window's contents. You can customize the output through the following elements:

 ![Sections of Output window indicated by lettered pointers](https://prod.docsiteassets.roblox.com/assets/studio/general/Output-Window-Diagram.png)

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-A.png)

Filters output by type, such as Error  or Warning .

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-B.png)

Filters output by context, such as Client , Server , or User Plugin . During a [Team Test](/docs/studio/testing-modes#collaborator-logs) , this dropdown also includes a Remote Client  option and a Sources  section for showing collaborators' client output.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-C.png)

Filters output by the text entered into the field, such as an object name.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-D.png)

Clears all output messages from the window. This action has a shortcut of Ctrl K  on Windows or ⌘ K  on Mac.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-E.png)

Controls the level of detail displayed for each output message.
-

Show Timestamp  — Shows a detailed timestamp in HH:MM:SS.SSS  format.

-

Show Context  — Shows the message context, such as Client  or Server .

-

Show Source  — If applicable, shows the associated script name and line number.

-

Show Tables Expanded by Default  — For outputted tables, contents are expanded by default.

-

Show Memory Address for Expandable Tables  — For expandable tables, shows the internal memory address, such as 0xb4f0417581144ec5 .

-

Log Mode  — Simplifies output by removing options, such as expandable trees.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
