<!-- Source: https://create.roblox.com/docs/nl-nl/samples -->

Code samples | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Voorbeelden en projecten](/docs/nl-nl/samples)

# Code samples

* Deze inhoud is binnenkort beschikbaar in je geselecteerde taal.

Nederlands

The following samples show you how to carry out common scripting tasks in Roblox. Where applicable, corresponding 3D objects or models are provided. You can import the samples directly into your inventory where you can view them in the Studio Toolbox  or open them directly in Studio.

[

#### Action Manager

Provides a wrapper for ContextActionService that displays actions on-screen. Input prompts automatically change based on the latest input type, rather than being set once based on peripherals.

](https://create.roblox.com/marketplace/asset/13549359972)

Toevoegen aan inventaris

[

#### Admin Commands

Demonstrates an admin command system using TextChatCommands. Command functions are stored in the Commands module and have an included permission level. Permission levels are determined from group rankings or a manual override set in the Admins module.

](https://create.roblox.com/marketplace/asset/13549366436)

Toevoegen aan inventaris

[

#### Beam Between

Given two attachments and a beam prefab, this class continuously orients duplicates of the attachments to face each other so that the beam remains straight. Also provides an API to enable/disable the beam and its orientation updates.

](https://create.roblox.com/marketplace/asset/13549374667)

Toevoegen aan inventaris

[

#### Change Part Color On Touch

Demonstrates changing the color of a part upon being touched by a player's character. The color change is debounced to ensure the Touched event does not trigger a color change too quickly. The part's color is randomly set using math.random.

](https://create.roblox.com/marketplace/asset/13549383422)

Toevoegen aan inventaris

[

#### Character Loaded Wrapper

Provides an API to use when referencing a Player's character to make sure it is "Fully loaded", which is defined as: 1) Character is a descendant of workspace 2) Character has a PrimaryPart set 3) Character contains a child which is a Humanoid 4) The Humanoid's RootPart property is not nil

](https://create.roblox.com/marketplace/asset/13549390287)

Toevoegen aan inventaris

[

#### Character Path Beam

Creates a guiding beam from the bottom of the local character to a destination attachment. Useful for guiding players towards objectives in order to progress.

](https://create.roblox.com/marketplace/asset/13549414385)

Toevoegen aan inventaris

[

#### Cloud Config

Demonstrates a cloud configuration system where flag values can be set in DataStore and are automatically polled for updates by live servers.

](https://create.roblox.com/marketplace/asset/13549421787)

Toevoegen aan inventaris

[

#### Code Reservation Service

Demonstrates a system to reserve and hand out single-use codes.

](https://create.roblox.com/marketplace/asset/14818045262)

Toevoegen aan inventaris

[

#### Create Instance Tree

Creates instances with given properties based on the given tree data table. This streamlines the tedious process of calling Instance.new and setting each property by creating a table of properties and a ClassName instead.

](https://create.roblox.com/marketplace/asset/13549427893)

Toevoegen aan inventaris

[

#### Crossfading Two Sounds

Crossfading is an audio editing technique that creates a smooth transition between two audio clips. Demonstrates crossfading between two sounds indefinitely.

](https://create.roblox.com/marketplace/asset/13549434117)

Toevoegen aan inventaris

[

#### Data Store Retries

DataStoreWrapper provides a retry mechanism for Data Stores that respects the order in which requests were made.

](https://create.roblox.com/marketplace/asset/13549442507)

Toevoegen aan inventaris

[

#### Donation Leaderboard

An example of a simple donation leaderboard. DevProducts IDs can be placed in the DonationProducts ModuleScript and will be displayed on the leaderboard to purchase. Upon purchase, the player's donation amount is incremented based on how many robux were spent.

](https://create.roblox.com/marketplace/asset/14045064871)

Toevoegen aan inventaris

[

#### Find First Child With Attribute

Searches children of an instance, returning the first child containing an attribute matching the given name and value. The DemoScript removes flavors from an ice cream cone in the correct order using findFirstChildWithAttribute

](https://create.roblox.com/marketplace/asset/13549448179)

Toevoegen aan inventaris

[

#### Raycasting

The fireRaycast function fires a ray from an Attachment position, visualizing the path of the ray and the surface normal that was hit. A model named "Device" rotates around in a circle, pointing the ray at various objects.

](https://create.roblox.com/marketplace/asset/13549459698)

Toevoegen aan inventaris

[

#### Model Following a Player

The FollowingAttachment module creates an attachment that trails on the ground at some max distance behind a player's character. DemoScript uses constraints to align a rock part's position and orientation with the attachment such that the rock follows each player's character. The attachment stops updating and the rock is destroyed when the character dies.

](https://create.roblox.com/marketplace/asset/13549504861)

Toevoegen aan inventaris

[

#### Format Time

Formats a number of seconds into a pretty string of Hours, Minutes, and Seconds. If all hours are 0, they are omitted. If all hours and all minutes are 0, they are both omitted. Leading 0's from hours are removed. If hours are omitted, leading 0's from minutes are removed. If hours and minutes are omitted, leading 0's from seconds are removed. The DemoScript uses formatTime to display a timer that rapidly increases on a Part.

](https://create.roblox.com/marketplace/asset/13549513767)

Toevoegen aan inventaris

[

#### Geofencing

Demonstrates a geofencing system to block content from users based on their region.

](https://create.roblox.com/marketplace/asset/13549574255)

Toevoegen aan inventaris

[

#### Get Character Attachment

Returns the attachment corresponding with AttachmentName under the character. The DemoScript uses getCharacterAttachment to correctly attach a pizza slice to a character's RightGripAttachment.

](https://create.roblox.com/marketplace/asset/13549617602)

Toevoegen aan inventaris

[

#### Input Categorizer

The InputCategorizer module categorizes various UserInputTypes (MouseButton1, MouseButton2, Gamepad1/2/3, etc.) into more manageable categories and provides an event for when the last input category changes, rather than last UserInputType.

](https://create.roblox.com/marketplace/asset/13595021558)

Toevoegen aan inventaris

[

#### Isometric Camera

Demonstrates how to update a player's camera to create an Isometric Camera style. The camera updates every render step to ensure the camera maintains a constant distance from the player, as well as follows the player as they move.

](https://create.roblox.com/marketplace/asset/13595027036)

Toevoegen aan inventaris

[

#### Leader Election

Demonstrates how to run a loop on a single server at once using MemoryStores. Useful for things like global matchmaking code that only need to run on one server at a time.

](https://create.roblox.com/marketplace/asset/13595031529)

Toevoegen aan inventaris

[

#### Lighting Presets

Demonstrates a system for storing lighting presets and updating the lighting settings from those presets. Presets can be set directly or tweened between to create e.g. a day/night cycle.

](https://create.roblox.com/marketplace/asset/14638386686)

Toevoegen aan inventaris

[

#### Playing an Animation

The loadAnimationTrack function is used to load an animation on an Animator by providing an animation asset ID.

](https://create.roblox.com/marketplace/asset/13595037394)

Toevoegen aan inventaris

[

#### Loading Screen

Demonstrates an example of a loading screen. The `updateDetailText` function provides the ability to update text on the loading screen with information on what is happening behind the scenes. A spinner gives the user confidence that the game is still running. Note: the sample must be placed within ReplicatedFirst to work properly.

](https://create.roblox.com/marketplace/asset/13595046452)

Toevoegen aan inventaris

[

#### Moderation System

Demonstrates a simple moderation system that can kick users from any server or ban them for arbitrary lengths of time.

](https://create.roblox.com/marketplace/asset/14638381501)

Toevoegen aan inventaris

[

#### Play Smoke Puff

Plays a particle animation of a puff of smoke at the location, volume, and size of a given part.

](https://create.roblox.com/marketplace/asset/13595063828)

Toevoegen aan inventaris

[

#### Player Lifecycle Events

Demonstrates connecting to common player, character and humanoid events. Events covered: PlayerAdded, PlayerRemoving, CharacterAdded, CharacterRemoving, CharacterAppearanceLoaded and Died (humanoid).

](https://create.roblox.com/marketplace/asset/13595067200)

Toevoegen aan inventaris

[

#### Portal Door

Demonstrates a portal door system that allows a player to walk into a small exterior building and appear inside a larger interior.

](https://create.roblox.com/marketplace/asset/14045095796)

Toevoegen aan inventaris

[

#### Retry Async

`retryAsync` retries function calls that may fail, and provides various arguments to describe the retry behavior. The first argument is the function it calls repeatedly until it either succeeds or is called the maximum number of times specified by `maxAttempts`. The optional third and fourth arguments allow you to customize the initial pause time and the exponent used to increase the pause time with each retry. The optional fifth argument allows you to specify a function call handler, used to make each function call (default is pcall). `retryAsync` returns a boolean indicating whether the final call to the given function was successful, and the return values of the final call (if successful) or the error message (if not successful). DemoScript provides an example using retryAsync to call a function that intentionally has a chance to error. Results of each call and the final result are printed.

](https://create.roblox.com/marketplace/asset/14638331353)

Toevoegen aan inventaris

[

#### Safe Player Added

Calls the given callback for all existing players in the game, and any that join thereafter. Useful in situations where you want to run code for every player, even players who are already in the game. The DemoScript uses safePlayerAdded to ensure all players in the game have a billboard with their name above their character's heads.

](https://create.roblox.com/marketplace/asset/13595075895)

Toevoegen aan inventaris

[

#### Custom Event

Signal is a custom event that works as a replacement for BindableEvents to create custom events and replicates the behavior of RBXScriptSignal. Objects are passed by reference, which is not possible with BindableEvents.

](https://create.roblox.com/marketplace/asset/13595083584)

Toevoegen aan inventaris

[

#### Sprint with Button

Demonstrates how to increase a player's speed when specific inputs are pressed. This sample implements left shift to run on keyboard, X to run on gamepad, and a touch button for mobile. The input buttons can be modified to any input desired.

](https://create.roblox.com/marketplace/asset/13595087289)

Toevoegen aan inventaris

[

#### ThreadQueue

ThreadQueue can be used to queue functions so that they don't all run at once. In this example, 10 functions are added to a queue at the same time, and then executed in order with a 1s delay between them.

](https://create.roblox.com/marketplace/asset/14638372891)

Toevoegen aan inventaris

[

#### Toggling Gui Frames

Demonstrates how to show and hide different frames within a Gui. The example starts with a menu button visible to the player. When pressed, the menu button is hidden and a menu window appears. Clicking the 'X' at the top right corner of the menu will bring the user back to the original view.

](https://create.roblox.com/marketplace/asset/13595092074)

Toevoegen aan inventaris

[

#### Tween Group

Links a group of tweens together, allowing them to be played, paused and cancelled as one. Note: TweenGroup does not support PlaybackState or Completed events.

](https://create.roblox.com/marketplace/asset/13595118497)

Toevoegen aan inventaris

[

#### Using TweenService on a Model

Demonstrates how to properly tween a model. Models should be tweened from an anchored part. If parts within the model are unanchored, weld these parts to the anchored part. Otherwise the unanchored parts will not follow the model as it tweens. In this case, the Base part is set as the HealthPack's PrimaryPart and all other parts in the model are welded to it.

](https://create.roblox.com/marketplace/asset/13595097154)

Toevoegen aan inventaris

[

#### Parallax Portal

Demonstrates a portal with a 'depth' effect achieved with parallaxing images.

](https://create.roblox.com/marketplace/asset/14375826814)

Toevoegen aan inventaris

[

#### Leaderboard Module

The Leaderboard Module updates a player's leaderboard with a name (statName) and value. The module creates the initial leaderboard as well as the stat for the player if it does not already exist. The demo used the Leaderboard Module to update all player's leaderboards with a "Points" stat that increases over time.

](https://create.roblox.com/marketplace/asset/14375819515)

Toevoegen aan inventaris

[

#### Purchase Handling

This sample demonstrates an approach to safely and robustly awarding developer product purchases to players

](https://create.roblox.com/marketplace/asset/14376223840)

Toevoegen aan inventaris

[

#### Player Data

This sample demonstrates an approach to storing and accessing player data

](https://create.roblox.com/marketplace/asset/14376214156)

Toevoegen aan inventaris

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
