<!-- Source: https://create.roblox.com/docs/en-us/studio/debugging -->

Debugging | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/studio/debugging.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Studio](/docs/en-us/studio)

# Debugging

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/studio/debugging.md)

Studio offers many debugging tools and workflows commonly found in Integrated Development Environments (IDEs). These help you inspect and resolve errors in scripts as they run.

## [Breakpoint debugging](#breakpoint-debugging)[](#breakpoint-debugging)

Breakpoints are checkpoints that pause or "break" the execution of your scripts at specific lines. You can use the pauses to inspect and debug your game, [watch](#watch)  variables, and inspect the [call stack](#call-stack) . Breakpoints are one of the most effective ways to debug functions, so they're one of the most important debugging tools.

### [Management](#management)[](#management)

In the [Script Editor](/docs/en-us/studio/script-editor) , you can [insert](#insert)  several types of breakpoints and edit the configuration of a breakpoint at any time, including during playtest sessions. If you edit breakpoints during a playtest session, the edits persist even after you finish it. You can also edit a breakpoint that's actively pausing your playtest session, but changes don't apply until the next playtest session.

#### [Insert](#insert)[](#insert)

Breakpoints take multiple variations and can be inserted at any line of executable code as follows:

Standard Conditional Logpoint Temporary

To insert a standard breakpoint at a line of code, click in the gutter directly to the right of its line number. Alternatively, right‑click in the gutter and select Insert Breakpoint . The breakpoint icon appears as a red circle.

![Standard breakpoint shown in the script gutter](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Gutter-Breakpoint.png)

#### [Disable](#disable)[](#disable)

To temporarily disable a breakpoint without [deleting](#delete)  it, use any of the following workflows:

-

Click the breakpoint's icon.

-

Right-click the breakpoint's icon and select Disable Breakpoint .

-

[Edit](#edit)  the breakpoint and toggle its Enabled  checkbox.

A disabled breakpoint appears as a hollow version of its enabled icon, for example a hollow circle for a disabled standard breakpoint, or a hollow diamond for a disabled logpoint.

![Disabled standard breakpoint shown in the script gutter](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Gutter-Breakpoint-Disabled.png) Disabled standard breakpoint

![Disabled logpoint shown in the script gutter](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Gutter-Breakpoint-Logpoint-Disabled.png) Disabled logpoint

#### [Delete](#delete)[](#delete)

To delete a breakpoint, middle-click its icon or right‑click its icon and select Delete Breakpoint .

Deleting a breakpoint deletes its Condition  and Log Message . If you want to keep this information for future debugging, [disable](#disable)  the breakpoint instead.

#### [Edit](#edit)[](#edit)

You can edit the configuration of a breakpoint at any time, including during playtest sessions. If you edit breakpoints during a playtest session, the edits persist even after you finish it. You can also edit a breakpoint that's actively pausing your playtest session, but changes don't apply until the next playtest session.

To edit a breakpoint:

1.

Right-click the breakpoint icon and select Edit Breakpoint .

2.

In the Edit Breakpoint  window, configure the breakpoint as desired. You can mix these configurations together to best suit your debugging needs.

| Option | | Description |
| --- | --- |
| Condition | | An optional expression that determines whether the breakpoint activates. If the condition is empty, the breakpoint always activates. If the condition exists, the breakpoint becomes a [conditional breakpoint](#insert)  and activates only if the condition is true. For example, if you want the breakpoint to activate only if the variable var  equals 10 , set the condition to var == 10 . |
| Log Message | | An expression that prints to the [Output](/docs/en-us/studio/output)  window when the breakpoint is hit. The format of the log message is the same as that of a [print()](/docs/en-us/reference/engine/globals/LuaGlobals#print)  statement. For example, set the log message as "The value of var:", var  to output the same message as print("The value of var:", var) . |
| Continue Execution | | Determines whether the breakpoint pauses the script if it activates. This option is disabled by default unless the inserted breakpoint is a [logpoint](#insert) . |
| Remove Breakpoint on Hit | | If checked, the breakpoint automatically removes itself after the first playtest session, effectively making it a [temporary](#insert)  breakpoint. |
| Trigger At | | The context  of a breakpoint determines whether it should activate on the Client  (client‑side scripts), Server  (server‑side scripts), or Edit  (debugging [plugin](/docs/en-us/studio/plugins)  scripts). If you choose Custom Context , the window indicates the current trigger contexts. |

### [Workflow](#workflow)[](#workflow)

The typical workflow for breakpoint debugging is as follows:

1.

Open the script you'd like to debug and [insert breakpoints](#insert)  on the lines of codes that you want to examine.

2.

From Studio's mezzanine, [initiate a playtest](/docs/en-us/studio/testing-modes#playtesting)  to begin debugging.

 ![Test option in the testing modes dropdown of Studio's mezzanine.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Mode-Test.png)

3.

When the script hits a breakpoint, the playtest session pauses  unless that breakpoint is [configured](#edit)  to continue execution. A yellow arrow over the breakpoint indicates which line of code executes next.

 ![Active breakpoint in the debugger showing yellow arrow](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Gutter-Breakpoint-Active.png)

4.

As the script pauses, inspect the [Breakpoints](#breakpoints)  window, [Watch](#watch)  window, [Call Stack](#call-stack)  window, [Output](/docs/en-us/studio/output)  window, and [Script Editor](#script-editor)  to find information about variable values and function executions.

5.

To continue executing code after hitting a breakpoint, click Resume Scripts  in the mezzanine.

 ![Resume Scripts button indicated in Studio's mezzanine](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Debug-Resume-Scripts.png)

You can also execute code one line at a time with the stepping buttons in the mezzanine:

 ![Breakpoint stepping buttons indicated in Studio's mezzanine](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Debug-Tools.png)

| Action | | Shortcut | | Description |
| Step Into | | F11 | | The Step Into  button moves the debugger into the code of the function on the current line. If there is no function on the current line, the debugger moves to the next line. |
| Step Over | | F10 | | The Step Over  button moves the debugger to the next line of code, not  moving into functions. |
| Step Out | | Shift F11 | | The Step Out  button moves the debugger out of the current function and to the next line of code after the function call. If the current line isn't inside a function, the debugger moves to the next line. |

6.

When you're finished debugging the current session, click the Stop  button.

 ![Stop button indicated in Studio's mezzanine.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Debug-Stop.png)

### [Monitoring](#monitoring)[](#monitoring)

Studio includes multiple windows and tools to monitor variable values and function executions while debugging. With this information, you can find the root cause of most problems in your scripts.

 ![Breakpoints button indicated in Studio's toolbar](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Debugging-Tools.png)

#### [Breakpoints](#breakpoints)[](#breakpoints)

The Breakpoints  window is a unified view that shows all breakpoints within all scripts. To open it, click Breakpoints  from Studio's Script  tab toolbar, or navigate to the Window  ⟩ Debug  menu and toggle on Breakpoints .

In the window, the Script  and Line  columns always display, and you can toggle on/off other [configuration](#edit)  columns through the ⋮  menu in the upper‑right corner. Within the Script  column, right‑click any breakpoint to reveal an options menu to [edit](#edit) , [disable/enable](#disable) , [delete](#delete) , or jump to the breakpoint's line within the script.

 ![Breakpoints window in Studio](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Breakpoints-Window.png)

While in a debugging session, the furthest left column shows (x3)  which indicates the multiple contexts (Client , Server , Edit ) for the breakpoint. By expanding any breakpoint's branch, you can then click the icon next to a specific context to [disable/enable](#disable)  it for that context, such as disabling a breakpoint only in the Client  context while keeping it enabled in the Server  context.

 ![Breakpoint expanded to show contexts](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Breakpoints-Window-Contexts.png)

#### [Call Stack](#call-stack)[](#call-stack)

The Call Stack  window, accessible from Studio's Script  tab toolbar or the Window  ⟩ Debug  menu, shows which line of code is going to execute next when the debugger reaches a breakpoint. If you call functions from inside other functions, it indicates which lines those functions were called from, letting you confirm whether the actual call flow matches the expected flow.

 ![Call stack flow in a script](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Call-Stack-Flow-Script.png)  ![Call stack flow in the Call Stack window](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Call-Stack-Flow-Window.png)

As the script pauses at breakpoints, use the stepping buttons in the mezzanine to step into, over, or out of a function/line as outlined in [workflow](#workflow) .

 ![Breakpoint stepping buttons indicated in Studio's mezzanine](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Debug-Tools.png)

#### [Watch](#watch)[](#watch)

The Watch  window, accessible from Studio's Script  tab toolbar or the Window  ⟩ Debug  menu, lets you actively watch variable and expression values as you step through breakpoints.

Variables My Watches

The Variables  tab shows information about the current variables in [scope](/docs/en-us/luau/scope) , filterable by clicking the All Scopes  button in the window's upper bar. Expanding a branch shows the members of that variable or instance and their values. You can also watch any variable by double‑click highlighting it in the [Script Editor](/docs/en-us/studio/script-editor) , right‑clicking, and selecting Add Watch  from the popup menu.

![Variables to watch inside a script](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Watch-Variables-Script.png)![Variables information in the Watch window](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Watch-Variables-Window.png)

#### [Script Editor](#script-editor)[](#script-editor)

The debugger is integrated with the [Script Editor](/docs/en-us/studio/script-editor) . When your game pauses at a breakpoint in a script, you can hover your mouse over the name of a variable to see its value. For example, you can see the composition of a table and its contained keys/values.

 ![Mouseover a variable in Script Editor to show value](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Script-Editor-Mouseover-Table.png)

## [Additional debugging tools](#additional-debugging-tools)[](#additional-debugging-tools)

In addition to the debugger, Studio offers additional debugging tools for you to fix problems and bugs in your game.

### [Command Bar](#command-bar)[](#command-bar)

The [Command Bar](/docs/en-us/studio/overview#command-bar)  allows you to run Luau commands while the game is running. It is available in Studio from the Window  ⟩ Script  menu and in the [Developer Console](/docs/en-us/studio/developer-console) .

### [Developer Console](#developer-console)[](#developer-console)

The [Developer Console](/docs/en-us/studio/developer-console)  provides a wide array of details including client and server output, memory usage, network performance, and more. To open console while testing or playing a game, type /console  into the chat or press F9 .

### [Log files](#log-files)[](#log-files)

When a script prints or errors in Studio or the player app, the app records the message in a log file in the local file system. These files are located in different places depending on the operating system.

#### [Windows](#windows)[](#windows)

To access log files on Windows:

1.

Open File Explorer .

2.

Navigate to the %LOCALAPPDATA%\Roblox\logs  directory.

3.

Double-click a log to open it. Logs with the same XXXXX  value are from the same Studio session.

#### [Mac](#mac)[](#mac)

To access log files on Mac:

1.

Open Finder .

2.

In the menu bar, select Go  ⟩ Go to Folder... .

3.

In the dialog, enter ~/Library/Logs/Roblox .

4.

Double-click the result to navigate to the Roblox logs directory.

5.

Inside the directory, double-click a log to open it.

#### [iOS](#ios)[](#ios)

You can collect iOS logs using a Mac or using an iOS device.

Mac Device

To access iOS log files on a Mac:

1.

Connect the iOS device to a Mac.

2.

Open Finder .

3.

Navigate to Utilities  and open the Console  application.

4.

To populate real-time logs in the Console application, select the iOS device from the sidebar, click the Start  button, and reproduce the issue on the iOS device.

5.

To populate archived logs in the Console application, run sudo log collect --device-name "[iOS Device Name]"  in the Terminal . Make sure there are no apostrophes in the device's name or you might get an error when running the command.

#### [Android](#android)[](#android)

To access log files on Android:

1.

Navigate to Settings  ⟩ System  ⟩ Developer options .

2.

Toggle Developer options  on.

3.

On a computer, download and install [Android Studio](https://developer.android.com/studio) .

4.

In Android Studio, click Logcat .

5.

Connect the Android device to the computer to automatically populate Logcat  with logs.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
