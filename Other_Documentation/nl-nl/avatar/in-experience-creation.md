<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/in-experience-creation -->

Avatar in-experience creatie | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. In-game creation

# Avatar in-experience creatie

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De volgende gids is van toepassing op makers die bekend zijn met scripting en Roblox Studio en van plan zijn ervaringen te ontwikkelen die gebruikersgegenereerde avataritems mogelijk maken.

Je kunt een ervaring publiceren die spelers in staat stelt om avatars in realtime te maken, aan te passen en aan te schaffen, naast [in-experience make-up creatie](/docs/nl-nl/avatar/in-experience-creation-makeup) . Wanneer deze aangepaste items worden aangeschaft, worden ze direct opgeslagen in de Roblox-inventaris van de speler, waardoor spelers ze kunnen uitrusten en dragen in andere ervaringen.

Ervaringseigenaren die in-experience avatarcreatie implementeren, profiteren van [Marketplace commissies](/docs/nl-nl/marketplace/marketplace-fees-and-commissions#commissies)  als de uitgever  van het avataritem, terwijl de speler die het maakt de maker  van het item is. Als een asset die in-experience is gemaakt, wordt geïnspecteerd, biedt het item een link naar de oorspronkelijke ervaring waarin het is gemaakt.

Je kunt in-experience creatie testen in de [Avatar Creator](https://www.roblox.com/games/124012682058672/Roblox-Avatar-Creator)  demo van Roblox.

Avatar-assets die in-experience zijn gemaakt, worden niet vermeld op de Marketplace en kunnen niet worden doorverkocht of verhandeld.

## [Hoe in-experience creatie te implementeren](#hoe-in-experience-creatie-te-implementeren)[](#hoe-in-experience-creatie-te-implementeren)

Gebruik de volgende instructies en codeverwijzingen om je eerste in-experience avatarcreatieproject te maken. De volgende instructies gebruiken een basislichaam [Model](/docs/nl-nl/reference/engine/classes/Model)  dat spelers kunnen aanpassen en wijzigen voordat ze het publiceren.

Voordat je begint, maak jezelf vertrouwd met het volgende:

-

Avatar modellen — De volgende implementatie vereist het importeren van een basislichaam dat voldoet aan de 15-deel specificaties van Roblox. Dit [Model](/docs/nl-nl/reference/engine/classes/Model)  dient als basis voor aanvullende gebruikersaanpassing en -wijziging.

-

Het basislichaam moet voldoen aan de [Avatar lichaamsrichtlijnen](/docs/nl-nl/marketplace/marketplace-policy#richtlijnen-voor-avatarlichamen)  van Roblox, inclusief het minimum aantal FACS-controles voor gezichtsrigging.

-

[Avatar creatietokens](#genereer-een-avatar-creatietoken)  — Ervaringen die avatarcreatie implementeren, vereisen ten minste één creatietoken. Deze tokens vereisen Robux om aan te schaffen en stellen je in staat om prijzen en andere verkoopinstellingen voor aankopen in-experience in te stellen.

-

API-klassen

-

[AvatarCreationService](/docs/nl-nl/reference/engine/classes/AvatarCreationService)  — Behandelt het vragen om avatarcreatie en validatie.

-

[EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage)  — Behandelt runtime creatie en manipulatie van texturen.

-

[EditableMesh](/docs/nl-nl/reference/engine/classes/EditableMesh)  — Behandelt runtime manipulatie van mesh-geometrie.

-

[WrapDeformer](/docs/nl-nl/reference/engine/classes/WrapDeformer)  — Behandelt runtime manipulatie van onzichtbare buitenste kooi-geometrie die avatarpersonages in staat stelt om [3D-kleding](/docs/nl-nl/avatar/layered-accessories)  te dragen.

### [Importeer een basislichaam](#importeer-een-basislichaam)[](#importeer-een-basislichaam)

Het basislichaam fungeert als de initiële basis die gebruikers kunnen aanpassen en bewerken. Je kunt je eigen [Model](/docs/nl-nl/reference/engine/classes/Model)  gebruiken of een aangepast asset importeren met de [Importer](/docs/nl-nl/studio/importer)  en instellen via [Avatar Setup](/docs/nl-nl/avatar-setup) .

Basislichamen moeten voldoen aan de avatar specificaties van Roblox en moeten componenten bevatten zoals de 15 [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  instanties die 6 lichaamsdelen vormen: hoofd, torso, linkerarm, linkerbeen, rechterarm en rechterbeen, evenals andere [avatarcomponenten](/docs/nl-nl/avatar/character-bodies#componenten-van-het-lichaamsmodel) .

Als je een single-mesh lichaam hebt, kun je proberen de [Avatar Auto Setup](/docs/nl-nl/avatar-setup#avatar-auto-setup)  te gebruiken om automatisch alle benodigde avatarcomponenten toe te voegen.

Voor referenties en voorbeelden van goed geconfigureerde avatarlichamen, zie [Avatar referenties](/docs/nl-nl/avatar/resources#referenties) .

### [Implementeer bewerkings-API's](#implementeer-bewerkings-apis)[](#implementeer-bewerkings-apis)

Om een systeem te ontwikkelen waarin gebruikers de [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  instanties op een avatar in jouw ervaring kunnen bewerken voor creatie, gebruik [EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage)  voor textuurbewerking, [EditableMesh](/docs/nl-nl/reference/engine/classes/EditableMesh)  voor mesh-bewerking, en [WrapDeformer](/docs/nl-nl/reference/engine/classes/WrapDeformer)  voor het behouden van skinning en FACS-gegevens tijdens mesh-bewerkingen.

1.

Nadat je je basislichaam hebt geïmporteerd, gebruik je het volgende script om je [EditableImages](/docs/nl-nl/reference/engine/classes/EditableImage) , [EditableMeshes](/docs/nl-nl/reference/engine/classes/EditableMesh) , en [WrapDeformers](/docs/nl-nl/reference/engine/classes/WrapDeformer)  in te stellen.

```

local AssetService = game:GetService("AssetService")

local function setupBodyPart(meshPart, wrapTarget)

	-- Maak en koppel een WrapDeformer aan de MeshPart

	local wrapDeformer = Instance.new("WrapDeformer")

	wrapDeformer.Parent = meshPart

	-- Maak een bewerkbare mesh voor de kooi-mesh van het wrapdoel

	local cageEditableMesh: EditableMesh =

		AssetService:CreateEditableMeshAsync(Content.fromUri(wrapTarget.CageMeshId), {

			FixedSize = true,

		})

	-- Wijs de kooi-mesh toe aan de WrapDeformer

	wrapDeformer:SetCageMeshContent(Content.fromObject(cageEditableMesh))

end

local function setupRigidMesh(meshPart)

	-- Maak een bewerkbare mesh van de originele MeshPart

	local editableMesh = AssetService:CreateEditableMeshAsync(Content.fromUri(meshPart.MeshId), {

		FixedSize = true,

	})

	-- Genereer een nieuwe MeshPart van de bewerkbare mesh

	local newMeshPart = AssetService:CreateMeshPartAsync(Content.fromObject(editableMesh))

	-- Kopieer grootte, positie en textuur van de originele MeshPart

	newMeshPart.Size = meshPart.Size

	newMeshPart.CFrame = meshPart.CFrame

	newMeshPart.TextureContent = meshPart.TextureContent

	-- Pas de nieuwe MeshPart toe op de originele

	meshPart:ApplyMesh(newMeshPart)

end

local function setupMeshTexture(meshPart, textureIdToEditableImageMap)

	-- Als EditableImage al bestaat voor deze TextureID, hergebruik deze in plaats van een nieuwe te maken

	if textureIdToEditableImageMap[meshPart.TextureID] then

		meshPart.TextureContent =

			Content.fromObject(textureIdToEditableImageMap[meshPart.TextureID])

		return

	end

	-- Maak een nieuwe EditableImage en pas deze toe als de textuurinhoud

	local editableImage = AssetService:CreateEditableImageAsync(Content.fromUri(meshPart.TextureID))

	textureIdToEditableImageMap[meshPart.TextureID] = editableImage

	meshPart.TextureContent = Content.fromObject(editableImage)

end

local function setupModel(model)

	-- Kaart voor het hergebruiken van EditableImage-instanties op basis van textuur-ID

	local textureIdToEditableImageMap = {}

	for _, descendant in model:GetDescendants() do

		if not descendant:IsA("MeshPart") then

			continue

		end

		-- Configureer MeshPart op basis van de aanwezigheid van WrapTarget

		-- Als WrapTarget aanwezig is, voeg een WrapDeformer-kind toe met een EditableMesh

		-- Anders, pas EditableMesh direct toe op de MeshPart

		local wrapTarget = descendant:FindFirstChildOfClass("WrapTarget")

		if wrapTarget then

			setupBodyPart(descendant, wrapTarget)

		else

			setupRigidMesh(descendant)

		end

		-- Configureer de EditableImage voor de MeshPart

		setupMeshTexture(descendant, textureIdToEditableImageMap)

	end

end

```

2.

Maak [EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage)  tools waarmee spelers de kleur kunnen wijzigen, tekenen of stickers aan je basislichaam kunnen toevoegen. Je kunt API's gebruiken zoals [DrawImage()](/docs/nl-nl/reference/engine/classes/EditableImage#DrawImage) , [DrawRectangle()](/docs/nl-nl/reference/engine/classes/EditableImage#DrawRectangle) , [WritePixelsBuffer()](/docs/nl-nl/reference/engine/classes/EditableImage#WritePixelsBuffer) .

-

Voor geavanceerde transformaties, stelt [DrawImageTransformed()](/docs/nl-nl/reference/engine/classes/EditableImage#DrawImageTransformed)  je in staat om positie, rotatie en schaal op te geven bij het tekenen van de ene EditableImage op de andere. Evenzo werkt [DrawImageProjected()](/docs/nl-nl/reference/engine/classes/EditableImage#DrawImageProjected)  veel zoals [DrawImage()](/docs/nl-nl/reference/engine/classes/EditableImage#DrawImage) , maar projecteert de getekende afbeelding correct als de [EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage)  instantie wordt gebruikt met een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) .

```

local function recolorTexture(

	meshPart: MeshPart,

	color: Color3

)

	local bodyPartTexture = AssetService:CreateEditableImageAsync(meshPart.TextureID)

	meshPart.TextureContent = Content.fromObject(bodyPartTexture)

	bodyPartTexture:DrawRectangle(

		Vector2.new(0, 0),

		bodyPartTexture.Size,

		color,

		0,

		Enum.ImageCombineType.Overwrite

	)

end

local function applySticker(

	meshPart: MeshPart,

	textureCoordinate: Vector2,

	stickerId: TextureId

)

	local bodyPartTexture = AssetService:CreateEditableImageAsync(meshPart.TextureID)

	meshPart.TextureContent = Content.fromObject(bodyPartTexture)

	local stickerTexture = AssetService:CreateEditableImageAsync(stickerId)

	bodyPartTexture:DrawImage(textureCoordinate, stickerTexture, Enum.ImageCombineType.BlendSourceOver)

end

local function applyStickerProjected(

  meshPart: MeshPart,

  targetMesh: EditableMesh,

  stickerId: TextureId,

  raycastHitPos: Vector3

)

  local bodyPartTexture = AssetService:CreateEditableImageAsync(meshPart.TextureID)

  local relativePos = meshPart.CFrame:PointToWorldSpace(raycastHitPos)

  local direction = (workspace.CurrentCamera.CFrame.Position - relativePos).Unit

  local projectionParams: ProjectionParams = {

      Direction = meshPart.CFrame:VectorToObjectSpace(direction),

      Position = meshPart.CFrame:PointToObjectSpace(relativePos),

      Size = Vector3.new(1, 1, 1),

      Up = meshPart.CFrame:VectorToObjectSpace(Vector3.new(0, 1, 0)),

  }

  local stickerTexture = AssetService:CreateEditableImageAsync(stickerId)

  local localBrushConfig: BrushConfig = {

      Decal = stickerTexture,

      ColorBlendType = Enum.ImageCombineType.BlendSourceOver,

      AlphaBlendType = Enum.ImageAlphaType.Default,

      BlendIntensity = 1,

      FadeAngle = 90.0

  }

  bodyPartTexture:DrawImageProjected(targetMesh, projectionParams, localBrushConfig)

end

```

3.

Gebruik [WrapDeformer](/docs/nl-nl/reference/engine/classes/WrapDeformer)  en [EditableMesh](/docs/nl-nl/reference/engine/classes/EditableMesh)  om tools te maken voor het bewerken van mesh-deformaties op je lichaam.

1.

[WrapDeformer](/docs/nl-nl/reference/engine/classes/WrapDeformer)  behandelt de live deformaties van de weergegeven [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  geometrie terwijl de onderliggende skinning en FACS-gegevens behouden blijven.

2.

[EditableMesh](/docs/nl-nl/reference/engine/classes/EditableMesh)  stelt je in staat om de kooi-mesh te wijzigen waar de [WrapDeformer](/docs/nl-nl/reference/engine/classes/WrapDeformer)  op reageert.

1.

Gebruik [WrapDeformer:SetCageMeshContent()](/docs/nl-nl/reference/engine/classes/WrapDeformer#SetCageMeshContent)  om de [EditableMesh](/docs/nl-nl/reference/engine/classes/EditableMesh)  instantie die de relevante kooi-mesh vertegenwoordigt toe te passen op de [WrapDeformer](/docs/nl-nl/reference/engine/classes/WrapDeformer) .

2.

Gebruik [EditableMesh](/docs/nl-nl/reference/engine/classes/EditableMesh) , zoals [SetPosition()](/docs/nl-nl/reference/engine/classes/EditableMesh#SetPosition) , om de vertices te vervormen en de vorm van de [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  te bewerken.

```

local function deformBodyPart(

	meshPart: MeshPart,

	controlPointCenter: Vector3,

	controlPointRadius: number,

	controlPointDeformation: Vector3

)

	local wrapTarget = meshPart:FindFirstChildWhichIsA("WrapTarget")

	local cageMeshId = wrapTarget.CageMeshId

	local wrapDeformer = Instance.new("WrapDeformer")

	wrapDeformer.Parent = meshPart

	local cageEditableMesh = AssetService:CreateEditableMeshAsync(cageMeshId)

	local verticesWithinSphere =

		cageEditableMesh:FindVerticesWithinSphere(controlPointCenter, controlPointRadius)

	for _, vertexId in verticesWithinSphere do

		local vertexPosition = cageEditableMesh:GetPosition(vertexId)

		cageEditableMesh:SetPosition(vertexId, vertexPosition + controlPointDeformation)

	end

	wrapDeformer:SetCageMeshContent(Content.fromObject(cageEditableMesh))

end

```

### [Maak een creatieprompt](#maak-een-creatieprompt)[](#maak-een-creatieprompt)

Nadat je je basislichaam en bewerkings-API's hebt ingesteld, maak je een prompt voor gebruikers om te creëren en aan te schaffen vanuit de ervaring met [AvatarCreationService:PromptCreateAvatarAsync()](/docs/nl-nl/reference/engine/classes/AvatarCreationService#PromptCreateAvatarAsync) .

```

export type BodyPartInfo = {

	bodyPart: Enum.BodyPart,

	instance: Instance --Folder met gemaakte MeshParts

}

export type BodyPartList = {BodyPartInfo}

local function publishAvatar(bodyPartInstances: BodyPartList, player: Player, tokenId: string)

	local humanoidDescription = Instance.new("HumanoidDescription")

	for _, bodyPartInfo in bodyPartInstances do

		local bodyPartDescription = Instance.new("BodyPartDescription")

		bodyPartDescription.Instance = bodyPartInfo.instance

		bodyPartDescription.BodyPart = bodyPartInfo.bodyPart

		bodyPartDescription.Parent = humanoidDescription

	end

	local success, result, bundleIdOrErrorMessage, outfitId = pcall(function()

		return AvatarCreationService:PromptCreateAvatarAsync(tokenId, player, humanoidDescription)

	end)

	if success then

		if result == Enum.PromptCreateAvatarResult.Success then

			print("Succesvol geüpload met BundleId: ", bundleIdOrErrorMessage)

      print("Succesvol geüpload met OutfitId: ", outfitId)

		else

			print("Onsuccesvol geüpload met foutmelding:", bundleIdOrErrorMessage)

		end

	else

		print("Avatarcreatie niet succesvol")

	end

end

```

[AvatarCreationService:PromptCreateAvatarAsync()](/docs/nl-nl/reference/engine/classes/AvatarCreationService#PromptCreateAvatarAsync)  neemt een [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  parameter om de avatar voor aankoop of creatie weer te geven. Voor avatarcreatie moet de [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  van het personage nieuwe assets bevatten die voor elk van de 6 lichaamsdelen moeten worden gemaakt ([Head](/docs/nl-nl/reference/engine/enums/BodyPart#Head) , [Torso](/docs/nl-nl/reference/engine/enums/BodyPart#Torso) , [RightLeg](/docs/nl-nl/reference/engine/enums/BodyPart#RightLeg) , [LeftLeg](/docs/nl-nl/reference/engine/enums/BodyPart#LeftLeg) , [RightArm](/docs/nl-nl/reference/engine/enums/BodyPart#RightArm) , [LeftArm](/docs/nl-nl/reference/engine/enums/BodyPart#LeftArm) ). Optioneel kan het ook een nieuwe [Hair](/docs/nl-nl/reference/engine/enums/AccessoryType#Hair)  accessoire bevatten.

Om dit te ondersteunen, moet de [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  6 [BodyPartDescription](/docs/nl-nl/reference/engine/classes/BodyPartDescription)  kinderen bevatten. Elke [BodyPartDescription.Instance](/docs/nl-nl/reference/engine/classes/BodyPartDescription#Instance)  eigenschap verwijst naar een [Folder](/docs/nl-nl/reference/engine/classes/Folder)  die alle [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  instanties bevat die het lichaamsdeel vormen. Bijvoorbeeld, de LeftArm  map bevat LeftHand , LeftUpperArm , en LeftLowerArm  [MeshParts](/docs/nl-nl/reference/engine/classes/MeshPart) . De [BodyPartDescription.BodyPart](/docs/nl-nl/reference/engine/classes/BodyPartDescription#BodyPart)  eigenschap moet ook worden ingesteld op de relevante [Enum.BodyPart](/docs/nl-nl/reference/engine/enums/BodyPart) .

Elk van de 15 [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  lichaamsdelen moet bevatten:

-

Een [EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage) .

-

Een [WrapDeformer](/docs/nl-nl/reference/engine/classes/WrapDeformer)  met een [EditableMesh](/docs/nl-nl/reference/engine/classes/EditableMesh) .

De geleverde [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  mag geen bestaande asset-ID's bevatten om lichaamsdelen of accessoires op de bedoelde creatie weer te geven. Aan de andere kant kan de [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  de humanoïde schalen van [BodyTypeScale](/docs/nl-nl/reference/engine/classes/HumanoidDescription#BodyTypeScale) , [HeadScale](/docs/nl-nl/reference/engine/classes/HumanoidDescription#HeadScale) , [HeightScale](/docs/nl-nl/reference/engine/classes/HumanoidDescription#HeightScale) , [WidthScale](/docs/nl-nl/reference/engine/classes/HumanoidDescription#WidthScale) , en [ProportionScale](/docs/nl-nl/reference/engine/classes/HumanoidDescription#ProportionScale)  bevatten. Wees je bewust van de schalen waarmee een basislichaam is geïmporteerd, zodat ze overeenkomen met de schalen die aan de [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  zijn verstrekt.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-iec/Avatar-Creation-Format.png)

#### [Inclusief accessoires](#inclusief-accessoires)[](#inclusief-accessoires)

Als je een accessoire, zoals haar, wilt opnemen, moet de [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  een kind [AccessoryDescription](/docs/nl-nl/reference/engine/classes/AccessoryDescription)  bevatten waar:

-

De [AccessoryDescription.Instance](/docs/nl-nl/reference/engine/classes/AccessoryDescription#Instance)  eigenschap verwijst naar de [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  instantie.

-

De [AccessoryDescription.AccessoryType](/docs/nl-nl/reference/engine/classes/AccessoryDescription#AccessoryType)  eigenschap is ingesteld op de relevante [Enum.AccessoryType](/docs/nl-nl/reference/engine/enums/AccessoryType) .

-

In het geval van het opnemen van [Enum.AccessoryType.Hair](/docs/nl-nl/reference/engine/enums/AccessoryType#Hair)  in je creaties, moet de [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  een [EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage)  bevatten. Het mag echter geen [WrapDeformer](/docs/nl-nl/reference/engine/classes/WrapDeformer)  kind bevatten, maar moet een [EditableMesh](/docs/nl-nl/reference/engine/classes/EditableMesh)  bevatten die direct op de [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  is ingesteld.

### [Genereer een avatar creatietoken](#genereer-een-avatar-creatietoken)[](#genereer-een-avatar-creatietoken)

[AvatarCreationService:PromptCreateAvatarAsync()](/docs/nl-nl/reference/engine/classes/AvatarCreationService#PromptCreateAvatarAsync)  neemt een Avatar Creatie Token ID  parameter. Dit token is de sleutel voor creaties uit jouw universum, en het is wat je kunt gebruiken om de prijs van avatarcreatie vanuit jouw ervaring in te stellen. Voor instructies en aanvullende details over het genereren van tokens, zie [Avatar Creatie Tokens](/docs/nl-nl/production/monetization/avatar-creation-token) .

Na het kopen en genereren van je token, kun je het token inspecteren in de Creator Hub om de ID te vinden die je vervolgens kunt gebruiken voor de [AvatarCreationService:PromptCreateAvatarAsync()](/docs/nl-nl/reference/engine/classes/AvatarCreationService#PromptCreateAvatarAsync)  API.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-iec/Avatar-Token-Id.png)

## [Reageer op spelers die zich aanmelden via attributie](#reageer-op-spelers-die-zich-aanmelden-via-attributie)[](#reageer-op-spelers-die-zich-aanmelden-via-attributie)

Avatarbundels die in-experience zijn gemaakt, bevatten een attributielink naar de oorspronkelijke ervaring waarin de avatar is gemaakt. Als de avatar door een andere speler wordt geïnspecteerd, verschijnt er een prompt met de optie om de ervaring te bezoeken waar de avatar is gemaakt.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-iec/Avatar-Creation-Attribution.png)

Om spelers die zich aanmelden bij jouw ervaring via deze attributielink te verwerken, gebruik je [Player:GetJoinData()](/docs/nl-nl/reference/engine/classes/Player#GetJoinData)  en parse je de geretourneerde tabel voor GameJoinContext .

GameJoinContext  bevat de volgende tabelwaarden:

-

JoinSource  — [Enum.JoinSource](/docs/nl-nl/reference/engine/enums/JoinSource)

-

Een [Player](/docs/nl-nl/reference/engine/classes/Player)  die zich aanmeldt bij jouw ervaring via deze attributielink zal [Enum.JoinSource.CreatedItemAttribution](/docs/nl-nl/reference/engine/enums/JoinSource#CreatedItemAttribution)  hebben om aan te geven dat de toegang afkomstig is van een gemaakt item.

-

ItemType  — optionele [Enum.AvatarItemType](/docs/nl-nl/reference/engine/enums/AvatarItemType)

-

AssetId  — optionele string

-

OutfitId  — optionele string

-

AssetType  — optionele [Enum.AssetType](/docs/nl-nl/reference/engine/enums/AssetType)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
