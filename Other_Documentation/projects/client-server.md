<!-- Source: https://create.roblox.com/docs/projects/client-server -->

Client-server runtime | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/projects/client-server.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Projects](/docs/projects)
6. /
7. [Architecture](/docs/projects/data-model)

# Client-server runtime

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/projects/client-server.md)

## [Server](#server)[](#server)

Roblox games are multiplayer by default and run in a client-server model. The Roblox server  is the ultimate authority for maintaining the game's state, and is responsible for keeping all connected clients in sync with the server.

![A server grouping with connections to three client devices.](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Client-Server-Model.png) Server with connections to three client devices

## [Client](#client)[](#client)

When a game runs, Roblox copies a version of the "edit" data model that you built and published from Studio and runs it on Roblox servers as the "runtime" data model.

Connected clients also receive a copy of the runtime data model and any initialization of the player occurs, such as initializing a player's backpack (inventory) or local user interface. When a game has [Workspace.StreamingEnabled](/docs/reference/engine/classes/Workspace#StreamingEnabled)  set to true, the server initially only sends a subset of content under [Workspace](/docs/reference/engine/classes/Workspace)  that is closest to the client. The client then renders the 3D world and begins running any applicable scripts.

![A diagram that maps objects between 'edit' and 'runtime' data models.](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Data-Model-Mapping.png)

## [Replication](#replication)[](#replication)

The server constantly updates connected clients, keeping everything in sync across the server and clients through a process called replication , which synchronizes the data model, physics simulation, and chat messages. Replication logic exists on both the client and server to ensure synchronization.

Data Physics Chat

Data model changes can occur in a variety of cases, such as when something in the 3D world is created or a property of the 3D world changes. This typically occurs when a script on the server or client makes a change that needs to be reflected on the other side of the client-server boundary. The following diagrams show common scenarios for data replication.

Client → Server

![A diagram of one client communicating with the server.](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Remote-Flow-Client-Server.png) Communication from any client to the server. For example, a client presses the P  key to drink an invisibility potion, and tells the server to make that player's character invisible to all other players.

Server → Client

![A diagram of the server communicating with one client.](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Remote-Flow-Server-Client.png) Communication from the server to one specific client. For example, a player joins the game and the server populates that player's inventory with a set of items.

Server → All Clients

![A diagram of the server communicating with all connected clients.](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Remote-Flow-Server-All-Clients.png) Communication between the server and all connected clients. For example, displaying a countdown timer to all participants in a race.

Most players on Roblox game between 100–300 milliseconds of network latency. Roblox Studio playtesting runs with a default of no latency, but you can change Network Simulation  settings in the Network  section of [Studio Settings](/docs/studio/setup#customization)  (Alt S  on Windows; ⌥ S  on Mac). Use a minimum delay of 50–150 milliseconds in both the inbound and outbound directions to better simulate how network latency will affect your game.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
