<!-- Source: https://create.roblox.com/docs/nl-nl/physics/constraints/ball-socket -->

BalSocket | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)
6. /
7. [Fysica](/docs/nl-nl/physics)
8. /
9. [Mechanische beperkingen](/docs/nl-nl/physics/mechanical-constraints)

# BalSocket

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Voor een overzicht van het maken, visualiseren en simuleren van mechanische beperkingen, inclusief Class.BalSocketConstraint , zie [Mechanische beperkingen](/docs/nl-nl/physics/mechanical-constraints) . Zie ook [Roblox eenheden](/docs/nl-nl/physics/units)  om te begrijpen hoe Roblox-eenheden zich verhouden tot metrische eenheden.

Een Class.BalSocketConstraint  dwingt zijn twee bevestigingen in dezelfde positie en staat ze toe vrij te draaien om alle drie de assen. U kunt echter limieten inschakelen om zowel kanteling als draaiing te beperken.

## [Limieten](#limieten)[](#limieten)

U kunt limieten instellen om zowel kanteling  als draaiing  van een bal socket te beperken, vergelijkbaar met hoe het hoofd van een mens kan kantelen en draaien binnen een beperkte axiale range. Het inschakelen van de Class.BalSocketConstraint.LimitsEnabled|LimitsEnabled  eigenschap maakt de Class.BalSocketConstraint.UpperAngle|UpperAngle  waarde toegankelijk om kanteling  binnen een kegel te beperken; het maakt ook de Class.BalSocketConstraint.TwistLimitsEnabled|TwistLimitsEnabled  eigenschap toegankelijk die, wanneer ingeschakeld, u toestaat draaiing  rotatie te beperken via de Class.BalSocketConstraint.TwistLowerAngle|TwistLowerAngle  en Class.BalSocketConstraint.TwistUpperAngle|TwistUpperAngle  limieten.

Beperking met Class.BalSocketConstraint.LimitsEnabled|LimitsEnabled  ingesteld op true  en Class.BalSocketConstraint.UpperAngle|UpperAngle  ingesteld op 15

Beperking met Class.BalSocketConstraint.LimitsEnabled|LimitsEnabled  en Class.BalSocketConstraint.TwistLimitsEnabled|TwistLimitsEnabled  ingesteld op true , Class.BalSocketConstraint.TwistLowerAngle|TwistLowerAngle  ingesteld op -60 , en Class.BalSocketConstraint.TwistUpperAngle|TwistUpperAngle  ingesteld op 0

Het inschakelen van Class.BalSocketConstraint.LimitsEnabled|LimitsEnabled  maakt ook de Class.BalSocketConstraint.Restitution|Restitution  waarde toegankelijk die de elasticiteit van de bevestigingen bij hun kantel- en/of draaiingslimieten definieert.

Wanneer Class.BalSocketConstraint.LimitsEnabled|LimitsEnabled  is ingeschakeld, beïnvloedt de oriëntatie van de bevestigingen van een bal socket hoe deze draait. Om ervoor te zorgen dat de rotatie plaatsvindt rond de gewenste as, moet de [Axis](/docs/nl-nl/reference/engine/classes/Attachment#Axis)  van elke bevestiging, weergegeven door de gele pijl, in dezelfde richting wijzen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
