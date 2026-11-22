<!-- Source: https://create.roblox.com/docs/nl-nl/physics/constraints/angular-velocity -->

HoekSnelheid | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)
6. /
7. [Fysica](/docs/nl-nl/physics)
8. /
9. [Beperkingen van verplaatser](/docs/nl-nl/physics/mover-constraints)

# HoekSnelheid

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Voor een overzicht van het maken, visualiseren en simuleren van mover-beperkingen, inclusief Class.HoekSnelheid , zie [mover-beperkingen](/docs/nl-nl/physics/mover-constraints) . Zie ook [Roblox eenheden](/docs/nl-nl/physics/units)  om te begrijpen hoe Roblox-eenheden zich verhouden tot metrische eenheden.

Een Class.HoekSnelheid  beperking past koppel toe op een assemblage om een constante hoeksnelheid te behouden.

De Class.HoekSnelheid  beperking past koppel toe dat probeert een constante  hoeksnelheid te behouden. Als je de hoeveelheid koppel die wordt toegepast wilt regelen, gebruik dan een [Koppel](/docs/nl-nl/physics/constraints/torque)  beperking. Als je alleen initiële  hoeksnelheid nodig hebt, stel dan de [AssemblyAngularVelocity](/docs/nl-nl/reference/engine/classes/BasePart#AssemblyAngularVelocity)  methode direct in op de assemblage.

## [Relativiteit](#relativiteit)[](#relativiteit)

Toepassing van snelheid kan worden gecontroleerd via de Class.HoekSnelheid.RelativeTo|RelativeTo  eigenschap van de beperking. Als deze is ingesteld op [World](/docs/nl-nl/reference/engine/enums/ActuatorRelativeTo) , wordt de hoeksnelheidsvector gebruikt zoals deze is. Als deze is ingesteld op [Attachment1](/docs/nl-nl/reference/engine/enums/ActuatorRelativeTo)  en de [Attachment1](/docs/nl-nl/reference/engine/classes/Constraint#Attachment1)  eigenschap van de beperking is ingesteld op een andere attachment, zal de hoeksnelheid worden beïnvloed door die van de andere attachment, zoals te zien is aan hoe de snelheid van het bovenste rode deel de snelheid van het bevestigde blauwe deel beïnvloedt.

RelativeTo = Wereld

RelativeTo = Attachment1

Het instellen van Class.HoekSnelheid.RelativeTo|RelativeTo  op [Attachment1](/docs/nl-nl/reference/engine/enums/ActuatorRelativeTo)  maakt ook de Class.HoekSnelheid.ReactionTorqueEnabled|ReactionTorqueEnabled  eigenschap toegankelijk.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
