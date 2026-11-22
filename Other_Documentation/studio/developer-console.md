<!-- Source: https://create.roblox.com/docs/studio/developer-console -->

Developer Console | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/studio/developer-console.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Studio](/docs/en-us/studio)
4. /
5. [Developer Console](/docs/studio/developer-console)

# Developer Console

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/studio/developer-console.md)

The Developer Console  is a tool for debugging your game when testing in Studio or running it in production. It shows log messages and errors similar to the [Output](/docs/studio/output)  window and detailed information on [Memory](#memory) , [Network](#network) , and more.

You can open the console during a testing or live game session using any of the following ways:

-

Press F9 .

-

Type /console  into the chat.

-

Use the in-game menu:

1.

Open the in-game Roblox Menu .

 ![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Roblox-Menu-Button.png)

2.

Select the Settings  tab.

3.

Scroll down to Developer Console  and click Open .

## [Console sections](#console-sections)[](#console-sections)

The shortcut bar at the top of the console shows the number of critical errors and warnings, client memory usage, and average ping time; click any of these to jump to its corresponding section in the console. Below the shortcut bar is a series of tools as outlined below.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/console/Console-Summary-Bar.png)

### [Log](#log)[](#log)

The Log  tool shows diagnostic messages from scripts.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/console/Log-Sections.png)

Client/server toggle Output filters Command bar

Using the client-server switch, you can toggle between Client  and Server  views:

-

The Client  view shows output from client-side [LocalScripts](/docs/reference/engine/classes/LocalScript)  and/or [Scripts](/docs/reference/engine/classes/Script)  with [RunContext](/docs/reference/engine/classes/Script#RunContext)  set to [Enum.RunContext.Client](/docs/reference/engine/enums/RunContext#Client) . Anyone running a game can view local output messages.

-

The Server  view shows output from server-side [Scripts](/docs/reference/engine/classes/Script)  ([RunContext](/docs/reference/engine/classes/Script#RunContext)  set to [Enum.RunContext.Server](/docs/reference/engine/enums/RunContext#Server)  or [Enum.RunContext.Legacy](/docs/reference/engine/enums/RunContext#Legacy) ). Only the game owner or [group](/docs/projects/groups)  members with editing permission can view server output messages.

### [Memory](#memory)[](#memory)

Developer Console  provides two tools for monitoring memory usage, including:

-

Memory  — View real-time memory consumption by usage categories, including memory usage by both your custom components and the engine internal processes.

-

Luau heap  — Create snapshots on the heap memory, which refers to the memory allocation to your scripts. This tool provides various memory allocation views to help you identify current memory allocation and issues from different perspectives, such as object types and engine classes. It also allows you to create multiple snapshots to compare differences in memory usage over time.

For more information, see [Memory Usage](/docs/studio/optimization/memory-usage)

### [Network](#network)[](#network)

The Network  tool shows the number of web calls that the game has made. This includes explicit calls made through [HttpService](/docs/reference/engine/classes/HttpService)  and web requests made by Roblox services like [DataStoreService](/docs/reference/engine/classes/DataStoreService) . The Network  tool has two sections:

-

The Summary  section lists a summary of all the web calls by type. Each type has details on the number of requests, the number of failed requests, and the amount of time that the request took.

-

The Details  section lists each individual web call. Each row shows the HTTP method, such as GET  or POST , along with the status code, time to execute, request type, and request URL. Click on a web call to see its response details, for example:

{"Version":"1.1":"Content":{"Headers":[]},"StatusCode":"OK","ReasonPhrase":"OK","Headers":[],"TrailingHeaders":[],"RequestMessage":null,"IsSuccessStatusCode":true}

### [Script Profiler](#script-profiler)[](#script-profiler)

The Script Profiler  tool allows you to record profiling sessions of all running scripts and view their CPU time costs with custom recording and display settings. It's helpful for identifying scripts that take up the most CPU resources and slow down the performance. For more information, see [Script Profiler](/docs/studio/optimization/scriptprofiler) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
