<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Pose -->

Pose | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [PoseBase](/docs/nl-nl/reference/engine/classes/PoseBase)
8. /
9. [Pose](/docs/nl-nl/reference/engine/classes/Pose)

Nederlands

Feedback

Engine-klasse

Pose

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Pose)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[CFrame](#CFrame) :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

 |
| --- | --- |
|

[MaskWeight](#MaskWeight) :[number](/docs/nl-nl/luau/numbers)

Verouderd

 |

Methoden

|

[AddSubPose](#AddSubPose) (pose :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

 |
|

[GetSubPoses](#GetSubPoses) () : Instances

 |
|

[RemoveSubPose](#RemoveSubPose) (pose :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

 |

Overgenomen leden

3  overgenomen van [PoseBase](/docs/nl-nl/reference/engine/classes/PoseBase)

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

---

API-referentie

Eigenschappen

CFrame

Parallel lezen

Mogelijkheden: Animation

Pose.CFrame :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

Feedback geven

---

MaskWeight

Verouderd

Details weergeven

---

Methoden

AddSubPose

Mogelijkheden: Animation

Pose:AddSubPose (pose :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

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

GetSubPoses

Mogelijkheden: Animation

Pose:GetSubPoses () : Instances

Teruggaves

Instances

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

RemoveSubPose

Mogelijkheden: Animation

Pose:RemoveSubPose (pose :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

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

Pose

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[CFrame](#CFrame)

[MaskWeight](#MaskWeight)

[Methoden](#methods)

[AddSubPose()](#AddSubPose)

[GetSubPoses()](#GetSubPoses)

[RemoveSubPose()](#RemoveSubPose)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
