<!-- Source: https://create.roblox.com/docs/en-us/projects -->

Projects | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/projects.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Projects](/docs/en-us/projects)

# Projects

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/projects/index.md)

A Roblox project is a collection of [places](#places) , [assets](#assets) , [settings](#settings) , and other resources that together represent a game . Roblox stores your projects in the cloud for convenient collaboration, editing, and version control. You create and manage projects with [Roblox Studio](/docs/en-us/studio) , an all‑in‑one IDE that provides building, scripting, testing, and publishing tools.

## [Places](#places)[](#places)

Games on Roblox are made up of individual places , comparable to scenes in Unity or maps in Unreal Engine. Each place contains all components for that portion of the game, including its specific environment, parts, meshes, scripts, and user interface.

See the pages for [creating and publishing](/docs/en-us/production/publishing/publish-games-and-places) , [configuring](/docs/en-us/projects/configure-games) , and [updating](/docs/en-us/projects/update-games)  games and places for details.

![A game grouping of three individual places with unique environments.](https://prod.docsiteassets.roblox.com/assets/publishing/experiences-places-assets/Experience-Hierarchy.png)

Every place is represented by a data model , a hierarchy of objects that describe everything about the place. The Roblox Engine uses the data model as a source of truth for a place's state, so it can simulate and render it on client devices. For more information on how the engine interprets the data model, see [Client-server runtime](/docs/en-us/projects/client-server) .

Proper, intentional object organization within the data model is essential for functionality and maintenance of your project. For more information on what objects are available and how to organize and use them, see [Data model](/docs/en-us/projects/data-model) .

## [Assets](#assets)[](#assets)

In Roblox, assets such as images, meshes, and audio are stored as cloud-based assets , so you don't need to bundle local copies into a saved Studio game. Each asset in the cloud is assigned a unique asset ID  from which multiple games can utilize them. You can create assets directly in Studio, such as models, or import assets like images, audio, and meshes from other tools.

rbxassetid://7229442422

![A decal asset of a young woman with a button for an eye.](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Texture-Example-Grafitti04.png)

rbxassetid://6768917255

![An untextured treasure chest MeshPart asset.](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Base-Mesh-In-Marketplace.png)

rbxassetid://9125402735

By default, assets are private to your game and you can use an asset in any place by referencing its ID. You can also distribute them to the community in the [Creator Store](https://create.roblox.com/store/) , so others can use them as well.

For more information on how to import and publish assets, see [Assets](/docs/en-us/projects/assets) .

## [Packages](#packages)[](#packages)

[Packages](/docs/en-us/projects/assets/packages)  are reusable object hierarchies that you can define and reuse in multiple places across multiple games. For any large project, packages offer the following benefits:

-

Packages can be used as asset kits, allowing you to duplicate a set of objects as needed.

-

Packages make it easier to update assets. For instance, a package can include a tree that's duplicated many times in an environment. If you need to make a change, such as swap textures for the tree, it can be updated once in the package instead of for each individual instance.

-

A package can start with graybox assets, and eventually be replaced with final art assets. When assets are replaced, they retain all original positions and orientations.

## [Settings](#settings)[](#settings)

Game settings are managed from the [Creator Dashboard](https://create.roblox.com/dashboard/creations)  or within Studio, including:

-

Basic Info  — Basic information about the game, such as its name, description, and genre. Much of the information here is used in your game's listing.

-

Communication  — Settings which enable eligible users to use [voice chat](/docs/en-us/chat/voice-chat)  or animate their avatar via their camera within your game.

-

Permissions  — Configures who can access your game. When games are first published, they are only accessible to you as the creator, users with Edit  or Playtest  access, and group members with the appropriate [roles and permissions](/docs/en-us/projects/groups#roles-and-permissions) . When you're ready, you can [release](/docs/en-us/production/publishing/publish-games-and-places#release-games)  the game to a wider audience.

-

Monetization  — Options for earning revenue from your game, as outlined in [Monetization](/docs/en-us/production/monetization) .

-

Localization  — Configuration for different [languages and regions](/docs/en-us/production/localization) .

-

Avatar  — Settings related to avatars, such as avatar scaling and clothing overrides.

## [Collaboration](#collaboration)[](#collaboration)

With Studio's built-in collaboration tools , team members can contribute to games independently on their own time, or alongside others. Key features include:

-

Group admins can manage which members have access to collaborate and which do not, effectively maintaining proper roles within a large team.

-

Collaborators can build alongside other team members in real time and automatically see changes made by others.

-

Collaborators can independently edit the same scripts that others may be editing, test locally, and commit their changes to the cloud-based project when ready.

For more information, see [Collaboration](/docs/en-us/projects/collaboration) .

## [Testing](#testing)[](#testing)

Your [team](/docs/en-us/projects/groups)  can instantly test a game on PC, mobile, VR, and other devices you wish to support through the Roblox app; no need to compile builds, deploy to app stores, or await app store approval.

Studio offers a suite of options for testing a game before releasing it to the public:

-

Rapid playtesting  that provides a close simulation of the game running on the Roblox application.

-

Multi-client simulation  for comparing how each client "sees" other clients within the game.

-

Device emulation  that provides insight on how controls operate on a mobile device or how on-screen UI displays on different screens and aspect ratios.

-

Collaborative playtesting  with members of your team.

For more information on each testing option, see [Studio testing modes](/docs/en-us/studio/testing-modes) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
