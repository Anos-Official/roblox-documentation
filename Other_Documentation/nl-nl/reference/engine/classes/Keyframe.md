<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Keyframe -->

Keyframe | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [Keyframe](/docs/nl-nl/reference/engine/classes/Keyframe)

Nederlands

Feedback

Engine-klasse

Keyframe

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Keyframe)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Time](#Time) :[number](/docs/nl-nl/luau/numbers)

 |
| --- | --- |

Methoden

|

[AddMarker](#AddMarker) (marker :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

 |
|

[AddPose](#AddPose) (pose :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

 |
|

[GetMarkers](#GetMarkers) () : {[KeyframeMarker](/docs/nl-nl/reference/engine/classes/KeyframeMarker) }

 |
|

[GetPoses](#GetPoses) () : {[Pose](/docs/nl-nl/reference/engine/classes/Pose) }

 |
|

[RemoveMarker](#RemoveMarker) (marker :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

 |
|

[RemovePose](#RemovePose) (pose :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Keyframe Genereer Poses

```

local function generateKeyframe(model)

	if not model.PrimaryPart then

		warn("Geen primaire deel ingesteld")

		return

	end

	local rootPart = model.PrimaryPart:GetRootPart()

	if not rootPart then

		warn("Root deel niet gevonden")

		return

	end

	local partsAdded = {}

	partsAdded[rootPart] = true

	local function addPoses(part, parentPose)

		-- haal alle gewrichten op die aan het deel zijn bevestigd

		for _, joint in pairs(part:GetJoints()) do

			-- we zijn alleen geïnteresseerd in Motor6Ds

			if joint:IsA("Motor6D") then

				-- vind het verbonden deel

				local connectedPart = nil

				if joint.Part0 == part then

					connectedPart = joint.Part1

				elseif joint.Part1 == part then

					connectedPart = joint.Part0

				end

				if connectedPart then

					-- zorg ervoor dat we dit deel nog niet hebben toegevoegd

					if not partsAdded[connectedPart] then

						partsAdded[connectedPart] = true

						-- maak een pose aan

						local pose = Instance.new("Pose")

						pose.Name = connectedPart.Name

						parentPose:AddSubPose(pose)

						-- recursie

						addPoses(connectedPart, pose)

					end

				end

			end

		end

	end

	local keyframe = Instance.new("Keyframe")

	-- vul de keyframe

	local rootPose = Instance.new("Pose")

	rootPose.Name = rootPart.Name

	addPoses(rootPart, rootPose)

	keyframe:AddPose(rootPose)

	return keyframe

end

local character = script.Parent

local keyframe = generateKeyframe(character)

print(keyframe)

```

---

API-referentie

Eigenschappen

Time

Parallel lezen

Mogelijkheden: Animation

Keyframe.Time :[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

Krijg de lengte van KeyframeSequence

```

local function getSequenceLength(keyframeSequence)

	local length = 0

	for _, keyframe in pairs(keyframeSequence:GetKeyframes()) do

		if keyframe.Time > length then

			length = keyframe.Time

		end

	end

	return length

end

local keyframeSequence = Instance.new("KeyframeSequence")

getSequenceLength(keyframeSequence)

```

Feedback geven

---

Methoden

AddMarker

Mogelijkheden: Animation

Keyframe:AddMarker (marker :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

Parameters

|

marker :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Teruggaves

()

Codevoorbeelden

Marker Toevoegen/Marker Verwijderen

```

local keyframe = Instance.new("Keyframe")

keyframe.Parent = workspace

local marker = Instance.new("KeyframeMarker")

marker.Name = "FootStep"

marker.Value = 100

keyframe:AddMarker(marker) --marker.Parent = keyframe

task.wait(2)

keyframe:RemoveMarker(marker) --marker.Parent = nil

```

Feedback geven

---

AddPose

Mogelijkheden: Animation

Keyframe:AddPose (pose :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

Parameters

|

pose :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Teruggaves

()

Codevoorbeelden

Keyframe Genereer Poses

```

local function generateKeyframe(model)

	if not model.PrimaryPart then

		warn("Geen primaire deel ingesteld")

		return

	end

	local rootPart = model.PrimaryPart:GetRootPart()

	if not rootPart then

		warn("Root deel niet gevonden")

		return

	end

	local partsAdded = {}

	partsAdded[rootPart] = true

	local function addPoses(part, parentPose)

		-- haal alle gewrichten op die aan het deel zijn bevestigd

		for _, joint in pairs(part:GetJoints()) do

			-- we zijn alleen geïnteresseerd in Motor6Ds

			if joint:IsA("Motor6D") then

				-- vind het verbonden deel

				local connectedPart = nil

				if joint.Part0 == part then

					connectedPart = joint.Part1

				elseif joint.Part1 == part then

					connectedPart = joint.Part0

				end

				if connectedPart then

					-- zorg ervoor dat we dit deel nog niet hebben toegevoegd

					if not partsAdded[connectedPart] then

						partsAdded[connectedPart] = true

						-- maak een pose aan

						local pose = Instance.new("Pose")

						pose.Name = connectedPart.Name

						parentPose:AddSubPose(pose)

						-- recursie

						addPoses(connectedPart, pose)

					end

				end

			end

		end

	end

	local keyframe = Instance.new("Keyframe")

	-- vul de keyframe

	local rootPose = Instance.new("Pose")

	rootPose.Name = rootPart.Name

	addPoses(rootPart, rootPose)

	keyframe:AddPose(rootPose)

	return keyframe

end

local character = script.Parent

local keyframe = generateKeyframe(character)

print(keyframe)

```

Keyframe Toevoegen/Verwijderen Houding

```

local keyframe = Instance.new("Keyframe")

keyframe.Parent = workspace

local pose = Instance.new("Pose")

pose.EasingStyle = Enum.PoseEasingStyle.Cubic

pose.EasingDirection = Enum.PoseEasingDirection.Out

local pose2 = Instance.new("Pose")

pose2.EasingStyle = Enum.PoseEasingStyle.Cubic

pose2.EasingDirection = Enum.PoseEasingDirection.Out

keyframe:AddPose(pose) -- pose.Parent = keyframe

task.wait(2)

keyframe:RemovePose(pose) -- pose.Parent = nil

task.wait(2)

keyframe:AddPose(pose) -- pose.Parent = keyframe

task.wait(2)

pose:AddSubPose(pose2) -- pose2.Parent = pose

task.wait(2)

pose:RemoveSubPose(pose2) -- pose2.Parent = nil

```

Feedback geven

---

GetMarkers

Mogelijkheden: Animation

Keyframe:GetMarkers () : {[KeyframeMarker](/docs/nl-nl/reference/engine/classes/KeyframeMarker) }

Teruggaves

{[KeyframeMarker](/docs/nl-nl/reference/engine/classes/KeyframeMarker) }

Codevoorbeelden

Krijg Keyframe Markers Bevestigd aan een Keyframe

```

local keyframe = Instance.new("Keyframe")

keyframe.Parent = workspace

local marker1 = Instance.new("KeyframeMarker")

marker1.Name = "FootStep"

marker1.Value = 100

local marker2 = Instance.new("KeyframeMarker")

marker2.Name = "Wave"

marker2.Value = 100

keyframe:AddMarker(marker1) --marker.Parent = keyframe

keyframe:AddMarker(marker2) --marker.Parent = keyframe

local markers = keyframe:GetMarkers()

for _, marker in pairs(markers) do

	print(marker.Name)

end

```

Feedback geven

---

GetPoses

Mogelijkheden: Animation

Keyframe:GetPoses () : {[Pose](/docs/nl-nl/reference/engine/classes/Pose) }

Teruggaves

{[Pose](/docs/nl-nl/reference/engine/classes/Pose) }

Codevoorbeelden

Keyframe Reset Poses

```

local function resetPoses(parent)

	-- beide functies zijn gelijk aan GetChildren

	local poses = parent:IsA("Keyframe") and parent:GetPoses() or parent:IsA("Pose") and parent:GetSubPoses()

	for _, pose in pairs(poses) do

		if pose:IsA("Pose") then

			pose.CFrame = CFrame.new()

			-- recursief

			resetPoses(pose)

		end

	end

end

```

Feedback geven

---

RemoveMarker

Mogelijkheden: Animation

Keyframe:RemoveMarker (marker :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

Parameters

|

marker :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Teruggaves

()

Codevoorbeelden

Marker Toevoegen/Marker Verwijderen

```

local keyframe = Instance.new("Keyframe")

keyframe.Parent = workspace

local marker = Instance.new("KeyframeMarker")

marker.Name = "FootStep"

marker.Value = 100

keyframe:AddMarker(marker) --marker.Parent = keyframe

task.wait(2)

keyframe:RemoveMarker(marker) --marker.Parent = nil

```

Feedback geven

---

RemovePose

Mogelijkheden: Animation

Keyframe:RemovePose (pose :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

Parameters

|

pose :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Teruggaves

()

Codevoorbeelden

Keyframe Toevoegen/Verwijderen Houding

```

local keyframe = Instance.new("Keyframe")

keyframe.Parent = workspace

local pose = Instance.new("Pose")

pose.EasingStyle = Enum.PoseEasingStyle.Cubic

pose.EasingDirection = Enum.PoseEasingDirection.Out

local pose2 = Instance.new("Pose")

pose2.EasingStyle = Enum.PoseEasingStyle.Cubic

pose2.EasingDirection = Enum.PoseEasingDirection.Out

keyframe:AddPose(pose) -- pose.Parent = keyframe

task.wait(2)

keyframe:RemovePose(pose) -- pose.Parent = nil

task.wait(2)

keyframe:AddPose(pose) -- pose.Parent = keyframe

task.wait(2)

pose:AddSubPose(pose2) -- pose2.Parent = pose

task.wait(2)

pose:RemoveSubPose(pose2) -- pose2.Parent = nil

```

Feedback geven

---

Ga naar

▼

Keyframe

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[Time](#Time)

[Methoden](#methods)

[AddMarker()](#AddMarker)

[AddPose()](#AddPose)

[GetMarkers()](#GetMarkers)

[GetPoses()](#GetPoses)

[RemoveMarker()](#RemoveMarker)

[RemovePose()](#RemovePose)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
