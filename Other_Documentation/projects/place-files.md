<!-- Source: https://create.roblox.com/docs/projects/place-files -->

Place files | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/projects/place-files.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Projects](/docs/projects)
6. /
7. [Games and places](/docs/production/publishing/publish-games-and-places)

# Place files

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/projects/place-files.md)

Each Roblox game consists of one or more [places](/docs/projects#places) , and Studio uploads your place data to Roblox's servers whenever you save or publish to Roblox in the File  menu.

You might also want to export local copies of places for use with a version control system or other [external tools](/docs/projects/external-tools) . To export your place in Studio, select Save to File  or Download a Copy  from the File  menu. Studio offers two file formats:

-

.rbxl  is the binary place file format. This format is compact, but not human-readable.

-

.rbxlx  is the XML-based place file format, which is quite a bit larger on disk than the binary format.

Roblox supports places up to 100 MB (104,857,600 bytes). Beyond that limit, Save to Roblox  and Publish to Roblox  might fail. The data that Studio uploads to Roblox is slightly smaller than the .rbxl  file format, so you can export your place to .rbxl  to get a sense of its size.

Very few places, even the most complex ones, reach this limit, and when they do, it's often due to inefficiencies in the place. See [Troubleshooting](/docs/projects/place-files#troubleshoot-place-file-size) .

## [Auto-recovery files](#auto-recovery-files)[](#auto-recovery-files)

If saving to Roblox fails due to the file size limit, Studio automatically generates a backup of your place called a recovery file . The frequency of auto-recovery backups depends on whether your game has [collaboration](/docs/projects/collaboration)  enabled:

-

If you have collaboration enabled and saving to Roblox fails, Studio backs up the last three save attempts as recovery files on your system.

-

If collaboration is disabled, Studio uses Auto-Recovery  settings from [Studio Settings](/docs/studio/setup#customization) .

On Windows, recovery files are located in C:\Users\Admin\AppData\Local\Roblox\RobloxStudio\AutoSaves .

On Mac, you can find them in /Users/your-username/Library/Application Support/Roblox/RobloxStudio/AutoSaves/ .

## [Troubleshoot place file size](#troubleshoot-place-file-size)[](#troubleshoot-place-file-size)

If you reach the 100 MB limit on your place file, there's likely an underlying issue that you can troubleshoot. Try the following steps.

### [Safety check](#safety-check)[](#safety-check)

Check the models in your place and their attached scripts for any obfuscated or unclear text. This text does not compress well and might even be a malicious backdoor into your place. Roblox moderation systems actively filter out these models, but if you happen to find one, delete the model from your place, find the model on the [Creator Store](https://create.roblox.com/store/models) , and report it immediately.

### [Redundant parts](#redundant-parts)[](#redundant-parts)

Unreferenced or hidden assets can accumulate over time and unnecessarily increase file size.

1.

See if any models or groups of parts are taking up more space than others:

1.

Export your place file and note its size on disk.

2.

Open the file in Roblox Studio.

3.

Copy and paste the models or groups of parts that you suspect are inordinately large.

4.

Save the file again and note its increase in file size.

2.

Check for redundant parts (parts of the same size and shape with the same position) or instances (redundant [SurfaceAppearances](/docs/reference/engine/classes/SurfaceAppearance) , textures, etc.) and delete them. The Creator Store has plugins that can help you identify these cases.

### [Simplify terrain](#simplify-terrain)[](#simplify-terrain)

Reducing or simplifying terrain can significantly reduce place size and improve performance. Avoiding excessive terrain features like dense forests or complex hills helps make games run faster and more efficiently. Of course, the game should match your artistic vision, but consider the following optimizations:

1.

Horizontal layers of the same material/occupancy compress much better than sloped layers. If possible, try to limit subsurface detail to horizontal layers.

2.

Turn on Show Wireframe Rendering  from Studio's View  menu and check for messy holes or misplaced water under the terrain surface. These mistakes can increase compressed size.

3.

There are community plugins that optimize non-visible blocks of terrain for better compression, such as [this one](https://create.roblox.com/store/asset/133396894381603/Terrain-File-Size-Optimizer) .

### [Collision fidelity](#collision-fidelity)[](#collision-fidelity)

[Box](/docs/reference/engine/enums/CollisionFidelity#Box)  and [Hull](/docs/reference/engine/enums/CollisionFidelity#Hull)  collision fidelity are more memory efficient than the default. Select your meshes, open the [Properties](/docs/studio/properties)  window, and change the CollisionFidelity  values as appropriate for your use case.

### [Teleports](#teleports)[](#teleports)

If other size reduction strategies fail, you can break your place into multiple, smaller places and link them through [teleports](/docs/projects/teleport) . Serialization and upload happen at the place level, so this approach lets you grow your universe place by place over time instead of trying to maintain a single, massive place.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
