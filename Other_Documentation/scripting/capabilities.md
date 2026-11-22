<!-- Source: https://create.roblox.com/docs/scripting/capabilities -->

Script capabilities | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/scripting/capabilities.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Scripting](/docs/scripting)
6. /
7. Advanced

# Script capabilities

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/scripting/capabilities.md)

Script capabilities are experimental and available as a client beta.

Script capabilities  let you control which actions scripts can perform inside the [DataModel](/docs/reference/engine/classes/DataModel)  subtree. Rather than the default "all-or-nothing system," you can set a script to only be able to access certain categories, such as audio, physics, data stores, and more.

-

This system lets you limit what models taken from the toolbox can do and makes it easier to include user-generated content inside the game.

-

It can also help ensure better security of games that allow players to run their own code, which is often executed in a restricted or emulated environment.

-

It can also be used to share libraries that restrict what they can do themselves. For example, a library providing additional math methods can be restricted to the smallest set of capabilities it needs so that other developers using that library don't have to validate the entire codebase to make sure it doesn't include malicious code.

## [Enable script capabilities](#enable-script-capabilities)[](#enable-script-capabilities)

To enable this feature, change the [SandboxedInstanceMode](/docs/reference/engine/classes/Workspace#SandboxedInstanceMode)  property from Default  to Experimental  in the Explorer  and Properties  window.

## [Sandboxed container](#sandboxed-container)[](#sandboxed-container)

Script capabilities introduces a concept of a sandboxed container . [Models](/docs/reference/engine/classes/Model) , [Folders](/docs/reference/engine/classes/Folder) , [Scripts](/docs/reference/engine/classes/Script) , or descendants of any of those classes have a [Sandboxed](/docs/reference/engine/classes/Instance#Sandboxed)  property available in the Properties  window.

 ![Sandboxed property of a Folder in the Properties window.](https://prod.docsiteassets.roblox.com/assets/studio/properties/Folder-Sandboxed.png)

Enabling the [Sandboxed](/docs/reference/engine/classes/Instance#Sandboxed)  property designates the instance as a sandboxed container inside the [DataModel](/docs/reference/engine/classes/DataModel)  tree, which limits the actions that the scripts inside that container can perform based on the set of values in the [Capabilities](/docs/reference/engine/classes/Instance#Capabilities)  property.

## [Capabilities](#capabilities)[](#capabilities)

The Capabilities  property is a set of values that control different aspects of execution. Capabilities fall into the following broad categories:

-

Execution control  - Specifies if a script can run on client or server

-

Instance access control  - Specifies which [DataModel](/docs/reference/engine/classes/DataModel)  parts a script can interact with

-

Script functionality control  - Specifies which Luau functions scripts can call

-

Engine API access control  - Specifies which parts of the Roblox Engine API can be used

When a script attempts to perform an action that is not in the set of capabilities, Roblox reports an error. Errors typically include the action being attempted, the target of an action, and the first capability that is missing:

```

The current thread cannot modify 'Workspace' (lacking capability AccessOutsideWrite)

The current thread cannot call 'Clone' (lacking capability CreateInstances)

The current thread cannot call 'GetSecret' (lacking capability Network)

```

### [Execution control](#execution-control)[](#execution-control)

Two capabilities handle execution control:

-

RunClientScript  - [LocalScript](/docs/reference/engine/classes/LocalScript)  or [Script](/docs/reference/engine/classes/Script)  with a [RunContext](/docs/reference/engine/classes/BaseScript#RunContext)  value of [Client](/docs/reference/engine/enums/RunContext#Client)  is allowed to execute on the client

-

RunServerScript  - [Script](/docs/reference/engine/classes/Script)  with a [RunContext](/docs/reference/engine/classes/BaseScript#RunContext)  value of [Server](/docs/reference/engine/enums/RunContext#Server)  is allowed to execute on the server

If the script is [Enabled](/docs/reference/engine/classes/BaseScript#Enabled) , but the capability corresponding to the location it attempts to start in is not available, a warning message is displayed in the Output  window. If a script wasn't supposed to run in that context, disable or delete it.

Note that [ModuleScripts](/docs/reference/engine/classes/ModuleScript)  do not need to have these execution capabilities to be required.

When a script fails to start because the execution control capability is missing, it is reported as a warning in the output, for example:

```

Cannot start server script 'Script' (lacking capability RunServerScript)

```

### [Instance access control](#instance-access-control)[](#instance-access-control)

A single capability handles instance access control:

-

AccessOutsideWrite  - Script is allowed to fetch and receive instances from outside the sandboxed container

When the capability is not available, the script can only look up instances that are inside its own sandboxed container. For example, if the script is placed directly in the sandboxed container, script.Parent.Parent  returns nil .

Additionally, any Roblox API event that passes in an [Instance](/docs/reference/engine/classes/Instance)  instead passes in nil  for any [Instance](/docs/reference/engine/classes/Instance)  outside the sandboxed container. For example, if the [BasePart.Touched](/docs/reference/engine/classes/BasePart#Touched)  is signaled by a touch from an instance outside the sandboxed container, the event is still received, but the argument is nil .

Avoid setting this capability; sandboxing guarantees are weaker when scripts can interact with any instance in a game.

#### [Access to services](#access-to-services)[](#access-to-services)

Even without AccessOutsideWrite , scripts in the sandboxed container can still access game , workspace , and services. This access is provided so that scripts can still call useful methods of those globals, like [DataModel.GetService](/docs/reference/engine/classes/DataModel#GetService) , but access to their child instances is still validated.

#### [Internally passed instances](#internally-passed-instances)[](#internally-passed-instances)

If an instance is passed through a function call that doesn't go through Roblox APIs, the reference is preserved. However, if a [ModuleScript](/docs/reference/engine/classes/ModuleScript)  is passed in this way, it can't be required without AccessOutsideWrite . This is because the return of the [ModuleScript](/docs/reference/engine/classes/ModuleScript)  is often mutable and can be modified by a script in a sandboxed container.

### [Script functionality control](#script-functionality-control)[](#script-functionality-control)

This set of capabilities controls some general aspects of scripts:

-

CreateInstances  - Script can create new instances using [Instance.new](/docs/reference/engine/datatypes/Instance#new) , [Instance.fromExisting](/docs/reference/engine/datatypes/Instance#fromExisting) , or [Instance:Clone()](/docs/reference/engine/classes/Instance#Clone)

-

LoadString  - Script is allowed to call [loadstring](/docs/reference/engine/globals/LuaGlobals#loadstring)

-

LoadUnownedAsset  - Script is allowed to call [require](/docs/reference/engine/globals/LuaGlobals#require)  with an asset ID or [AssetService:LoadAssetAsync()](/docs/reference/engine/classes/AssetService#LoadAssetAsync)

-

ScriptGlobals  - Script has [shared](/docs/reference/engine/globals/LuaGlobals#shared)  and [_G](/docs/reference/engine/globals/LuaGlobals#_G)  available

Keep in mind that default function restrictions still apply. Even if LoadString  is enabled, the game still has to enable it in [ServerScriptService](/docs/reference/engine/classes/ServerScriptService) , and it is still only available on the server.

To create new instances, aside from CreateInstances , an additional Engine API capability providing access to that instance is required.

### [Engine API access control](#engine-api-access-control)[](#engine-api-access-control)

This last group of capabilities controls script access to various Engine APIs:

-

Animation  - Access to instances related to animations

-

AssetCreateUpdate  - Access to Engine APIs related to creating or updating assets

-

AssetManagement  - Access to Engine APIs related to operations on assets that are not read, create, or update

-

AssetRead  - Access to Engine APIs related to getting information about assets

-

Audio  - Access to instances related to audio APIs

-

AvatarAppearance  - Access to instances related to the visual elements of avatars

-

AvatarBehavior  - Access to Engine APIs related to controlling or modifying the humanoid

-

Basic  - Access to general APIs that offer little risk

-

CSG  - Access to instances and functions related to constructive solid geometry (CSG)

-

CapabilityControl  - Access to modifying the Sandboxed  and Capabilities  properties of instances

-

Capture  - Access to Engine APIs related to capturing screenshots or videos on the user's screen

-

Chat  - Access to instances related to in-game chat

-

Consequences  - Access to APIs for punishing users (kicks or bans)

-

DataStore  - Access to data store and memory store APIs

-

DynamicGeneration  - Access to Engine APIs related to dynamically modifying assets

-

Environment  - Access to instances related to the control of how the environment is displayed

-

Groups  - Access to Engine APIs relating to groups/communities

-

Input  - Access to instances related to user input

-

LegacySound  - Access to Engine APIs related to sound that will be deprecated

-

LoadOwnedAsset  - Access to Engine APIs for loading assets that are owned by you, shared to you, owned by Roblox, or are a benign asset type

-

Logging  - Access to the logs API

-

Material  - Access to Engine APIs related to materials

-

Monetization  - Access to Engine APIs related to monetizing a game, excluding most PromptPurchases

-

Network  - Access to HTTP networking APIs

-

Physics  - Access to instances related to physics

-

PlatformAvatarEditing  - Access to Engine APIs related to creating or updating avatars, or APIs to aid with that

-

Players  - Access to Engine APIs related to the [Player](/docs/reference/engine/classes/Player)  class or that return/interact with [Players.LocalPlayer](/docs/reference/engine/classes/Players#LocalPlayer)

-

PromptExternalPurchase  - Allows access to Engine APIs related to prompting purchase of arbitrary assets

-

RemoteEvent  - Access to instances for internal networking operations

-

SensitiveInput  - Access to Engine APIs related to capturing sensitive input from the user, i.e. high-privacy hardware sensors.

-

ServerCommunication  - Access to Engine APIs related to cross-server communication, such as [MessagingService](/docs/reference/engine/classes/MessagingService)

-

Social  - Access to Engine APIs related to social features, such as friends and invites

-

Teleport  - Access to Engine APIs related to teleporting

-

UI  - Access to instances related to user interfaces

The capabilities of each class, property, method, and event are displayed in the [Engine API reference](/docs/../reference/engine) . For example, [Player:GetFriendsOnlineAsync()](/docs/reference/engine/classes/Player#GetFriendsOnlineAsync)  requires the Player  and Social  capabilities.

Several [HttpService](/docs/reference/engine/classes/HttpService)  methods are available without any capabilities aside from being able to execute the scripts:

-

[HttpService:JSONDecode()](/docs/reference/engine/classes/HttpService#JSONDecode)

-

[HttpService:JSONEncode()](/docs/reference/engine/classes/HttpService#JSONEncode)

-

[HttpService:GenerateGUID()](/docs/reference/engine/classes/HttpService#GenerateGUID)

If an instance property or method is accessed without a required capability, an error is reported describing the missing capability.

Finally, capabilities do not cover every instance in the Roblox Engine today. Instances not listed in this section or the following one are not available for interaction from a sandboxed container and throw an error saying that an Unassigned  capability is not available to the current script.

An additional limitation is that [getfenv()](/docs/reference/engine/globals/LuaGlobals#getfenv)  and [setfenv()](/docs/reference/engine/globals/LuaGlobals#setfenv)  functions are not available for scripts in a sandboxed container. Calling them from a sandboxed script reports:

```

The current thread cannot call ['getfenv'/'setfenv'] - the target uses APIs not available in the current sandbox

```

Only script access to instances is limited. The instances themselves can still exist and operate by themselves inside a sandboxed container. Lights still shine, user interfaces are still visible, and audio setups that are already wired play sounds.

## [Interactions between containers](#interactions-between-containers)[](#interactions-between-containers)

### [Nested containers](#nested-containers)[](#nested-containers)

When one sandboxed container is nested inside another one, the instances of the inner container are accessible to the outer one.

Capabilities of the inner container are limited by the capabilities of the outer one. For example, if the outer container has capabilities of Basic , Audio  and CSG , while the inner container has Basic  and Network , only Basic  capabilities are available to the inner container at runtime.

If there are no capabilities in common between the inner and outer containers, the resulting capability set is empty.

### [Bindable functions and events](#bindable-functions-and-events)[](#bindable-functions-and-events)

[BindableEvent](/docs/reference/engine/classes/BindableEvent)  and [BindableFunction](/docs/reference/engine/classes/BindableFunction)  provide the best way to communicate with the container or allow it to run callbacks with capabilities it itself is not allowed to use directly.

When an event is fired or a function is invoked, connections are executed in the context of the function that registered them. This means that if the event or function callback is registered by the sandboxed container, it is called with the capabilities of that container. If the callback is registered by the code outside, when sandboxed container scripts invoke them, they execute your functions with capabilities available to your functions.

It is important to note that even with the AccessOutsideWrite  capability, scripts in sandboxed containers cannot invoke events or functions outside their containers if they have a larger capability set than the container itself.

When a sandboxed script tries to fire or invoke an event or function ([BindableEvent](/docs/reference/engine/classes/BindableEvent) , [BindableFunction](/docs/reference/engine/classes/BindableFunction) , or [RemoteEvent](/docs/reference/engine/classes/RemoteEvent) ) whose ancestor capabilities exceed its own, the error names the property to inspect.

If the target is not inside any sandboxed container:

```

The current thread cannot fire '<Target>' since '<Target>' has the Sandboxed property set to false but the calling thread is sandboxed

```

To resolve this, set [Sandboxed](/docs/reference/engine/classes/Instance#Sandboxed)  to true  for the target. Alternatively, you can modify the source of the calling thread to have [Sandboxed](/docs/reference/engine/classes/Instance#Sandboxed)  set to false , but this is not recommended as it eliminates the security benefits sandboxing provides.

If the target is sandboxed but has capabilities the caller lacks:

```

The current thread cannot fire '<Target>' since '<Target>' has additional values for the Capabilities property: <First Missing Capability> (and N more)

```

To resolve this, narrow the target's [Capabilities](/docs/reference/engine/classes/Instance#Capabilities)  to a subset of the caller's, or expand the caller's [Capabilities](/docs/reference/engine/classes/Instance#Capabilities)  to match the target's.

### [Module require](#module-require)[](#module-require)

Inner [ModuleScripts](/docs/reference/engine/classes/ModuleScript)  can be required by the sandboxed container as usual. However, if the target instance is outside the container, the [ModuleScript](/docs/reference/engine/classes/ModuleScript)  can only be required if the capability set that is available to it is smaller or equal to the capabilities available to the container.

This limitation does not apply to RunClientScript  and RunServerScript  capabilities. If the [ModuleScript](/docs/reference/engine/classes/ModuleScript)  is placed in a container with only RunClientScript  but is required from a script that has the RunServerScript  capability, it is allowed to succeed and run those functions on the server.

When [require()](/docs/reference/engine/globals/LuaGlobals#require)  fails on a capability mismatch, the error names the target module and the property to inspect in the same manner as Bindable functions and events described in the previous section.

### [Directly called functions](#directly-called-functions)[](#directly-called-functions)

If a [ModuleScript](/docs/reference/engine/classes/ModuleScript)  in a sandboxed container is required from outside the container, some of the protections are not available. In particular, the target function is able to access all instances available to the caller. If the caller is not in a sandboxed container, the call acts as if AccessOutsideWrite  is available to it.

Other capability restrictions still apply. If you have a DataStore  access capability, but the target module does not, it is unable to call [DataStore](/docs/reference/engine/classes/DataStore)  methods. However, if you pass your own function working with [DataStore](/docs/reference/engine/classes/DataStore) , the target can run it during that call. If the target schedules a thread using methods like those from [task](/docs/reference/engine/libraries/task) , those threads lose the ability to call that function.

Instances can be passed to the target module or assigned to the module fields.

If required, it is recommended to assign table members using [rawset](/docs/reference/engine/globals/LuaGlobals#rawset)  to avoid running __index / __newindex  metamethods that might be set on the table.

The overall recommendation is to communicate with [BindableEvent](/docs/reference/engine/classes/BindableEvent)  and [BindableFunction](/docs/reference/engine/classes/BindableFunction)  whenever possible.

### [Movement of instances](#movement-of-instances)[](#movement-of-instances)

Most instances do not have restrictions on movement between containers. Script instances, however, can only be moved into a container that has the same set of capabilities or a subset of those capabilities.

This means that a sandboxed container with AccessOutsideWrite  cannot just re-parent a script inside itself to outside and get more capabilities.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
