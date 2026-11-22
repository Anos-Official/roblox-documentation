<!-- Source: https://create.roblox.com/docs/nl-nl/ui/video-frames -->

Videokaders | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Gebruikersinterface](/docs/nl-nl/ui)
6. /
7. UI-objecten

# Videokaders

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Video-assets die worden gebruikt in [VideoFrame](/docs/nl-nl/reference/engine/classes/VideoFrame) -instanties maken videoweergave in games mogelijk. Je kunt [video's uploaden](#videos-uploaden)  waarvan je zeker weet dat je toestemming hebt om ze te gebruiken, zoals video's die je zelf maakt, en het [privacy-systeem voor assets](/docs/nl-nl/projects/assets/privacy)  zorgt er automatisch voor dat de ID's van je geüploade video's niet toegankelijk zijn voor gebruikers zonder de juiste toestemming.

## [Video's uploaden](#videos-uploaden)[](#videos-uploaden)

Om video-assets te uploaden, schakel de bètakenmerk in via Bestand  ⟩ Bèta-functies  ⟩ Video Uploads .

Als je een 13+ [ID-geverifieerde](https://en.help.roblox.com/hc/en-us/articles/4407282410644-Age-ID-Verification)  gebruiker bent, kun je video's uploaden via de [Asset Manager](/docs/nl-nl/projects/assets/manager) , het [Creator Dashboard](https://create.roblox.com/dashboard/creations?activeTab=Video)  of de [Open Cloud API](/docs/nl-nl/cloud/guides/usage-assets) . Je kunt een video uploaden zolang deze voldoet aan de volgende vereisten:

-

Je hebt de wettelijke rechten om het video-asset te gebruiken.

-

Het voldoet aan de [Roblox Community Standards](https://en.help.roblox.com/hc/en-us/articles/203313410)  en [Terms of Use](https://en.help.roblox.com/hc/en-us/articles/115004647846) .

-

Het is 5 minuten of korter in .mp4  of .mov  formaat.

-

De resolutie is minder dan of gelijk aan 4096×2160.

-

Het is minder dan 3,75 GB.

Video's die niet aan deze vereisten voldoen, worden afgewezen. Alpha-kanalen worden niet ondersteund en worden genegeerd. Houd bij het uploaden van video's rekening met het volgende:

-

Elke video-upload kost 2.000 Robux.

-

Je kunt maximaal 20 video's per dag uploaden.

## [Video's afspelen](#videos-afspelen)[](#videos-afspelen)

Een [VideoFrame](/docs/nl-nl/reference/engine/classes/VideoFrame)  moet worden gekoppeld aan een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui) , [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui)  of [BillboardGui](/docs/nl-nl/reference/engine/classes/BillboardGui)  om afspeelbaar te zijn. Momenteel kunnen maximaal twee video's tegelijkertijd worden afgespeeld.

Om een video in je game af te spelen zonder code:

1.

Maak een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  zoals beschreven in [On-Screen UI Containers](/docs/nl-nl/ui/on-screen-containers) , of een [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui)  of [BillboardGui](/docs/nl-nl/reference/engine/classes/BillboardGui)  zoals beschreven in [In-game UI containers](/docs/nl-nl/ui/in-experience-containers) .

2.

Voeg een video toe vanuit de [Toolbox](/docs/nl-nl/projects/assets/toolbox)  of [Asset Manager](/docs/nl-nl/projects/assets/manager) . Een nieuw [VideoFrame](/docs/nl-nl/reference/engine/classes/VideoFrame) -object wordt ingevoegd voor de video.

3.

Koppel de [VideoFrame](/docs/nl-nl/reference/engine/classes/VideoFrame)  aan de container.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/StarterGui-ScreenGui-VideoFrame.png)

4.

Met de nieuwe [VideoFrame](/docs/nl-nl/reference/engine/classes/VideoFrame)  geselecteerd, schakel je de eigenschappen Looped  en Playing  in het [Properties](/docs/nl-nl/studio/properties)  venster in.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/VideoFrame-Looped-Playing.png)

Als je een video in je game wilt afspelen met code, plak dan de volgende code in een [Script](/docs/nl-nl/reference/engine/classes/Script)  binnen [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService)  om een [Part](/docs/nl-nl/reference/engine/classes/Part)  te maken en de video op het voorste oppervlak af te spelen.

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

videoFrame.Video = "rbxassetid://5608384572"  -- Vervang door de asset-ID van jouw video

while not videoFrame.IsLoaded do

	videoFrame.Loaded:Wait()

end

videoFrame:Play()

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
