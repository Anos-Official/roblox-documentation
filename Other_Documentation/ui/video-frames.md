<!-- Source: https://create.roblox.com/docs/ui/video-frames -->

Video frames | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/ui/video-frames.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [User interface](/docs/ui)
6. /
7. UI objects

# Video frames

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/ui/video-frames.md)

Video assets used in [VideoFrame](/docs/reference/engine/classes/VideoFrame)  instances allow for video playback in games. You can [upload](#upload-videos)  videos that you're certain you have permission to use, such as videos you make yourself, and the [asset privacy](/docs/projects/assets/privacy)  system automatically ensures that the IDs of your uploaded videos can't be accessed by users without the proper permissions.

## [Upload videos](#upload-videos)[](#upload-videos)

To upload video assets, enable the beta feature through File  ⟩ Beta Features  ⟩ Video Uploads .

If you're a 13+ [ID verified](https://en.help.roblox.com/hc/en-us/articles/4407282410644-Age-ID-Verification)  user, you can upload videos through the [Asset Manager](/docs/projects/assets/manager) , the [Creator Dashboard](https://create.roblox.com/dashboard/creations?activeTab=Video) , or the [Open Cloud API](/docs/cloud/guides/usage-assets) . You can upload a video as long as it meets the following requirements:

-

You have the legal rights to use the video asset.

-

It adheres to the [Roblox Community Standards](https://en.help.roblox.com/hc/en-us/articles/203313410)  and [Terms of Use](https://en.help.roblox.com/hc/en-us/articles/115004647846) .

-

It's 5 minutes or less in either .mp4  or .mov  format.

-

Its resolution is less than or equal to 4096×2160.

-

It's less than 3.75 GB.

Videos that don't meet these requirements are rejected. Alpha channels are not supported and will be ignored. When uploading videos, consider the following:

-

Each video upload costs 2,000 Robux.

-

You can upload a maximum of 20 videos a day.

## [Play videos](#play-videos)[](#play-videos)

A [VideoFrame](/docs/reference/engine/classes/VideoFrame)  must be parented to a [ScreenGui](/docs/reference/engine/classes/ScreenGui) , [SurfaceGui](/docs/reference/engine/classes/SurfaceGui) , or [BillboardGui](/docs/reference/engine/classes/BillboardGui)  in order to be playable. Currently, a maximum of two videos can play simultaneously.

To play a video in your game without code:

1.

Create a [ScreenGui](/docs/reference/engine/classes/ScreenGui)  as outlined in [On-Screen UI Containers](/docs/ui/on-screen-containers) , or a [SurfaceGui](/docs/reference/engine/classes/SurfaceGui)  or [BillboardGui](/docs/reference/engine/classes/BillboardGui)  as outlined in [In-game UI containers](/docs/ui/in-experience-containers) .

2.

Insert a video from the [Toolbox](/docs/projects/assets/toolbox)  or [Asset Manager](/docs/projects/assets/manager) . A new [VideoFrame](/docs/reference/engine/classes/VideoFrame)  object is inserted for the video.

3.

Parent the [VideoFrame](/docs/reference/engine/classes/VideoFrame)  to the container.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/StarterGui-ScreenGui-VideoFrame.png)

4.

With the new [VideoFrame](/docs/reference/engine/classes/VideoFrame)  selected, enable its Looped  and Playing  properties in the [Properties](/docs/studio/properties)  window.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/VideoFrame-Looped-Playing.png)

If you want to play a video in your game with code, paste the following code into a [Script](/docs/reference/engine/classes/Script)  within [ServerScriptService](/docs/reference/engine/classes/ServerScriptService)  to create a [Part](/docs/reference/engine/classes/Part)  and play the video on its front surface.

```

local Workspace = game:GetService("Workspace")

local screenPart = Instance.new("Part")

screenPart.Size = Vector3.new(16, 9, 1)

screenPart.Position = Vector3.new(0, 8, -20)

screenPart.Orientation = Vector3.new(0, 180, 0)

screenPart.Anchored = true

screenPart.Parent = Workspace

local surfaceGui = Instance.new("SurfaceGui")

surfaceGui.Parent = screenPart

local videoFrame = Instance.new("VideoFrame")

videoFrame.Size = UDim2.new(1, 0, 1, 0)

videoFrame.Parent = surfaceGui

videoFrame.Looped = true

videoFrame.Video = "rbxassetid://5608384572"  -- Replace with your video's asset ID

while not videoFrame.IsLoaded do

	videoFrame.Loaded:Wait()

end

videoFrame:Play()

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
