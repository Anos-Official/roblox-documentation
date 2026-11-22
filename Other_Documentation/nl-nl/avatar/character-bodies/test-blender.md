<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/character-bodies/test-blender -->

Blender-tests voor karakterlichamen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Lichamen
6. /
7. Test bodies

# Blender-tests voor karakterlichamen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het is belangrijk om je karakterlichamen periodiek in Blender te testen, zodat je problemen kunt opmerken voordat ze grotere problemen worden wanneer je je karakters in Studio importeert. Terwijl je verschillende karaktercomponenten iteratief ontwikkelt, voer je de volgende Blender-tests regelmatig uit en bekijk je eventuele zorgpunten.

## [Technische specificaties](#technische-specificaties)[](#technische-specificaties)

Je karakterlichaamscomponenten voor je avatar moeten voldoen aan de vereisten in Roblox's [specificaties voor karakterlichamen](/docs/nl-nl/avatar/character-bodies/specifications) . Bij het gebruik van sjablonen en het volgen van geschikte niet-destructieve modelleerpraktijken, zouden de meeste van deze componenten niet aangeraakt moeten worden, maar je moet nog steeds dubbel controleren of elk component voldoet aan de technische vereisten voordat je je werk in Studio importeert, inclusief maar niet beperkt tot:

-

Vereisten voor lichaamsgrootte

-

Driehoekbudgetten

-

Naamgeving en zichtbaarheid van lichaamsdelen

-

Rigging- en skinninggegevens

-

Naamgeving en positionering van bevestigingen

-

Naamgeving en positionering van de buitenste kooi

## [Gegevens voor gezichtsanimatie](#gegevens-voor-gezichtsanimatie)[](#gegevens-voor-gezichtsanimatie)

Gezichtsanimatie maakt gebruik van meerdere modelleercomponenten om effectief te werken. Als je een [sjabloon](/docs/nl-nl/avatar/resources#sjablonen)  gebruikt of anderszins wijzigingen aanbrengt in een model met bestaande gezichtsanimatiegegevens, is het mogelijk om per ongeluk een update te maken die de opgeslagen poses beïnvloedt, hetzij in de animatietijdlijn of in de aangepaste eigenschappen van het Head_Geo -mesh van je karakter.

De volgende stappen kunnen je helpen de integriteit van je gezichtsanimatiegegevens te verifiëren:

1.

Met het Armature -object geselecteerd, bekijk je je animatieframes in de tijdlijn :

-

De tijdlijn loopt meestal van 0 – 330 , hoewel niet alle sjablonen het volledige bereik gebruiken en er mogelijk gaten zijn tussen poses.

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Testing-Animation-Timeline.png)

-

Controleer of de neutrale pose  van het karakter op frame 0  staat.

-

Verwijder eventuele keyframe-gaten tussen de frames met animatiegegevens.

2.

Bekijk het paneel Objecteigenschappen  > Aangepaste eigenschappen  voor het Head_Geo -object:

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Testing-Custom-Properties.png)

-

Controleer of de RootFaceJoint -attribuut is ingesteld op de naam van het eerste gezichtsanimatiebot.

-

Zorg ervoor dat dit bot een kind is van het Hoofd -bot, een van de [15 vereiste botten](/docs/nl-nl/avatar/character-bodies/specifications#rigging)  in de rigging-armatuur van een avatar.

-

In sjablonen en sommige referentiemodellen wordt dit bot vaak DynamicHead  genoemd, en het geeft het begin van de gezichtsanimatierig aan.

-

Controleer of er hetzelfde aantal aangepaste eigenschappen is als unieke animatieframes, waarbij elke animatiepose zijn eigen toegewezen aangepaste eigenschap heeft.

-

Controleer of de namen voor de toegewezen poses hier overeenkomen met de spelling en hoofdlettergebruik van de [FACS-pose referentie](/docs/nl-nl/avatar/dynamic-heads/facs-poses-reference) .

Als je problemen ontdekt met je gezichtsanimatiegegevens, moet je mogelijk de skinning-, posing- of mappingprocessen voor het hoofd van je karakter herhalen. Voor een algemeen overzicht van het proces voor het maken van avatarhoofden, zie [Hoofden maken](/docs/nl-nl/art/characters/facial-animation/create-basic-heads) .

Als je een sjabloon gebruikt en tegen problemen aanloopt, is het mogelijk dat de gezichtsgegevens zijn overschreven door een opgeslagen animatie, of dat de rigging of toegewezen gegevens per ongeluk zijn verwijderd. Als het moeilijk is om het probleem snel te identificeren en op te lossen, kan het sneller zijn om je karakteraanpassing opnieuw te starten vanaf het oorspronkelijke sjabloonbestand.

## [Skinning-gegevens](#skinning-gegevens)[](#skinning-gegevens)

Het correct skinnen van je karaktermodellen zorgt voor natuurlijke gewrichtsbewegingen en realistische poses en uitdrukkingen. Er zijn verschillende manieren om skinning-gegevens te verifiëren, zoals het gebruik van Blender's Pose-modus om de gewrichten van je karakter te poseren en te onderzoeken hoe bepaalde oriëntaties de skinning van de gewrichten kunnen beïnvloeden.

De volgende stappen kunnen je helpen de kwaliteit van je skinning-gegevens te verifiëren:

1.

Met het Armature -object geselecteerd, navigeer je naar Objecteigenschappen  > Viewport-weergave , en schakel je Toon Voor  in. Dit stelt je in staat om botten binnen je karakter te zien en te benaderen.

2.

Schakel over naar Pose -modus, selecteer vervolgens alle gezichtsbots van je model en druk op H  om ze te verbergen. Je kunt ze later weer onthullen met Alt H  (⌥ H ) in Pose-modus.

3.

Selecteer een willekeurig lichaamsbot en druk op R  om te roteren. Controleer of je lichaamsbotten het karaktermesh correct vervormen en buigen zoals verwacht in natuurlijke poses.

1.

Terwijl je een bot actief roteert, klik met de rechtermuisknop om de rotatie te annuleren en het bot naar zijn oorspronkelijke positie in te stellen.

2.

Terwijl je een bot actief roteert, kun je klikken om te bevestigen  en de huidige positie op te slaan. Je kunt verschillende poses van je karakter maken door de rotatie van verschillende ledematen tegelijk te veranderen.

3.

Als je een rotatie hebt opgeslagen, druk dan op Alt R  (⌥ R ) om eventuele rotatie in Pose-modus te wissen. Zorg ervoor dat je je pose reset telkens wanneer je de tests hebt voltooid.

Je kunt ook door veelvoorkomende poses en bewegingen gaan met behulp van Roblox's [Calisthenics Tool](/docs/nl-nl/art/modeling/calisthenics-tool)  add-on, die verschillende veelvoorkomende animaties toepast op een avatar-armatuur die je kunt afspelen en bekijken in Blender's animatietijdlijn.

De [Calisthenics Tool](/docs/nl-nl/art/modeling/calisthenics-tool)  voegt animaties toe aan je tijdlijn om snel lichaamsanimaties te previewen. Wees voorzichtig bij het opslaan of exporteren van je karakter wanneer je deze tool gebruikt, omdat het mogelijk conflicten kan veroorzaken met opgeslagen gezichtsanimatiegegevens die dezelfde tijdlijn gebruiken.

Als je problemen ontdekt met je skinning, moet je mogelijk de rigging- en skinningstappen voor je humanoïde oplossen en opnieuw toepassen. Voor een overzicht van de rigging- en skinningprocessen, zie [Rigging en skinning](/docs/nl-nl/art/modeling/rigging) .

Als je een sjabloon gebruikt, is het mogelijk dat de skinning-gegevens zijn beïnvloed door een destructieve modelleerwijziging. Dit kan vereisen dat je opnieuw moet skinnen of je karakteraanpassing opnieuw moet starten vanaf het oorspronkelijke sjabloonbestand.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
