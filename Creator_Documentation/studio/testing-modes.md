<!-- Source: https://create.roblox.com/docs/en-us/studio/testing-modes -->

Studio testing modes | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/studio/testing-modes.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Studio](/docs/en-us/studio)

# Studio testing modes

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/studio/testing-modes.md)

Because of the underlying [client-server model](/docs/en-us/projects/client-server)  of the Roblox Engine, it's important that you test your game in various modes before [releasing it to the public](/docs/en-us/production/publishing/publish-games-and-places#release-games) . All of the testing options are accessible in the left portion of the mezzanine.

 ![Testing controls indicated in Studio's mezzanine.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Controls.png)

## [Playtesting](#playtesting)[](#playtesting)

There are three common options for playtesting a game. Choose the desired option from the dropdown menu and click the Play  button to its right to begin the playtest.

 ![Test option in the testing modes dropdown of Studio's mezzanine.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Mode-Test.png)

| Mode | | Shortcut | | Description |
| --- | --- |
| Test | | F5 | | Starts simulating the game, inserting your avatar at either a [SpawnLocation](/docs/en-us/reference/engine/classes/SpawnLocation)  or coordinates of around (0, 100, 0) . |
| Test Here | |  | | Starts simulating the game, inserting your avatar in front of the camera's current position. |
| Run | | F8 | | Starts simulating the game but does not insert your avatar. The simulation begins at the current camera position and you can navigate around using the Studio camera controls. |

Once a playtest is running, additional options become available in the mezzanine.

 ![Additional options available during a playtest from Studio's mezzanine.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Options.png)

| Action | | Shortcut | | Description |
| Pause  / Resume | |  | | Lets you [pause/resume physics and animations](#pauseresume) . |
| Stop | | Shift F5 | | Stops simulation of the game and resets all objects and instances to how they were before the playtest. |
| Client  / Server | |  | | During playtesting in a "solo" mode (Test  or Test Here ), toggles between Client  mode and Server  mode. See [toggle client/server](/docs/en-us/studio/testing-modes#toggle-clientserver)  for details. |

### [Toggle client/server](#toggle-clientserver)[](#toggle-clientserver)

When testing in either Test  or Test Here  mode, Studio runs two separate simulations — one [client](/docs/en-us/projects/client-server#client)  simulation and one [server](/docs/en-us/projects/client-server#server)  simulation — which can provide a more accurate impression of how the game will execute in production.

While solo playtesting, you can toggle between Client  and Server  modes by clicking the Client/Server  toggle button. When you toggle, the button changes to reflect the current simulation mode.

![](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Client.png) Client

![](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Server.png) Server

Depending on the simulation mode, control of your character and the camera changes as follows:

Client Mode Server Mode

![](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Client-Server-Toggle-3D-Client.jpg) In Client  mode, the 3D viewport is surrounded by a blue  border and the simulation uses your character controls and camera setup. This testing mode is a close simulation of the game running on the Roblox application, without multiple players.

Within the [Explorer](/docs/en-us/studio/explorer)  window hierarchy, certain objects only exist in their expected containers.

![Explorer window showing items that exist on client only](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Client-Server-Toggle-Explorer-Client.png) In Client  mode, the expected client-side objects are present in the hierarchy, including those copied over from [StarterPack](/docs/en-us/reference/engine/classes/StarterPack)  to the player's [Backpack](/docs/en-us/reference/engine/classes/Backpack)  and from [StarterPlayer](/docs/en-us/reference/engine/classes/StarterPlayer)  into the player's [PlayerScripts](/docs/en-us/reference/engine/classes/PlayerScripts) .

![Explorer window showing items that exist on server only](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Client-Server-Toggle-Explorer-Server.png) In Server  mode, the expected server-side objects are present in the hierarchy, including scripts in [ServerScriptService](/docs/en-us/reference/engine/classes/ServerScriptService)  and objects you placed in [ServerStorage](/docs/en-us/reference/engine/classes/ServerStorage) .

In the [Output](/docs/en-us/studio/output)  window, messages are labeled blue  (client) or green  (server), indicating their origin from either the client or server. For messages output from [ModuleScripts](/docs/en-us/reference/engine/classes/ModuleScript) , the label color is determined by whether the module was called from a client-side [LocalScript](/docs/en-us/reference/engine/classes/LocalScript)  or from a server-side [Script](/docs/en-us/reference/engine/classes/Script) .

 ![Output window showing green label for server output and blue label for client output](https://prod.docsiteassets.roblox.com/assets/studio/general/Output-Window-Client-Server-Labels.png)

### [Pause/resume](#pauseresume)[](#pauseresume)

While solo playtesting, the Pause/Resume  button is useful for debugging ephemeral scenes and mechanisms, without disabling rendering.

 ![Pause/Resume button indicated in Studio's mezzanine.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Pause.png)

By default, pausing and resuming acts upon both the client and  server. If you wish to pause or resume only the client or  server:

1.

Set the [client/server toggle](#toggle-clientserver)  based on which simulation you want to pause/resume.

2.

Click the small arrow on the Pause/Resume  button and select the alternate option of Pause/Resume Client  or Pause/Resume Server . Clicking the button will then pause or resume only that side of the simulation.

When the simulation is paused, you can step forward  1/60th of a second (60 Hz) by clicking the Step Forward  button. Like the Pause/Resume  button to its left, clicking the small arrow lets you select stepping for only the client or  server based on the [client/server toggle](#toggle-clientserver) .

 ![Step Forward button indicated in Studio's mezzanine.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Step-Forward.png)

Note the following technical details in relation to pause/resume:

-

Although [Animations](/docs/en-us/reference/engine/classes/Animation)  are not based on physics, these toolbar buttons also pause/resume animations.

-

Pausing or resuming has no effect on running scripts.

-

Only the [RunService](/docs/en-us/reference/engine/classes/RunService)  callbacks [PreAnimation](/docs/en-us/reference/engine/classes/RunService#PreAnimation) , [PreSimulation](/docs/en-us/reference/engine/classes/RunService#PreSimulation) , [PostSimulation](/docs/en-us/reference/engine/classes/RunService#PostSimulation) , and [Stepped](/docs/en-us/reference/engine/classes/RunService#Stepped)  pause or resume through these toolbar buttons. Other callbacks ([PreRender](/docs/en-us/reference/engine/classes/RunService#PreRender) , [Heartbeat](/docs/en-us/reference/engine/classes/RunService#Heartbeat) , and [RenderStepped](/docs/en-us/reference/engine/classes/RunService#RenderStepped) ) continue to fire, maintaining normal functionality of camera scripts, rendered visualizations, and plugins.

## [Multi-client simulation](#multi-client-simulation)[](#multi-client-simulation)

The Server & Clients  option from the dropdown menu lets you launch multiple sessions of Studio, one acting as the server and each other acting as a client. This testing mode is a valuable tool for comparing how a client "sees" other clients within the game.

1.

With the Server & Clients  option selected in the dropdown menu, choose the number of client sessions to test. Usually 1–2 clients is sufficient, although you can simulate up to eight.

 ![Server & Clients option in the testing modes dropdown of Studio's mezzanine.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Mode-Server-Clients.png)

2.

Press the Play  button or F7  to begin the client-server simulation.

3.

When you're finished testing, press the End Session  button from any of the simulation sessions to close all simulated clients and the simulated server.

 ![End Session indicated in Studio's mezzanine](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-End-Session.png)

## [Party simulation](#party-simulation)[](#party-simulation)

The Party Simulator  allows you to test and debug games that use party-related APIs directly within Studio, without needing to publish and coordinate multiple devices. This tool lets you configure and emulate parties for test players in your [Server & Clients](#multi-client-simulation)  play tests.

When play testing, Party Simulator automatically assigns all test players to the configured simulated parties.

 ![Party Emulator displaying simulated parties and various assignment options](https://prod.docsiteassets.roblox.com/assets/studio/general/Party-Simulator.png)

If Party Simulator is enabled:

-

Each [Player.PartyId](/docs/en-us/reference/engine/classes/Player#PartyId)  property reflects the Party Simulator assignments.

-

[SocialService:GetPartyAsync()](/docs/en-us/reference/engine/classes/SocialService#GetPartyAsync)  returns a simulated table of party data.

-

[SocialService:GetPlayersByPartyId()](/docs/en-us/reference/engine/classes/SocialService#GetPlayersByPartyId)  returns a list of [Player](/docs/en-us/reference/engine/classes/Player)  instances assigned to the provided [Player.PartyId](/docs/en-us/reference/engine/classes/Player#PartyId) .

You can adjust the number of local test players at any time using Studio's [Server & Clients](#multi-client-simulation)  setting. When the test player count changes, the emulator automatically updates to include or remove players in the configuration.

## [Collaborative testing](#collaborative-testing)[](#collaborative-testing)

If you're working on a game with others in [collaboration](/docs/en-us/projects/collaboration)  mode, you can test with other collaborators as follows:

1.

Select Team Test  in the dropdown menu and press the Play  button to open a new Studio session with your character inserted.

 ![Team Test option in the testing modes dropdown of Studio's mezzanine.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Mode-Team-Test.png)

2.

Other collaborators can then join by pressing the Play  button from the mezzanine in their Studio session.

Only one team test session can run at any given time. To close a session and kick out all testers, click the End Session  button.

### [Collaborator logs](#collaborator-logs)[](#collaborator-logs)

During a Team Test, each collaborator's client output is shared with the session so that your team can debug together. Only client output is shared, and only while a collaborator is in the Team Test; leaving the Team Test stops sharing.

1.

Click the context filter dropdown at the top of the Output  window. A Sources  section lists everyone in the session.

2.

Check a name to show that collaborator's output, or check All  to show everyone, including people who join later. Their messages appear prefixed with their name, such as [builderman] Loaded 12 enemies .

Note the following behaviors:

-

Nobody is shown when a Team Test starts. Your own output is never affected by who you select in Sources ; it keeps following your usual context and message-type filters.

-

The Remote Client  option in the context filter shows or hides everyone else's output at once, separately from your own Client  output.

-

Message-type filters (Output , Info , Warning , Error ) and the text filter apply to collaborators' messages as well.

-

When the Team Test ends, Studio restores the output you had before the session started.

-

The Sources  section only shows collaborators' client output, not the Team Test server's output.

Scripts, plugins, and command bar code can also read a collaborator's recent log history with [LogService:GetLogHistoryAsync()](/docs/en-us/reference/engine/classes/LogService#GetLogHistoryAsync) , passing the collaborator's [Player.User](/docs/en-us/reference/engine/classes/Player#User) . To read the Team Test server's log history, pass User.fromId(0) . This method only works during a Team Test (it's disabled in solo playtesting and live games), returns up to the 512 most recent messages in the same format as [LogService:GetLogHistory()](/docs/en-us/reference/engine/classes/LogService#GetLogHistory) , and yields. It fetches logs over the network and can error, so wrap calls in pcall .

```

local LogService = game:GetService("LogService")

local Players = game:GetService("Players")

for _, player in Players:GetPlayers() do

	local ok, history = pcall(LogService.GetLogHistoryAsync, LogService, player.User)

	if not ok then

		warn(`Couldn't read {player.Name}'s logs: {history}`)

		continue

	end

	for _, entry in history do

		if entry.messageType == Enum.MessageType.MessageError then

			print(`[{player.Name}] {entry.message}`)

		end

	end

end

-- The Team Test server's log history

local ok, serverHistory = pcall(LogService.GetLogHistoryAsync, LogService, User.fromId(0))

if ok then

	print(`The server has {#serverHistory} log entries`)

end

```

## [Device simulation](#device-simulation)[](#device-simulation)

Use [Device Simulator](/docs/en-us/studio/device-simulator)  to preview how your experience looks and behaves on a device you don't have in front of you, including its screen dimensions, pixel density, on-screen keyboard, and touch input. Device Simulator pairs with [Controller Emulator](/docs/en-us/studio/controller-emulator)  to emulate the gamepads, VR controllers, handhelds, and TV remotes players use to control your experience.

## [Network simulation](#network-simulation)[](#network-simulation)

Use [Network Simulator](/docs/en-us/studio/network-simulator)  to add latency, jitter, and packet loss to Studio [playtest](#playtesting)  connections and reproduce the network conditions players encounter on wired, Wi-Fi, and mobile connections. This is especially useful for testing games that use [Server Authority](/docs/en-us/projects/server-authority) , since prediction and rollback/resimulation mechanisms are sensitive to networking conditions, and for testing [UnreliableRemoteEvents](/docs/en-us/reference/engine/classes/UnreliableRemoteEvent) , which might be lost or arrive out of order.

## [Scripted testing](#scripted-testing)[](#scripted-testing)

In addition to the interactive testing tools above, Studio exposes services that let you drive testing programmatically from a plugin or build pipeline. All three services are Studio-only and do nothing when run in a published experience.

| Service | | Purpose |
| [StudioDeviceSimulatorService](/docs/en-us/reference/engine/classes/StudioDeviceSimulatorService) | | Scriptable [device simulation](/docs/en-us/studio/device-simulator) . Browse device presets, switch the active device, override resolution and DPI, control orientation and scaling, and create custom device profiles that persist to disk. |
| [StudioTestService](/docs/en-us/reference/engine/classes/StudioTestService) | | Programmatic [multi-client simulation](#multi-client-simulation) . Start a server with up to 8 simulated clients, add players mid-session, pass arguments into the test, trigger client disconnects, and end tests from the server. |
| [VirtualInput](/docs/en-us/reference/engine/classes/VirtualInput) | | Simulated mouse, keyboard, and pointer events that are processed exactly like real hardware input. Obtain an instance from [UserInputService:CreateVirtualInput()](/docs/en-us/reference/engine/classes/UserInputService#CreateVirtualInput) . |

These services enable include cross-device multiplayer testing (cycle through device profiles and launch a multiplayer test at each), player join/leave stress testing, orientation regression testing, and end-to-end UI flow automation.

## [VR headsets](#vr-headsets)[](#vr-headsets)

If you'd like to support virtual reality (VR) headsets for your game, make sure to test or [emulate](#vr-emulation)  VR in Studio.

### [VR emulation](#vr-emulation)[](#vr-emulation)

VR emulation  lets you test VR games in Studio without a physical headset. Just like emulating any other device, use [Device Simulator](/docs/en-us/studio/device-simulator)  to choose a Headset  device such as Meta Quest 2  or Meta Quest 3 . [Controller Emulator](/docs/en-us/studio/controller-emulator)  automatically selects the appropriate controller for the headset.

![The Controller Emulator with a Quest 3 controller.](https://prod.docsiteassets.roblox.com/assets/studio/general/Controller-Emulator-VR.png)

![Emulator with a Quest 3 emulation.](https://prod.docsiteassets.roblox.com/assets/studio/general/Emulator-Viewport-VR.jpg)

The combination of a headset and multiple controllers, each with motion tracking, make VR emulation more complex:

-

For motion tracking emulation, press Alt 1  (⌥ 1 ) to lock the mouse to and unlock the mouse from the viewport.

-

Use Shift ←  or Shift →  to switch between common combinations of the headset, left controller, and right controller. For example, you might use the Headset  option to look around as you walk forward with the left controller button, but then switch to the Right Controller  when you need to use motion controls to aim at a target.

### [Headset configuration](#headset-configuration)[](#headset-configuration)

Studio supports testing for all VR headsets that are compatible with [OpenXR](https://www.khronos.org/openxr/) , the open‑source industry standard providing access to VR.

Currently, testing in VR is only supported on Windows.

To enable Studio testing in VR, you must connect your headset to your PC and configure the OpenXR runtime before  launching Studio. If you've already launched Studio, quit and complete the configuration steps first.

If you only have one VR headset, installing the corresponding VR app automatically configures the runtime for you. If you have multiple headsets, you must set up the runtime manually and make sure to only  configure the one that you want to use for testing.

The following steps are for the two most common VR apps:

-

SteamVR for headsets such as the HTC Vive and Valve Index.

-

Oculus for headsets such as the Meta Quest and Oculus Rift.

Steam VR Oculus VR

1.

Install and open the SteamVR app on your computer.

2.

Under SteamVR Settings , select the Developer  tab. Then select Show Advanced Settings .

3.

Set SteamVR as OpenXR runtime.

4.

Turn the controllers on by pressing the System  button until you hear a beeping sound.

-

To turn the controller off, press and hold the System  button until you hear the same beeping sound.

If you follow the steps correctly, the status icons on the SteamVR app and the status lights on the hardware should all be green, indicating that the configuration is completed.

When you quit the SteamVR app, the controllers automatically turn off. The controllers also automatically turn off after being idle for a period of time.

### [Roblox Quest app](#roblox-quest-app)[](#roblox-quest-app)

You can test your game in the Roblox app on Quest without linking your headset to your computer. Use the following steps to access your game on your headset in this mode:

1.

In Studio, [publish your game](/docs/en-us/production/publishing/publish-games-and-places#publish-games) .

2.

Using your [Creator Dashboard](https://create.roblox.com/dashboard/creations)  or the link in Studio, open the game page in your web browser.

3.

On the game page, add the game to your favorites by clicking the Favorite  icon.

4.

Using your headset, open the standalone Roblox app.

5.

Scroll down to the Favorites  section in the home page and run your game.

### [Studio VR mode](#studio-vr-mode)[](#studio-vr-mode)

After [configuring your headset](#headset-configuration) , you can turn on the Studio VR testing mode through the following steps:

1.

In the File  menu, select Studio Settings .

2.

Select Rendering .

3.

Under General  settings, turn on Enable VR Mode .

You can now test your game using your VR headset using any of the available [playtest options](#playtesting) . During a VR testing session, if your headset cable disconnects or you close the Roblox Studio Beta app on the headset, you'll need to restart Studio to re-run testing.

## [Player emulation](#player-emulation)[](#player-emulation)

For detailed emulation of game [localization](/docs/en-us/production/localization)  and content policies, you can test through the Player Emulator , accessible from Studio's Test  menu.

With the emulator window open, toggle on Enable Test Profile . Emulation will remain as toggled (enabled or disabled) even if you close the window.

Lower down in the window, commonly used options include:

| Option | | Description |
| Locale | | Lets you emulate a [localized](/docs/en-us/production/localization)  language while playtesting. |
| Pseudolocalize | | Swaps out characters with similar but slightly different characters so that it's easy to identify which strings are going through the [translation](/docs/en-us/production/localization)  system. Enabling this helps you identify unlocalized  text without having to change the emulation language. For example:
-

Bloxy Cola  ⟩ ßℓôж¥ Çôℓá

-

Dominus Empyreus  ⟩ Ðô₥ïñúƨ É₥ƥ¥řèúƨ

 |
| Elongate | | Elongates text strings by a factor defined via the slider. For example:
-

Bloxy Cola  ⟩ Bloooxyy Coolaa  (50% longer)

-

Dominus Empyreus  ⟩ Doomiinuus Eempyyreus  (30% longer)

Using elongation helps you identify places where your user interfaces might not be able to handle text that's longer than the default translated text. Note that Spanish is on average 30% longer than English and the equivalent for German is even longer. Also note that this only affects text that goes through the [translation](/docs/en-us/production/localization)  system. |
| Region | | Lets you emulate a player's country/region while playtesting; this selection may impact other toggles and checkboxes in the window as outlined in [GetPolicyInfoForPlayerAsync()](/docs/en-us/reference/engine/classes/PolicyService#GetPolicyInfoForPlayerAsync) . |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
