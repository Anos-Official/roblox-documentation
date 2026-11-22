<!-- Source: https://create.roblox.com/docs/nl-nl/characters/appearance -->

Uiterlijk van het personage | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Personages](/docs/nl-nl/characters)

# Uiterlijk van het personage

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De meeste spellen laten spelers hun eigen Roblox-avatar gebruiken, hoewel sommige een aanpassingssysteem in het spel implementeren, zoals de [UGC Homestore](/docs/nl-nl/resources/templates#ugc-homestore)  sjabloon. Andere spellen maken beperkte [wijzigingen](/docs/nl-nl/characters/appearance)  aan spelersavatars, zoals helmen, vleugels of accessoires die passen bij het genre.

Om een uniek spel te creëren dat het uiterlijk van je gebruikers verandert, kun je de standaard karaktereigenschappen aanpassen via [avatarinstellingen](#globale-avatarinstellingen)  of een [handmatig aangepast uiterlijk](#handmatig-aangepast-uiterlijk) .

## [Globale avatarinstellingen](#globale-avatarinstellingen)[](#globale-avatarinstellingen)

De Bestand  ⟩ Avatarinstellingen  van Studio stelt je in staat om snel verschillende globale eigenschappen van spelerspersonages in je spel in te stellen. Deze instellingen zijn globaal van toepassing op alle spelersmodelen die je spel betreden. Om specifieke personages te wijzigen, zoals niet-speler personagemodellen, zie [handmatig aangepast uiterlijk](#handmatig-aangepast-uiterlijk) .

In dit venster kun je verschillende presets instellen voor kleding, accessoires, lichaamsdelen, botsingsgedrag, animaties en meer. Wanneer je deze instellingen bewerkt, wordt een voorbeeld van de toegepaste instellingen weergegeven in de werkruimte.

Voor meer informatie, zie [Avatarinstellingen](/docs/nl-nl/studio/avatar-settings) .

## [Handmatig aangepast uiterlijk](#handmatig-aangepast-uiterlijk)[](#handmatig-aangepast-uiterlijk)

Karaktermodellen bevatten een [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  object dat het model speciale kenmerken geeft, zoals lopen, springen, items uitrusten en interactie met de omgeving.

Je kunt een [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  programmatisch aanpassen door [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  bij te werken. Dit omvat spelersmodellen of niet-speler personagemodellen in je spel.

Je kunt de volgende karaktereigenschappen in je spel aanpassen met [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription) :

| Karaktereigenschap | | Beschrijving |
| --- | --- |
| Schaal | | Numerieke waarden voor fysieke eigenschappen [hoogte](/docs/nl-nl/reference/engine/classes/HumanoidDescription#HeightScale) , [breedte](/docs/nl-nl/reference/engine/classes/HumanoidDescription#WidthScale) , [hoofd](/docs/nl-nl/reference/engine/classes/HumanoidDescription#HeadScale) , [lichaamstype](/docs/nl-nl/reference/engine/classes/HumanoidDescription#BodyTypeScale)  en [proportie](/docs/nl-nl/reference/engine/classes/HumanoidDescription#ProportionScale) . Dit heeft geen invloed op R6-lichaamstypes. |
| Accessoires | | De asset-ID's van [accessoires](/docs/nl-nl/reference/engine/classes/Accessory)  die door een karakter zijn uitgerust. |
| Classic Kleding | | De asset-ID's van de [Shirt](/docs/nl-nl/reference/engine/classes/Shirt) , [Pants](/docs/nl-nl/reference/engine/classes/Pants)  en [ShirtGraphic](/docs/nl-nl/reference/engine/classes/ShirtGraphic)  afbeeldings-texturen die je op het karakter kunt toepassen. |
| Lichaamsdeel | | De asset-ID's van de [Gezicht](/docs/nl-nl/reference/engine/classes/HumanoidDescription#Face) , [Hoofd](/docs/nl-nl/reference/engine/classes/HumanoidDescription#Head) , [Torso](/docs/nl-nl/reference/engine/classes/HumanoidDescription#Torso) , [RechterArm](/docs/nl-nl/reference/engine/classes/HumanoidDescription#RightArm) , [LinkerArm](/docs/nl-nl/reference/engine/classes/HumanoidDescription#LeftArm) , [RechterBeen](/docs/nl-nl/reference/engine/classes/HumanoidDescription#RightLeg)  en [LinkerBeen](/docs/nl-nl/reference/engine/classes/HumanoidDescription#LeftLeg)  delen van een karakter. |
| Lichaamskleuren | | De [BodyColors](/docs/nl-nl/reference/engine/classes/BodyColors)  van de individuele delen van het karakter. |
| Animaties | | De asset-ID's van [Animaties](/docs/nl-nl/reference/engine/classes/Animation)  die je op een karakter kunt gebruiken. |

Pas een karakter aan met [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  met de volgende stappen:

1.

[Maak een beschrijving](#maak-humanoiddescription)  van het karakter van de gebruiker, een specifieke Outfit-ID of van een specifieke Gebruikers-ID.

2.

[Wijzig de beschrijving](#wijzig-humanoiddescription)  om de eigenschappen aan te passen die je wilt toepassen op het [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  karakter.

3.

[Pas de beschrijving toe](#pas-humanoiddescription-toe)  op een enkel karakter, alle spelerspersonages of zelfs op alle spawende personages.

Bij het bijwerken van de eigenschappen van een karakter via [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  is het belangrijk om een actuele [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  van dat specifieke [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  te gebruiken met [Humanoid:GetAppliedDescription()](/docs/nl-nl/reference/engine/classes/Humanoid#GetAppliedDescription) .

### [Maak HumanoidDescription](#maak-humanoiddescription)[](#maak-humanoiddescription)

Je kunt een nieuwe [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  instantie direct binnen de Explorer  hiërarchie of binnen een [Script](/docs/nl-nl/reference/engine/classes/Script)  maken met de volgende code:

Maak een nieuwe HumanoidDescription instantie

```

local humanoidDescription = Instance.new("HumanoidDescription")

```

In de meeste gevallen moet je een bestaande [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  gebruiken in plaats van een standaard nieuwe [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  door te verwijzen naar een bestaand spelerskarakter, avataroutfit of gebruikers-ID.

####  Van het spelerskarakter

Gebruik het volgende codevoorbeeld om een nieuwe [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  te maken op basis van de huidige eigenschappen van het spelerskarakter:

Genereer een HumanoidDescription van een spelerskarakter

```

local humanoid = player.Character and player.Character:FindFirstChildWhichIsA("Humanoid")

local humanoidDescription = Instance.new("HumanoidDescription")

if humanoid then

	humanoidDescription = humanoid:GetAppliedDescription()

end

```

####  Van een bestaande outfit

Gebruik de volgende voorbeeldcode om een [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  te maken van een outfit-ID met [Players.GetHumanoidDescriptionFromOutfitID](/docs/nl-nl/reference/engine/classes/Players#GetHumanoidDescriptionFromOutfitId) :

Genereer een HumanoidDescription van een Outfit-ID

```

local Players = game:GetService("Players")

local outfitId = 480059254

local humanoidDescriptionFromOutfit = Players:GetHumanoidDescriptionFromOutfitId(outfitId)

```

####  Van een specifieke gebruiker

Gebruik de volgende voorbeeldcode om een [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  te maken van een gebruikers-ID met [Players:GetHumanoidDescriptionFromUserId()](/docs/nl-nl/reference/engine/classes/Players#GetHumanoidDescriptionFromUserId) :

Genereer een HumanoidDescription van een gebruikers-ID

```

local Players = game:GetService("Players")

local userId = 491243243

local humanoidDescriptionFromUser = Players:GetHumanoidDescriptionFromUserId(userId)

```

### [Wijzig HumanoidDescription](#wijzig-humanoiddescription)[](#wijzig-humanoiddescription)

Om [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  eigenschappen aan te passen, stel je ze direct in op de [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  of gebruik je een specifieke methode voordat je de [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  op een karakter toepast.

Het volgende codevoorbeeld geeft voorbeelden van het instellen van de verschillende soorten [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  eigenschappen:

Werk verschillende HumanoidDescription eigenschappen bij

```

local humanoidDescription = Instance.new("HumanoidDescription")

humanoidDescription.HatAccessory = "2551510151,2535600138"

humanoidDescription.BodyTypeScale = 0.1

humanoidDescription.ClimbAnimation = 619521311

humanoidDescription.Face = 86487700

humanoidDescription.GraphicTShirt = 1711661

humanoidDescription.HeadColor = Color3.new(0, 1, 0)

```

####  Stel meerdere accessoires in

Voor gelaagde of bulkaccessoirewijzigingen kun je [HumanoidDescription:SetAccessories()](/docs/nl-nl/reference/engine/classes/HumanoidDescription#SetAccessories)  gebruiken om accessoires gerelateerde updates te maken. Het volgende codevoorbeeld voegt een gelaagde trui en jas in die volgorde toe aan een [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription) :

Verander meerdere accessoires tegelijk

```

local humanoidDescription = Instance.new("HumanoidDescription")

local accessoryTable = {

	{

		Order = 1,

		AssetId = 6984769289,

		AccessoryType = Enum.AccessoryType.Sweater

	},

	{

		Order = 2,

		AssetId = 6984767443,

		AccessoryType = Enum.AccessoryType.Jacket

	}

}

humanoidDescription:SetAccessories(accessoryTable, false)

```

### [Pas HumanoidDescription toe](#pas-humanoiddescription-toe)[](#pas-humanoiddescription-toe)

Pas [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  toe op specifieke [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  personages in je spel met [Humanoid:ApplyDescription()](/docs/nl-nl/reference/engine/classes/Humanoid#ApplyDescription)  of [Humanoid.LoadCharacterWithHumanoidDescription](/docs/nl-nl/reference/engine/classes/Player#LoadCharacterWithHumanoidDescription) .

Het wijzigen van de assets op een karakter terwijl je ook [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  wijzigt, kan leiden tot ongedefinieerd gedrag.

####  Op een enkel karakter

[ApplyDescription()](/docs/nl-nl/reference/engine/classes/Humanoid#ApplyDescription)  kan elk [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  targeten. Gebruik de volgende code om een nieuw paar zonnebrillen en een nieuwe torso aan het spelerskarakter toe te voegen:

Werk HumanoidDescription bij voor een specifiek spelerskarakter

```

local humanoid = player.Character and player.Character:FindFirstChildWhichIsA("Humanoid")

if humanoid then

	local descriptionClone = humanoid:GetAppliedDescription()

	descriptionClone.Torso = 86500008

	-- Meerdere gezichtaccessoire-assets zijn toegestaan in een door komma's gescheiden string

	descriptionClone.FaceAccessory = descriptionClone.FaceAccessory .. ",2535420239"

	-- Pas de gewijzigde "descriptionClone" toe op humanoid

	humanoid:ApplyDescription(descriptionClone)

end

```

####  Op alle spelerspersonages

Gebruik de volgende voorbeeldcode om een [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  toe te passen op alle huidige spelers in het spel:

Werk HumanoidDescription bij voor alle huidige spelerspersonages

```

local Players = game:GetService("Players")

for _, player in Players:GetPlayers() do

	local humanoid = player.Character and player.Character:FindFirstChildWhichIsA("Humanoid")

	if humanoid then

		-- Maak een HumanoidDescription

		local humanoidDescription = Instance.new("HumanoidDescription")

		humanoidDescription.HatAccessory = "2551510151,2535600138"

		humanoidDescription.BodyTypeScale = 0.1

		humanoidDescription.ClimbAnimation = 619521311

		humanoidDescription.Face = 86487700

		humanoidDescription.GraphicTShirt = 1711661

		humanoidDescription.HeadColor = Color3.new(0, 1, 0)

		humanoid:ApplyDescription(humanoidDescription)

	end

end

```

####  Op alle spawende personages

Gebruik de volgende voorbeeldcode om een specifieke [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  in te stellen voor alle spawende spelerspersonages:

Werk HumanoidDescription bij voor alle spawende personages

```

local Players = game:GetService("Players")

-- Stop automatische spawning zodat het kan worden gedaan in de "PlayerAdded" callback

Players.CharacterAutoLoads = false

local function onPlayerAdded(player)

	-- Maak een HumanoidDescription

	local humanoidDescription = Instance.new("HumanoidDescription")

	humanoidDescription.HatAccessory = "2551510151,2535600138"

	humanoidDescription.BodyTypeScale = 0.1

	humanoidDescription.ClimbAnimation = 619521311

	humanoidDescription.Face = 86487700

	humanoidDescription.GraphicTShirt = 1711661

	humanoidDescription.HeadColor = Color3.new(0, 1, 0)

	-- Spawn karakter met de HumanoidDescription

	player:LoadCharacterWithHumanoidDescription(humanoidDescription)

end

-- Verbind de "PlayerAdded" gebeurtenis met de "onPlayerAdded()" functie

Players.PlayerAdded:Connect(onPlayerAdded)

```

Als de [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  instantie in de Explorer  is gemaakt en aan de werkruimte is gekoppeld, gebruik dan de volgende voorbeeldcode in een [Script](/docs/nl-nl/reference/engine/classes/Script)  om toegang te krijgen tot de werkruimte-instantie:

```

local Players = game:GetService("Players")

-- Stop automatische spawning zodat het kan worden gedaan in de "PlayerAdded" callback

Players.CharacterAutoLoads = false

local function onPlayerAdded(player)

	-- Spawn karakter met "workspace.StudioHumanoidDescription"

	player:LoadCharacterWithHumanoidDescription(workspace.StudioHumanoidDescription)

end

-- Verbind de "PlayerAdded" gebeurtenis met de "onPlayerAdded()" functie

Players.PlayerAdded:Connect(onPlayerAdded)

```

## [Gelaagde accessoires op niet-R15](#gelaagde-accessoires-op-niet-r15)[](#gelaagde-accessoires-op-niet-r15)

Gecage accessoires, zoals gelaagde accessoires, gebruiken [WrapTarget](/docs/nl-nl/reference/engine/classes/WrapTarget)  en [WrapLayer](/docs/nl-nl/reference/engine/classes/WrapLayer)  om uit te rekken en over een doel [Model](/docs/nl-nl/reference/engine/classes/Model)  te wikkelen. Gelaagde accessoires kunnen werken met zowel standaard [spelerspersonages](/docs/nl-nl/characters#speler-personages)  als niet-R15 modellen.

Aangepaste implementatie van gelaagde accessoires, zoals een model dat een unieke cage UV-kaart gebruikt, kan niet worden geüpload en gepubliceerd naar de Marketplace. Je kunt echter [aangepaste cage-meshes](/docs/nl-nl/art/modeling/cage-meshes)  maken voor in-game assets zoals gebouwen, spel-specifieke kleding en props.

Of je nu gelaagde accessoires implementeert op een [R15 rigging armature](/docs/nl-nl/avatar/character-bodies/specifications#rigging) , of een aangepaste rig gebruikt, zorg ervoor dat je accessoires en lichamen de volgende bevatten:

-

Het doelmodel, meestal het lichaam, heeft een [WrapTarget](/docs/nl-nl/reference/engine/classes/WrapTarget)  component op de meshes waarover aanvullende modellen bedoeld zijn om te wikkelen.

-

Het layeringmodel, meestal de kleding of accessoire, heeft een [WrapLayer](/docs/nl-nl/reference/engine/classes/WrapLayer)  component op de meshes die bedoeld zijn om het doelmodel te wikkelen.

-

De buitenste cage van het doelmodel , en de binnenste en buitenste cage van het layeringmodel  hebben overeenkomende UV-kaarten.

-

De overeenkomstige vertices op de doelcage moeten dezelfde UV's hebben als die vertices op de layer cage.

-

Als je doelmodel geen R15 is, of geen [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  bevat, moet je een [Weld](/docs/nl-nl/reference/engine/classes/Weld)  object aan de layering [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  toevoegen.

-

De [Weld](/docs/nl-nl/reference/engine/classes/Weld)  moet Part0  en Part1  hebben ingesteld om de layering MeshPart te koppelen aan de Part-hiërarchie van het Model. Bijvoorbeeld, Part0  verwijst naar de accessoire en Part1  verwijst naar de bovenliggende Part.

-

Als je doelmodel zowel R15 is als een [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  bevat, wordt deze las automatisch gemaakt.

Zie de volgende bronnen voor aanvullende informatie over gelaagde accessoires en caging:

-

[Overzicht van gelaagde accessoires caging](/docs/nl-nl/avatar/layered-accessories#cage-meshes)

-

[Best practices voor gelaagde accessoires caging](/docs/nl-nl/avatar/layered-accessories/caging-best-practices)

-

[Specificaties voor gelaagde accessoires cage mesh](/docs/nl-nl/avatar/layered-accessories/specifications#cage-meshes)

-

[Specificaties voor avatar body cage](/docs/nl-nl/avatar/character-bodies/specifications#buitenste-kooien)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
