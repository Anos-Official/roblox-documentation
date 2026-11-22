<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/dynamic-heads/facs-poses-reference -->

FACS poses referentie | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Animations
6. /
7. Dynamic heads

# FACS poses referentie

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het [Facial Action Coding System](https://en.wikipedia.org/wiki/Facial_Action_Coding_System)  (FACS) is een uitgebreid, anatomisch gebaseerd systeem voor het beschrijven van alle visueel waarneembare gezichtsbewegingen. Dit systeem splitst alle gezichtsuitdrukkingen op in individuele soorten spiersamentrekkingen, zoals LeftEyeClosed  of MouthLeft . Je kunt deze spiersamentrekkingen, of poses , configureren en opslaan binnen het hoofdmodel via een derde partij modellering software, zoals [Blender](https://www.blender.org)  of [Maya](https://www.autodesk.com/products/maya/overview) . Wanneer je het hoofdmodel in Studio importeert, kun je deze poses vervolgens [animeren](/docs/nl-nl/art/characters/facial-animation/animate-heads)  om levendige gezichtsuitdrukkingen te creëren.

Hieronder staat een lijst van 50 basisposes die je kunt gebruiken in Roblox om een breed scala aan gezichts-emoties uit te drukken. Behalve de eerste neutrale pose, maakt de volgorde van poses die je opslaat in je karaktermodel niet uit, aangezien deze informatie wordt ingesteld tijdens het [mappen](/docs/nl-nl/art/characters/facial-animation/create-basic-heads#map-elke-pose)  proces als een aangepaste eigenschap.

Als je van plan bent je avatar op de Marketplace te publiceren, moet het hoofd van je avatar de vereiste [17 gezichts basisposes](/docs/nl-nl/avatar/dynamic-heads/specifications#facs-poses)  bevatten. Marketplace-validatie wijst activa af die deze 17 vereiste basisposes niet bevatten.

Je kunt meerdere FACS basisposes samenvoegen in één animatiefase om complexe gezichtsuitdrukkingen te creëren. Sommige combinaties van poses kunnen echter botsen, tenzij je ook een [correctieve](/docs/nl-nl/art/characters/facial-animation/create-basic-heads#combinatieposes)  toevoegt aan hun volledige standaardwaarden.

## [LeftEyeClosed](#lefteyeclosed)[](#lefteyeclosed)

Als je publiceert op de Marketplace, moet je avatar asset deze pose bevatten.

[LeftEyeClosed](/docs/nl-nl/reference/engine/classes/FaceControls#LeftEyeClosed)  sluit het linkerooglid van het karakter.

## [RightEyeClosed](#righteyeclosed)[](#righteyeclosed)

Als je publiceert op de Marketplace, moet je avatar asset deze pose bevatten.

[RightEyeClosed](/docs/nl-nl/reference/engine/classes/FaceControls#RightEyeClosed)  sluit het rechterooglid van het karakter.

## [EyesLookDown](#eyeslookdown)[](#eyeslookdown)

Als je publiceert op de Marketplace, moet je avatar asset deze pose bevatten.

[EyesLookDown](/docs/nl-nl/reference/engine/classes/FaceControls#EyesLookDown)  laat de ogen naar beneden kijken.

## [JawDrop](#jawdrop)[](#jawdrop)

Als je publiceert op de Marketplace, moet je avatar asset deze pose bevatten.

[JawDrop](/docs/nl-nl/reference/engine/classes/FaceControls#JawDrop)  laat de kaak naar beneden zakken, waardoor de mond opent.

## [Pucker](#pucker)[](#pucker)

Als je publiceert op de Marketplace, moet je avatar asset deze pose bevatten.

[Pucker](/docs/nl-nl/reference/engine/classes/FaceControls#Pucker)  maakt een kusachtige vorm met de mond.

## [LeftLipCornerPuller](#leftlipcornerpuller)[](#leftlipcornerpuller)

Als je publiceert op de Marketplace, moet je avatar asset deze pose bevatten.

[LeftLipCornerPuller](/docs/nl-nl/reference/engine/classes/FaceControls#LeftLipCornerPuller)  tilt de hoeken van de mond omhoog in een glimlach.

## [RightLipCornerPuller](#rightlipcornerpuller)[](#rightlipcornerpuller)

Als je publiceert op de Marketplace, moet je avatar asset deze pose bevatten.

[RightLipCornerPuller](/docs/nl-nl/reference/engine/classes/FaceControls#RightLipCornerPuller)  tilt de hoeken van de mond omhoog in een glimlach.

## [ChinRaiser](#chinraiser)[](#chinraiser)

Als je publiceert op de Marketplace, moet je avatar asset deze pose bevatten.

[ChinRaiser](/docs/nl-nl/reference/engine/classes/FaceControls#ChinRaiser)  tilt de kin omhoog; beweegt de onderlip omhoog.

Wanneer je [ChinRaiser](/docs/nl-nl/reference/engine/classes/FaceControls#ChinRaiser)  gebruikt en de mond van het karakter is gesloten, botst de onderlip van het karakter met de bovenlip. Wanneer je de mond gesloten wilt houden terwijl je de kin omhoog tilt, gebruik dan [ChinRaiserUpperLip](#chinraiserupperlip)  en [ChinRaiser](/docs/nl-nl/reference/engine/classes/FaceControls#ChinRaiser)  samen om zowel de onderlip als de bovenlip omhoog te tillen en een botsing te voorkomen. Let op dat als je deze methode gebruikt, je zowel [ChinRaiser](/docs/nl-nl/reference/engine/classes/FaceControls#ChinRaiser)  als [ChinRaiserUpperLip](#chinraiserupperlip)  op dezelfde waarde moet instellen, zodat de lippen dezelfde afstand omhoog bewegen.

## [ChinRaiserUpperLip](#chinraiserupperlip)[](#chinraiserupperlip)

Als je publiceert op de Marketplace, moet je avatar asset deze pose bevatten.

[ChinRaiserUpperLip](/docs/nl-nl/reference/engine/classes/FaceControls#ChinRaiserUpperLip)  tilt de bovenlip omhoog wanneer ChinRaiser is ingeschakeld en deze de bovenlip aanraakt.

## [LeftCheekRaiser](#leftcheekraiser)[](#leftcheekraiser)

Als je publiceert op de Marketplace, moet je avatar asset deze pose bevatten.

[LeftCheekRaiser](/docs/nl-nl/reference/engine/classes/FaceControls#LeftCheekRaiser)  doet het linkeroog van het karakter knijpen.

## [RightCheekRaiser](#rightcheekraiser)[](#rightcheekraiser)

Als je publiceert op de Marketplace, moet je avatar asset deze pose bevatten.

[RightCheekRaiser](/docs/nl-nl/reference/engine/classes/FaceControls#RightCheekRaiser)  doet het rechteroog van het karakter knijpen.

## [LeftInnerBrowRaiser](#leftinnerbrowraiser)[](#leftinnerbrowraiser)

Als je publiceert op de Marketplace, moet je avatar asset deze pose bevatten.

[LeftInnerBrowRaiser](/docs/nl-nl/reference/engine/classes/FaceControls#LeftInnerBrowRaiser)  tilt de binnenste helft van de linker wenkbrauw van het karakter omhoog.

## [RightInnerBrowRaiser](#rightinnerbrowraiser)[](#rightinnerbrowraiser)

Als je publiceert op de Marketplace, moet je avatar asset deze pose bevatten.

[RightInnerBrowRaiser](/docs/nl-nl/reference/engine/classes/FaceControls#RightInnerBrowRaiser)  tilt de binnenste helft van de rechter wenkbrauw van het karakter omhoog.

## [LeftLipCornerDown](#leftlipcornerdown)[](#leftlipcornerdown)

Als je publiceert op de Marketplace, moet je avatar asset deze pose bevatten.

[LeftLipCornerDown](/docs/nl-nl/reference/engine/classes/FaceControls#LeftLipCornerDown)  laat de hoeken van de mond naar beneden zakken in een frons.

## [RightLipCornerDown](#rightlipcornerdown)[](#rightlipcornerdown)

Als je publiceert op de Marketplace, moet je avatar asset deze pose bevatten.

[RightLipCornerDown](/docs/nl-nl/reference/engine/classes/FaceControls#RightLipCornerDown)  laat de hoeken van de mond naar beneden zakken in een frons.

## [LeftLowerLipDepressor](#leftlowerlipdepressor)[](#leftlowerlipdepressor)

Als je publiceert op de Marketplace, moet je avatar asset deze pose bevatten.

[LeftLowerLipDepressor](/docs/nl-nl/reference/engine/classes/FaceControls#LeftLowerLipDepressor)  laat de onderlip naar beneden zakken, weg van de bovenlip, waardoor de ondertanden zichtbaar worden.

## [RightLowerLipDepressor](#rightlowerlipdepressor)[](#rightlowerlipdepressor)

Als je publiceert op de Marketplace, moet je avatar asset deze pose bevatten.

[RightLowerLipDepressor](/docs/nl-nl/reference/engine/classes/FaceControls#RightLowerLipDepressor)  laat de onderlip naar beneden zakken, weg van de bovenlip, waardoor de ondertanden zichtbaar worden.

## [EyesLookLeft](#eyeslookleft)[](#eyeslookleft)

[EyesLookLeft](/docs/nl-nl/reference/engine/classes/FaceControls#EyesLookLeft)  laat de ogen naar links kijken.

## [EyesLookRight](#eyeslookright)[](#eyeslookright)

[EyesLookRight](/docs/nl-nl/reference/engine/classes/FaceControls#EyesLookRight)  laat de ogen naar rechts kijken.

## [EyesLookUp](#eyeslookup)[](#eyeslookup)

[EyesLookUp](/docs/nl-nl/reference/engine/classes/FaceControls#EyesLookUp)  laat de ogen omhoog kijken.

## [LeftLipStretcher](#leftlipstretcher)[](#leftlipstretcher)

[LeftLipStretcher](/docs/nl-nl/reference/engine/classes/FaceControls#LeftLipStretcher)  strekt de hoeken van de mond uit elkaar.

## [LeftUpperLipRaiser](#leftupperlipraiser)[](#leftupperlipraiser)

[LeftUpperLipRaiser](/docs/nl-nl/reference/engine/classes/FaceControls#LeftUpperLipRaiser)  tilt de bovenlip van het karakter omhoog, weg van de onderlip, waardoor de boventanden zichtbaar worden.

## [LipsTogether](#lipstogether)[](#lipstogether)

[LipsTogether](/docs/nl-nl/reference/engine/classes/FaceControls#LipsTogether)  brengt de lippen van het karakter samen. Als de mond van het karakter echter gesloten is, zijn hun lippen al samen en botsen ze.

De belangrijkste gebruiksdoel van deze pose is in verband met de [JawDrop](#jawdrop)  eigenschap. Als je [JawDrop](#jawdrop)  en [LipsTogether](/docs/nl-nl/reference/engine/classes/FaceControls#LipsTogether)  op 100% van hun standaardwaarden instelt, blijven de lippen van het karakter samen terwijl de kaak zakt.

Bovendien, als je [JawDrop](#jawdrop)  op 100% van zijn standaardwaarde instelt, en [LipsTogether](/docs/nl-nl/reference/engine/classes/FaceControls#LipsTogether)  in en uit 100% van zijn standaardwaarde laat verlopen, openen en sluiten de lippen van het karakter.

## [RightLipStretcher](#rightlipstretcher)[](#rightlipstretcher)

[RightLipStretcher](/docs/nl-nl/reference/engine/classes/FaceControls#RightLipStretcher)  strekt de hoeken van de mond uit elkaar.

## [RightUpperLipRaiser](#rightupperlipraiser)[](#rightupperlipraiser)

[RightUpperLipRaiser](/docs/nl-nl/reference/engine/classes/FaceControls#RightUpperLipRaiser)  tilt de rechterbovenlip van het karakter omhoog, weg van de onderlip, waardoor de boventanden zichtbaar worden.

## [FlatPucker](#flatpucker)[](#flatpucker)

[FlatPucker](/docs/nl-nl/reference/engine/classes/FaceControls#FlatPucker)  brengt de hoeken van de mond naar binnen en drukt de lippen tegen de tanden aan. Deze pose staat ook bekend als lipverstrakker.

## [Funneler](#funneler)[](#funneler)

[Funneler](/docs/nl-nl/reference/engine/classes/FaceControls#Funneler)  maakt een 'O' vorm met de mond.

## [LowerLipSuck](#lowerlipsuck)[](#lowerlipsuck)

[LowerLipSuck](/docs/nl-nl/reference/engine/classes/FaceControls#LowerLipSuck)  rolt de onderlip over de tanden.

## [LipPresser](#lippresser)[](#lippresser)

[LipPresser](/docs/nl-nl/reference/engine/classes/FaceControls#LipPresser)  drukt de lippen samen.

## [MouthLeft](#mouthleft)[](#mouthleft)

[MouthLeft](/docs/nl-nl/reference/engine/classes/FaceControls#MouthLeft)  verplaatst de mond naar links van het karakter. Deze eigenschap verplaatst de kaak, tanden of tong van het karakter niet, alleen hun mond. Als je die extra gezichtskenmerken wilt verplaatsen, gebruik dan [JawLeft](#jawleft)  in plaats daarvan.

## [MouthRight](#mouthright)[](#mouthright)

[MouthRight](/docs/nl-nl/reference/engine/classes/FaceControls#MouthRight)  verplaatst de mond naar rechts van het karakter. Deze eigenschap verplaatst de kaak, tanden of tong van het karakter niet naar rechts, alleen hun mond. Als je die extra gezichtskenmerken wilt verplaatsen, gebruik dan [JawRight](#jawright)  in plaats daarvan.

## [UpperLipSuck](#upperlipsuck)[](#upperlipsuck)

[UpperLipSuck](/docs/nl-nl/reference/engine/classes/FaceControls#UpperLipSuck)  rolt de bovenlip om de tanden.

## [LeftCheekPuff](#leftcheekpuff)[](#leftcheekpuff)

[LeftCheekPuff](/docs/nl-nl/reference/engine/classes/FaceControls#LeftCheekPuff)  blaast de linkerwang van het karakter op.

## [LeftDimpler](#leftdimpler)[](#leftdimpler)

[LeftDimpler](/docs/nl-nl/reference/engine/classes/FaceControls#LeftDimpler)  beweegt de hoeken van de linkerkant van de mond terug naar de tanden.

## [RightCheekPuff](#rightcheekpuff)[](#rightcheekpuff)

[RightCheekPuff](/docs/nl-nl/reference/engine/classes/FaceControls#RightCheekPuff)  blaast de rechterwang van het karakter op.

## [RightDimpler](#rightdimpler)[](#rightdimpler)

[RightDimpler](/docs/nl-nl/reference/engine/classes/FaceControls#RightDimpler)  beweegt de hoeken van de rechterkant van de mond terug naar de tanden.

## [JawLeft](#jawleft)[](#jawleft)

[JawLeft](/docs/nl-nl/reference/engine/classes/FaceControls#JawLeft)  verplaatst de kaak, tanden, tong en onderlip van het karakter naar links. Als je alleen de mond van het karakter naar links wilt verplaatsen, gebruik dan [MouthLeft](#mouthleft)  in plaats daarvan.

## [JawRight](#jawright)[](#jawright)

[JawRight](/docs/nl-nl/reference/engine/classes/FaceControls#JawRight)  verplaatst de kaak, tanden, tong en onderlip van het karakter naar rechts. Als je alleen de mond van het karakter naar rechts wilt verplaatsen, gebruik dan [MouthRight](#mouthright)  in plaats daarvan.

## [Corrugator](#corrugator)[](#corrugator)

[Corrugator](/docs/nl-nl/reference/engine/classes/FaceControls#Corrugator)  brengt de linker- en rechterwenkbrauwen naar binnen samen.

## [LeftBrowLowerer](#leftbrowlowerer)[](#leftbrowlowerer)

[LeftBrowLowerer](/docs/nl-nl/reference/engine/classes/FaceControls#LeftBrowLowerer)  laat de linkerwenkbrauw van het karakter naar beneden zakken.

## [LeftOuterBrowRaiser](#leftouterbrowraiser)[](#leftouterbrowraiser)

[LeftOuterBrowRaiser](/docs/nl-nl/reference/engine/classes/FaceControls#LeftOuterBrowRaiser)  tilt het buitenste deel van de linkerwenkbrauw van het karakter omhoog.

## [LeftNoseWrinkler](#leftnosewrinkler)[](#leftnosewrinkler)

[LeftNoseWrinkler](/docs/nl-nl/reference/engine/classes/FaceControls#LeftNoseWrinkler)  tilt het linker neusgat van het karakter omhoog, trekt de wenkbrauw iets naar beneden en rimpelt de linkerkant van de neus.

## [RightBrowLowerer](#rightbrowlowerer)[](#rightbrowlowerer)

[RightBrowLowerer](/docs/nl-nl/reference/engine/classes/FaceControls#RightBrowLowerer)  laat de rechterwenkbrauw van het karakter naar beneden zakken.

## [RightOuterBrowRaiser](#rightouterbrowraiser)[](#rightouterbrowraiser)

[RightOuterBrowRaiser](/docs/nl-nl/reference/engine/classes/FaceControls#RightOuterBrowRaiser)  tilt het buitenste deel van de rechterwenkbrauw van het karakter omhoog.

## [RightNoseWrinkler](#rightnosewrinkler)[](#rightnosewrinkler)

[RightNoseWrinkler](/docs/nl-nl/reference/engine/classes/FaceControls#RightNoseWrinkler)  tilt het rechter neusgat van het karakter omhoog, trekt de wenkbrauw iets naar beneden en rimpelt de rechterkant van de neus.

## [LeftEyeUpperLidRaiser](#lefteyeupperlidraiser)[](#lefteyeupperlidraiser)

[LeftEyeUpperLidRaiser](/docs/nl-nl/reference/engine/classes/FaceControls#LeftEyeUpperLidRaiser)  tilt het linkerooglid van het karakter omhoog om meer van het witte deel van het oog boven de iris te onthullen.

## [RightEyeUpperLidRaiser](#righteyeupperlidraiser)[](#righteyeupperlidraiser)

[RightEyeUpperLidRaiser](/docs/nl-nl/reference/engine/classes/FaceControls#RightEyeUpperLidRaiser)  tilt het rechterooglid van het karakter omhoog om meer van het witte deel van het oog boven de iris te onthullen.

## [TongueDown](#tonguedown)[](#tonguedown)

[TongueDown](/docs/nl-nl/reference/engine/classes/FaceControls#TongueDown)  buigt de tong naar beneden. Deze pose is alleen zichtbaar als je deze combineert met [TongueOut](#tongueout) , anders buigt de tong alleen naar beneden binnen de mond van het karakter.

## [TongueOut](#tongueout)[](#tongueout)

[TongueOut](/docs/nl-nl/reference/engine/classes/FaceControls#TongueOut)  steekt de punt van de tong uit de mond.

## [TongueUp](#tongueup)[](#tongueup)

[TongueUp](/docs/nl-nl/reference/engine/classes/FaceControls#TongueUp)  buigt de tong omhoog. Deze pose is alleen zichtbaar als je deze combineert met [TongueOut](#tongueout) , anders buigt de tong alleen omhoog binnen de mond van het karakter.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
