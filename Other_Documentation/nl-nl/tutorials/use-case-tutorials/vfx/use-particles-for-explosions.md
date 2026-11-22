<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/vfx/use-particles-for-explosions -->

Creëer explosies met VFX | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. VFX

# Creëer explosies met VFX

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Eerder heb je gewerkt met deeltjes die continu afspeelden, zoals [rook van een vulkaan](/docs/nl-nl/tutorials/use-case-tutorials/vfx/custom-particle-effects) . Deeltjes kunnen ook in een enkele explosie worden gebruikt, zoals explosies. Deze tutorial laat je zien hoe je een valstrik kunt maken die een explosie van deeltjes afgeeft en een speler doodt.

## [Emitter-instelling](#emitter-instelling)[](#emitter-instelling)

De explosie zal een ParticleEmitter gebruiken met enkele gewijzigde eigenschappen die een explosie creëren.

1.

Ontwerp een gevaarlijk uitziende valstrik. Voeg vervolgens een ParticleEmitter  met de naam Explosion  toe aan het onderdeel.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/using-particles-for-explosions/burstParticles_partExample.png)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/using-particles-for-explosions/burstParticles_createExplosion.png)

2.

Maak een elektrisch vonk-effect met behulp van deze eigenschappen.

| Eigenschap | | Waarde | | Beschrijving |
| --- | --- |
| ** Textuur** | | rbxassetid://6101261905 | | Elektrische vonk textuur. |
| ** Wrijving** | | 10 | | Hoe snel de deeltjes snelheid verliezen. |
| ** Levensduur** | | 0.2, 0.6 | | Maakt explosiedeeltjes voor een korte tijd zichtbaar. |
| ** Snelheid** | | 20, 40 | | Compenseert voor de korte levensduur. |
| ** Verspreidingshoek** | | 180, 180 | | Vuur deeltjes in alle richtingen af. |

3.

Zorg ervoor dat de valstrik geen deeltjes constant afgeeft door Ingeschakeld  op uit  te zetten.

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/using-particles-for-explosions/burstParticles_toggleEnabled.png)

## [Test deeltjesexplosies](#test-deeltjesexplosies)[](#test-deeltjesexplosies)

Om de deeltjesexplosie te testen, kun je een Studio-plugin gebruiken die door Roblox is ontwikkeld.

1.

Ga naar de Marketplace-pagina voor de [Emit() Plugin](https://www.roblox.com/library/303835976/ParticleEmitter-Emit-n)  Plugin. Klik op die pagina op de knop Installeren .

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/using-particles-for-explosions/burstParticles_pluginInstall.png)

2.

Wanneer Studio opent, zou de plugin automatisch moeten installeren.

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/using-particles-for-explosions/burstParticles_confirmPluginInstall.png)

3.

Selecteer de Explosion  emitter en let op de plugin UI die verschijnt in de linkerbovenhoek van het 3D-venster. Typ in het nummervak 100  (het aantal deeltjes dat moet worden afgegeven) en druk op Enter .

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/using-particles-for-explosions/burstParticles_enterEmitRate.png)

4.

Druk op de knop Afgeven  om de emitter te testen.

## [Kleur en transparantie](#kleur-en-transparantie)[](#kleur-en-transparantie)

Enkele extra stappen kunnen de explosie indrukwekkender maken.

1.

Open het sequentievenster voor de Kleur  van de emitter door op de drie stippen naast de eigenschap te klikken. Maak vervolgens sleutelpunten in het venster om een kleurverloop te maken.

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/using-particles-for-explosions/burstParticles_colorSequence.png)

2.

Voor Transparantie , gebruik een nummerreeks  die de transparantie over een vloeiende curve verhoogt om een geleidelijke vervaging te tonen.

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/using-particles-for-explosions/burstParticles_transparencyGradient.png)

Een voltooide deeltjeseffect kan er als volgt uitzien.

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/using-particles-for-explosions/burstParticles_transparencyGradientExample.jpg)

## [Script-instelling](#script-instelling)[](#script-instelling)

Met de emitter compleet, kan de explosie nu via een script worden afgespeeld. Het script werkt door te controleren of spelers de valstrik aanraken. Wanneer het iemand detecteert, worden de deeltjes afgegeven en zal de speler sterven.

1.

Voeg in het valstrikonderdeel een nieuw Script  toe met de naam PlayExplosion .

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/using-particles-for-explosions/burstParticles_explorerCreateScript.png)

2.

Stel variabelen in om het onderdeel en de emitter op te slaan. Voeg vervolgens een variabele genaamd EMIT_AMOUNT  toe die het aantal deeltjes opslaat dat per explosie wordt afgegeven.

```

local trapObject = script.Parent

local particleEmitter = trapObject.Explosion

local EMIT_AMOUNT = 100

```

3.

Codeer een gebeurtenis om te controleren of een [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  het onderdeel aanraakt. Als dat zo is, stel dan de gezondheid van die humanoïde in op 0, waardoor ze gedwongen worden om opnieuw te spawnen.

```

local trapObject = script.Parent

local particleEmitter = trapObject.Explosion

local EMIT_AMOUNT = 100

local function killPlayer(otherPart)

	local character = otherPart.Parent

	local humanoid = character:FindFirstChildWhichIsA("Humanoid")

	if humanoid then

		humanoid.Health = 0

	end

end

trapObject.Touched:Connect(killPlayer)

```

## [Speel de explosie af](#speel-de-explosie-af)[](#speel-de-explosie-af)

In scripts worden deeltjes afgegeven met de [Emit()](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Emit)  functie. Dit creëert een eenmalige explosie van een aantal deeltjes.

1.

Roep de Emit()  functie aan en geef EMIT_AMOUNT  door, de eerder gemaakte variabele.

```

local trapObject = script.Parent

local particleEmitter = trapObject.Explosion

local EMIT_AMOUNT = 100

local function killPlayer(otherPart)

	local character = otherPart.Parent

	local humanoid = character:FindFirstChildWhichIsA("Humanoid")

	if humanoid then

		humanoid.Health = 0

		particleEmitter:Emit(EMIT_AMOUNT)

	end

end

trapObject.Touched:Connect(killPlayer)

```

2.

Test het script door in de valstrik te lopen.

Met slechts een paar wijzigingen aan het voorbeeld in deze tutorial, kun je een verscheidenheid aan verschillende effecten creëren. Enkele alternatieven zijn sprankels voor het verzamelen van verzamelobjecten, of explosies om de impact van een projectiel aan te geven.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
