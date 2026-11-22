<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/animation-packs -->

Animatiepakketten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Animations

# Animatiepakketten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een animatiepakket  is een gecoördineerde set van locomotieclips voor avatars die bepaalt hoe de karakter van een speler zich door ervaringen beweegt. Elk pakket vervangt de standaard bewegingsanimaties voor zeven kernlocomotiestaten.

## [Inhoud van het animatiepakket](#inhoud-van-het-animatiepakket)[](#inhoud-van-het-animatiepakket)

Een compleet animatiepakket dekt de volgende locomotiestaten:

| Staat | | Vereiste clips | | Aantal clips | | Beschrijving |
| --- | --- |
| Stil | | Stil | | 1 of 2 | | Stilstaand zonder spelerinvoer. |
| Lopen | | Lopen | | 1 | | Bewegen met loopsnelheid. |
| Rennen | | Rennen | | 1 | | Bewegen met rensnelheid. |
| Springen | | Springen | | 1 | | De lucht in lanceren. |
| Vallen | | Vallen | | 1 | | Dalen na een sprongetje of van een rand. |
| Klimmen | | Klimmen | | 1 | | Op een klimbare oppervlakte omhoog gaan. |
| Zwemmen | | Zwemmen en Stilzwemmen | | 2 | | Bewegen door water of stilstaand in water. |

Stil ondersteunt tot twee clips, en Zwemmen omvat zowel bewegende als stilstaande sub-animaties, dus een compleet pakket bevat acht of negen clips.

Animatiepakketten verschillen van [emotes](/docs/nl-nl/avatar/emotes) . Emotes zijn sociale animaties die een speler activeert, zoals gebaren of dansen. Animatiepakketten vervangen de locomotieset die automatisch afspeelt tijdens beweging.

## [Vereisten en beperkingen](#vereisten-en-beperkingen)[](#vereisten-en-beperkingen)

Animatiepakketten moeten voldoen aan de volgende vereisten:

-

Alle clips moeten verwijzen naar een [standaard R15 rig](/docs/nl-nl/avatar/character-bodies/specifications#standaard-r15-rigs) .

-

Alle clips moeten origineel werk zijn van de maker. Pakketten die standaard Roblox-animaties hergebruiken, falen in de validatie.

-

Elke clip moet een [CurveAnimation](/docs/nl-nl/reference/engine/classes/CurveAnimation)  zijn. Het uploadproces accepteert geen [KeyframeSequence](/docs/nl-nl/reference/engine/classes/KeyframeSequence) -gegevens.

-

Elke clip moet 10 seconden of korter zijn.

-

Alle clips behalve Springen moeten in een lus afspelen.

-

Elke clip in het pakket moet dezelfde Ouder modelnaam  delen, zodat Studio ze in één oudermodel groepeert.

-

Pakketten moeten voldoen aan het [Marketplace-beleid](/docs/nl-nl/marketplace/marketplace-policy) .

Je kunt clips maken in Studio of een extern hulpmiddel, maar je moet de upload en het samenstellen van het pakket in Studio voltooien. Uploads zijn beperkt tot één pakket per dag per maker. De uploadkosten zijn 80 Robux per pakket.

Voor details over kosten, commissies en huidige prijsvloeren, zie [Marketplace-kosten en commissies](/docs/nl-nl/marketplace/marketplace-fees-and-commissions) . Voor de algemene workflow voor het publiceren op de Marketplace, zie [Publiceren op Marketplace](/docs/nl-nl/marketplace/publish-to-marketplace) .

## [Voorbereiden van animatieclips](#voorbereiden-van-animatieclips)[](#voorbereiden-van-animatieclips)

Herhaal de volgende voorbereidingsworkflow voor elke van de acht of negen vereiste clips.

### [Stel een R15 rig in](#stel-een-r15-rig-in)[](#stel-een-r15-rig-in)

1.

Ga naar het tabblad Avatar , klik op Character  om de Rig Builder te openen.

2.

Selecteer R15 , selecteer vervolgens Block Avatar  om een basisrig in de werkruimte in te voegen.

3.

Ga naar het tabblad Avatar , klik op Clip Editor  om de [Animatie-editor](/docs/nl-nl/animation/editor)  te openen.

4.

Selecteer de rig in de viewport of het Explorer -venster. De tijdlijn van de Animatie-editor wordt geactiveerd.

De resulterende clips spelen op elke ondersteunde avatar-uiterlijk. Het maken op een standaard R15 Block Avatar-rig biedt brede compatibiliteit.

### [Importeer een animatieclip](#importeer-een-animatieclip)[](#importeer-een-animatieclip)

1.

In de Animatie-editor, klik op ⋯  naast de rig-naam, selecteer vervolgens Importeren  ⟩ Van Bestand .

2.

Selecteer het doel .fbx -bestand.

3.

In de prompt Importinstellingen , selecteer Geïmporteerde Rig  als de bron voor de rootpose.

4.

Klik op Importeren . De animatiegegevens worden in de tijdlijn ingevuld.

### [Converteer een clip naar CurveAnimation](#converteer-een-clip-naar-curveanimation)[](#converteer-een-clip-naar-curveanimation)

1.

Op de tijdlijnbedieningsbalk, klik op de knop Curve Editor  rechts van de afspeelbediening.

2.

Klik op Bevestigen . De track wordt geconverteerd naar een [CurveAnimation](/docs/nl-nl/reference/engine/classes/CurveAnimation) -clip.

3.

Hernoem de clip in het tekstveld linksboven in de Animatie-editor, zoals klim , vallen , stil1 , of springen .

4.

Klik op ⋯ , selecteer vervolgens Opslaan  om de clip lokaal op te slaan.

Converteren naar een [CurveAnimation](/docs/nl-nl/reference/engine/classes/CurveAnimation)  is onomkeerbaar, en de clip werkt mogelijk niet met sommige derde-partij animatieplugins. Controleer je animatiegegevens voordat je converteert.

Voor meer informatie over curve-gebaseerde bewerking, zie [Curve Editor](/docs/nl-nl/animation/curve-editor) .

### [Configureer clip looping](#configureer-clip-looping)[](#configureer-clip-looping)

1.

In het Explorer -venster, breid [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage)  ⟩ RBX_ANIMSAVES  ⟩ [jouw rig]  uit.

2.

Selecteer de opgeslagen animatietrack.

3.

In het Eigenschappen -venster, zoek de sectie Gegevens  en schakel Loop  in.

Alle clips behalve Springen moeten in een lus afspelen. Springen speelt één keer per actie en mag niet in een lus afspelen.

## [Upload animatieclips](#upload-animatieclips)[](#upload-animatieclips)

Herhaal het volgende uploadproces voor elke opgeslagen clip:

1.

In het Explorer -venster, klik met de rechtermuisknop op het animatievermogen en selecteer Opslaan naar Roblox .

2.

Stel Titel  in op de clipnaam.

3.

Stel Maker  in op jouw account of groep.

4.

Schakel Stel animatie-eigenschappen in (Optioneel)  in. Het dialoogvenster wordt uitgebreid met extra velden.

5.

Vul de velden voor animatie-eigenschappen in zoals beschreven in [Configureer animatie-eigenschappen](#configureer-animatie-eigenschappen) . Hoewel de UI deze instelling als optioneel labelt, moet je deze velden invullen om het pakket correct samen te stellen.

6.

Klik op Opslaan , wacht vervolgens op de bevestiging Succesvol ingediend  met de nieuwe asset-ID.

### [Configureer animatie-eigenschappen](#configureer-animatie-eigenschappen)[](#configureer-animatie-eigenschappen)

| Veld | | Beschrijving |
| Animatietype | | De bijpassende locomotiecategorie, zoals Klimanimatie , Loopanimatie , of Stilanimatie . |
| Subanimatie | | De bijpassende subtype indien van toepassing. Voor Zwemclips, selecteer Zwem  voor de bewegende clip en Stilzwemmen  voor de stilstaande clip. |
| Ouder modelnaam | | Een gedeelde string voor elke clip in het pakket, zoals mijn_animatie_pakket . Studio gebruikt deze string om alle clips in één oudermodel onder [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  te groeperen. |
| Gewicht | | Geldt alleen voor Stilclips. Zie [Wijs Stilgewichten toe](#wijs-stilgewichten-toe) . |

Elke clip in het pakket moet dezelfde Ouder modelnaam  gebruiken. Als de namen niet overeenkomen, maakt Studio aparte modellen en faalt het pakket in de validatie.

### [Wijs Stilgewichten toe](#wijs-stilgewichten-toe)[](#wijs-stilgewichten-toe)

Een pakket ondersteunt tot twee Stilclips. Het veld Gewicht  accepteert een positief geheel getal dat het relatieve selectiegewicht tussen de clips definieert. Het standaardgewicht is 1  wanneer het veld leeg is.

## [Stel een animatiepakket samen en valideer het](#stel-een-animatiepakket-samen-en-valideer-het)[](#stel-een-animatiepakket-samen-en-valideer-het)

1.

In het Explorer -venster onder [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) , zoek het oudermodel dat is gemaakt van de gedeelde Ouder modelnaam .

2.

Klik met de rechtermuisknop op het oudermodel en selecteer Opslaan naar Roblox .

3.

Stel Titel  en Beschrijving  in op de publiek zichtbare naam en details voor het pakket.

4.

Stel Inhoudstype  in op Avatar-item .

5.

Stel Assetcategorie  in op Avatar-animaties .

6.

Controleer de validatielijst. Studio toont zeven staatsgroepen: Vallen, Zwemmen, Springen, Lopen, Klimmen, Stil, en Rennen. Elke vermelding moet Validatie Geslaagd  tonen.

7.

Als een vermelding een fout toont, corrigeer het probleem voordat je verdergaat. Veelvoorkomende oorzaken zijn onder andere niet-overeenkomende ouder modelnamen, ontbrekende clips, onjuiste looping-instellingen, of clips die geen [CurveAnimation](/docs/nl-nl/reference/engine/classes/CurveAnimation) -objecten zijn.

8.

Controleer de weergegeven transactiegegevens en klik op Betalen & Indienen .

Na indiening, volg de bevestigingslink naar het Creator Dashboard om de Marketplace-instellingen te configureren.

Een clip faalt in de validatie als deze een van de volgende dingen doet:

-

Verplaatst het rootgewricht te ver van zijn startpositie.

-

Overschrijdt de maximale snelheid van frame-tot-frame beweging.

-

Verplaatst een lichaamsdeel meer dan 1,5 studs van zijn startpositie in een frame.

-

Duurt langer dan 10 seconden.

Voor de complete lijst van validatiecontroles en foutmeldingen, zie [UGC-validatiesysteem](/docs/nl-nl/marketplace/validation-system) .

## [Publiceer een animatiepakket](#publiceer-een-animatiepakket)[](#publiceer-een-animatiepakket)

Na indiening in Studio komt het pakket in de moderatiewachtrij. Zodra het is goedgekeurd, configureer je prijzen, beschikbaarheid en andere Marketplace-instellingen in het Creator Dashboard. De prijsvloer voor animatiepakketten op de Marketplace is 300 Robux. Dit is de minimale verkoopprijs, geen extra kosten.

Groepsuploads en Beperkte publicatie worden ondersteund voor animatiepakketten.

Voor de volledige publicatieworkflow, inclusief metadata, prijzen en verkoopopties, zie [Publiceren op Marketplace](/docs/nl-nl/marketplace/publish-to-marketplace) . Voor details over kosten, commissies en prijsklassen, zie [Marketplace-kosten en commissies](/docs/nl-nl/marketplace/marketplace-fees-and-commissions) .

## [Gedrag van animatiepakketten in ervaringen](#gedrag-van-animatiepakketten-in-ervaringen)[](#gedrag-van-animatiepakketten-in-ervaringen)

Wanneer een speler een animatiepakket uitrust, wordt het pakket toegepast in elke ervaring waarvan de instelling Animatiepakketten  is ingesteld op Spelerkeuze . Dit is de standaardinstelling. Ontwikkelaars kunnen Standaard R15  of Standaard R6  selecteren om de animatiepakketten van de speler te overschrijven met standaard platformanimaties.

Voor meer informatie over het configureren van animatie- en bewegingsinstellingen, zie [Avatar-instellingen](/docs/nl-nl/studio/avatar-settings#beweging) .

## [Probleemoplossing](#probleemoplossing)[](#probleemoplossing)

| Probleem | | Correctie |
| Pakket mist een of meer locomotiestaten tijdens validatie. | | Controleer of je een clip hebt geüpload voor elke vereiste staat en dat elke clip de juiste waarden voor Animatietype  en Subanimatie  gebruikt. |
| Ouder modelnamen komen niet overeen. | | Elke clip in het pakket moet dezelfde Ouder modelnaam -string gebruiken. Herupload elke clip die een andere naam gebruikt. |
| Clip loopt niet zoals verwacht. | | Alle clips behalve Springen moeten Loop  ingeschakeld hebben in het Eigenschappen -venster. Selecteer de opgeslagen track onder [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage)  ⟩ RBX_ANIMSAVES  ⟩ [jouw rig] , schakel vervolgens Loop  in. |
| Clip is geen CurveAnimation. | | Converteer de clip met de knop Curve Editor  in de Animatie-editor voordat je opslaat. Het uploadproces vereist [CurveAnimation](/docs/nl-nl/reference/engine/classes/CurveAnimation)  output. |
| Validatie faalt met ruimtelijke grenzenfouten. | | Een lichaamsdeel verplaatst meer dan 1,5 studs van zijn startpositie in een frame, het rootgewricht beweegt te ver van zijn startpositie, of de clip overschrijdt de maximale snelheid van frame-tot-frame beweging. Verminder extreme vertalingen en exporteer de clip opnieuw. |
| Validatie faalt met een duurfout. | | Elke clip moet 10 seconden of korter zijn. Trim de clip in de Animatie-editor en upload deze opnieuw. |
| Upload faalt met een eigendom of moderatiefout. | | Controleer of je alle animatie-assets bezit of de juiste groepsmachtigingen hebt. Assets met een hangende moderatie of die toebehoren aan een andere maker kunnen niet in het pakket worden opgenomen. |
| Groepsupload faalt vanwege ontbrekende machtigingen. | | Controleer of het uploadaccount een groepsrol heeft met toestemming om assets te maken. |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
