<!-- Source: https://create.roblox.com/docs/nl-nl/animation/curve-editor -->

Curveneditor | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Animatie](/docs/nl-nl/animation)
6. /
7. Animaties maken
8. /
9. [Animatie-editor](/docs/nl-nl/animation/editor)

# Curveneditor

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De Curveneditor  is een op curven gebaseerde animatiebewerkingsinterface binnen de [Animatie-editor](/docs/nl-nl/animation/editor)  die je in staat stelt om te zien en te wijzigen hoe de positie en oriëntatie van een rig verandert tussen keyframes via kleurgecodeerde curvegrafieken. Het stelt je in staat om onafhankelijke tracks voor de X , Y  en Z  hoeken te definiëren, wat extra niveaus van controle biedt om je animaties vloeiender en realistischer te maken.

In plaats van de standaard methode van de dope sheet editor waarbij je de scrubber handmatig van het ene frame naar het andere verplaatst om te zien hoe de positie en oriëntatie van een rig in de loop van de tijd veranderen, laat de Curveneditor je snel de positie- en oriëntatiewaarden van je geselecteerde tracks raadplegen via de positie liniaal  aan de linkerkant van de tijdlijn en de rotatie liniaal  aan de rechterkant van de tijdlijn.

 ![Overzicht Curveneditor](https://prod.docsiteassets.roblox.com/assets/animation/curve-editor/UI-Overview.png)

## [Open de Curveneditor](#open-de-curveneditor)[](#open-de-curveneditor)

Je kunt de tijdlijn van de editor op elk moment tussen de dope sheet editor en de Curveneditor schakelen.

1.

Open de [Animatie-editor](/docs/nl-nl/animation/editor)  vanuit het Avatar  tabblad van Studio of het Venster  ⟩ Avatar  menu.

 ![Animatie-editor aangegeven in de werkbalk van Studio](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Animation.png)

2.

BELANGRIJK

 Studio converteert automatisch [quaternions](https://en.wikipedia.org/wiki/Quaternion)  naar [Euler-hoeken](https://en.wikipedia.org/wiki/Euler_angles)  wanneer je de Curveneditor opent, dus het is belangrijk dat je je rotatietype voordat  je naar de Curveneditor schakelt verifieert. Zodra je quaternions naar Euler-hoek tracks converteert, is het onmogelijk om ze terug te converteren naar quaternions.

1.

Klik in de rechterbovenhoek van het editorvenster op het instellingenpictogram. Een contextmenu wordt weergegeven.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/curve-editor/Timeline-Options-Menu.png)

2.

Beweeg de muis over Standaard Rotatietype , en selecteer vervolgens Euler-hoeken  of Quaternions . Je rotatietype wordt ingesteld op je keuze en wordt het standaard rotatietype voor toekomstige projecten.

3.

Klik in de linkerbovenhoek van de tijdlijn  op het Curveneditor  pictogram. Een pop-upvenster wordt weergegeven om te bevestigen dat je [KeyframeSequence](/docs/nl-nl/reference/engine/classes/KeyframeSequence)  clip zal worden geconverteerd naar een [CurveAnimation](/docs/nl-nl/reference/engine/classes/CurveAnimation)  clip.

 ![Curveneditor openen](https://prod.docsiteassets.roblox.com/assets/animation/curve-editor/Opening-Curve-Editor.png)

Als je het standaard rotatietype van Euler-hoeken hebt behouden, converteert Studio automatisch alle bestaande quaternions naar Euler-hoeken volgens de instelling voor de [volgorde van Euler-hoeken](#volgorde-van-euler-hoeken) . Omdat [KeyframeSequences](/docs/nl-nl/reference/engine/classes/KeyframeSequence)  werken met quaternions en curve-animaties standaard werken met Euler-hoeken, kan je animatie er iets anders uitzien tussen keyframes, vooral als een van je Euler-hoeken in de buurt komt van [Gimbal lock](https://en.wikipedia.org/wiki/Gimbal_lock) .

Als je het rotatietype op quaternions hebt ingesteld, behoudt de conversie naar curven de quaternions en blijft de animatie hetzelfde.

## [Interpolatie](#interpolatie)[](#interpolatie)

Interpolatie is het proces van Studio om "in te vullen" positie- en oriëntatiewaarden tussen je keyframes. Dit stelt de rig in staat om naadloos van de ene oriëntatie of positie naar de andere te animeren in plaats van schokkerig tussen keyframes te springen. Terwijl Euler-hoek curven interpoleren tussen de waarden van elk keyframe, interpoleren quaternion curven van 0  naar 1  over een bepaalde tijd. Om dit te illustreren, tonen de volgende afbeeldingen dezelfde [KeyframeSequence](/docs/nl-nl/reference/engine/classes/KeyframeSequence)  nadat je de Curveneditor opent met ofwel een Euler-hoek of een quaternion rotatietype:

![](https://prod.docsiteassets.roblox.com/assets/animation/curve-editor/Euler-Angle-Curve.png) Euler-hoek Curve

![](https://prod.docsiteassets.roblox.com/assets/animation/curve-editor/Quaternion-Curve-Interpolation.png) Quaternion Curve

Voor Euler-hoek curven  vertegenwoordigt de hoogte van elk keyframe zijn oriëntatiewaarde in de loop van de tijd. Voor quaternion curven  vertegenwoordigt elk segment de oriëntatie die verandert tussen keyframes, en de lijn toont de interpolatie tussen hen.

Je kunt aanpassen hoe de Curveneditor de interpolatie voor zowel Euler-hoek curven als quaternion curven behandelt door [tangenten in te stellen](#instellen) , [de interpolatiemodus te wijzigen](#interpolatiemodus) , of door [interpolatiecurven te genereren](#genereer-interpolatiecurven)  tussen twee of meer keyframes.

### [Tangenten](#tangenten)[](#tangenten)

De Curveneditor biedt tangenten , of handvatten, waarmee je snel de interpolatie vóór of na een keyframe kunt aanpassen. Euler-hoek curven hebben een tangent zowel vóór als na het keyframe, terwijl quaternion curven één tangent aan het begin en een andere aan het einde van een segment hebben. De initiële tangent controleert de interpolatie na het keyframe en de secundaire tangent controleert de interpolatie vóór het keyframe. Bijvoorbeeld:

![](https://prod.docsiteassets.roblox.com/assets/animation/curve-editor/Euler-Angle-Curve-Tangents.png) Euler-hoek Curve Tangenten

![](https://prod.docsiteassets.roblox.com/assets/animation/curve-editor/Quaternion-Curve-Tangents.png) Quaternion Curve Tangenten

Voor quaternion curve tangenten, ongeacht hoe veel je elke tangent aanpast, begint elk segment altijd bij 0  en eindigt bij 1 . Hoewel elk segment van een quaternion curve grafiek losgekoppeld is van de volgende segmenten, vertegenwoordigen de twee keyframes binnen hetzelfde frame altijd dezelfde oriëntatie.

Tangenten veranderen van uiterlijk wanneer je ze naar een nieuwe positie instelt; een niet ingestelde tangent wordt weergegeven als een heldere cirkel, en een ingestelde tangent wordt weergegeven als een witte cirkel. Studio berekent automatisch de positie voor niet ingestelde tangenten op basis van de positie van ingestelde tangenten. Bijvoorbeeld, als je slechts één tangent instelt en de andere niet instelt, wordt de niet ingestelde tangent uitgelijnd met zijn tegenovergestelde tangent.

#### [Instellen](#instellen)[](#instellen)

Om een tangent in te stellen:

1.

Klik en sleep de tangent in de richting waarin je de curve wilt trekken. De curve past zich aan op basis van de locatie van je cursor.

2.

Laat de tangent los. De interpolatie tussen keyframes past zich dienovereenkomstig aan.

3.

OPTIONEEL

 Als je één tangent hebt ingesteld en de niet ingestelde tangent horizontaal wilt uitlijnen, klik met de rechtermuisknop op de niet ingestelde tangent en selecteer Stel Tangent in op Nul  in het contextmenu.

#### [Reset](#reset)[](#reset)

Als je ooit een tangent naar een nieuwe positie hebt ingesteld en de resulterende interpolatie ongewenst is, kun je altijd de "auto-tangent modus" gebruiken om de waarde van een tangent te wissen en deze terug te zetten naar het standaard interpolatiegedrag.

1.

Klik met de rechtermuisknop op een tangent. Een contextmenu wordt weergegeven.

2.

Selecteer Stel Tangent In Op Nul . De tangent wordt teruggezet naar zijn standaard interpolatiegedrag.

### [Interpolatiemodus](#interpolatiemodus)[](#interpolatiemodus)

De interpolatiemodus is de snelheid waarmee een animatie beweegt tussen verschillende keyframeposities binnen de animatie. Er zijn drie interpolatiemodi beschikbaar voor curve-animaties:

-

Lineair  (standaard) — Beweegt met een constante snelheid van het ene keyframe naar het andere.

-

Constant  — Verwijdert de interpolatie tussen het geselecteerde keyframe en het volgende keyframe, waardoor de animatie "snapt" van keyframe naar keyframe.

-

Cubic  — Versnelt in en/of uit de animatie. Cubic is de enige modus die je in staat stelt om tangenten te definiëren.

Om de interpolatiemodus te wijzigen:

1.

Klik met de rechtermuisknop op een keyframe. Een contextmenu wordt weergegeven.

2.

Beweeg de muis over Interpolatiemodus , en selecteer vervolgens Lineair , Constant , of Cubic . De interpolatiemodus verandert de curve na het keyframe.

### [Genereer interpolatiecurven](#genereer-interpolatiecurven)[](#genereer-interpolatiecurven)

Voor curve-animaties zijn bounce- en elastische easing-stijlen niet beschikbaar als standaard interpolaties zoals ze zijn voor [KeyframeSequences](/docs/nl-nl/reference/engine/classes/KeyframeSequence) . Echter, wanneer je een [KeyframeSequence](/docs/nl-nl/reference/engine/classes/KeyframeSequence)  naar een curve-animatie converteert, voegt Studio automatisch extra keyframes toe aan je animatie om de animatie intact te houden, en je kunt twee of meer keyframes selecteren en een interpolatiecurve  genereren die een aantal van hun tussenliggende keyframes verwijdert en vervangt om bounce- en elastische easing-gedrag na te bootsen.

Om interpolatiecurven te genereren:

1.

Selecteer twee of meer keyframes. Elk keyframe dat je selecteert wordt gemarkeerd.

2.

Klik met de rechtermuisknop op een van deze keyframes. Een contextmenu wordt weergegeven.

3.

Beweeg de muis over Genereer Curve , vervolgens over Bounce  of Elastic , en selecteer dan In , Out , of InOut . Een interpolatiecurve tussen je geselecteerde keyframes wordt gegenereerd volgens je instellingen.

-

In  — De beweging is langzamer aan het begin en sneller aan het einde van het keyframebereik.

-

Out  — De beweging is sneller aan het begin en langzamer aan het einde van het keyframebereik.

-

InOut  — In  en Out  op dezelfde tween, met In  aan het begin en Out  die halverwege het keyframebereik in werking treedt.

## [Volgorde van Euler-hoeken](#volgorde-van-euler-hoeken)[](#volgorde-van-euler-hoeken)

Wanneer je met Euler-hoeken werkt, vertegenwoordigt Studio de X , Y , en Z  assen door drie kanaalwaarden die een specifieke volgorde volgen om je rig van zijn startoriëntatie naar zijn volgende oriëntatie te verplaatsen. Elke volgorde is genoemd naar de [matrixvermenigvuldigingen](https://en.wikipedia.org/wiki/Matrix_multiplication)  om de uiteindelijke oriëntatie te krijgen. Bijvoorbeeld, een XYZ  volgorde (X × Y × Z ) betekent dat de rig begint te bewegen op de Z  as, dan de Y  as, en dan de X  as.

Hoe een animatie verandert wanneer je de volgorde van Euler-hoeken instelt, hangt af van wanneer  je de volgorde wijzigt:

-

Als je een [KeyframeSequence](/docs/nl-nl/reference/engine/classes/KeyframeSequence)  of een [CurveAnimation](/docs/nl-nl/reference/engine/classes/CurveAnimation)  met een ingesteld quaternion rotatietype laadt en vervolgens de volgorde wijzigt, heeft de nieuwe volgorde geen invloed op de animatie. Dit komt omdat Studio quaternions gebruikt om veranderingen in de oriëntatie van je rig te configureren met de kortste weg mogelijk tussen zijn startoriëntatie en zijn volgende oriëntatie. Deze methode heeft echter invloed op hoe de quaternions van elk keyframe transformeren in X , Y , en Z  hoeken in de tracklijst, wat visueel invloed kan hebben op de waarden binnen de tijdlijn zonder de animatie zelf te beïnvloeden.

-

Als je de volgorde van een bestaande Euler-hoek track wijzigt, kan de animatie veranderen, aangezien Studio de waarden van elk keyframe behoudt. Dit betekent dat het pad dat Studio volgt om de oriëntatie van je rig te veranderen van zijn startoriëntatie naar zijn volgende oriëntatie verandert met de volgorde van Euler-hoeken.

Om de volgorde van Euler-hoeken in te stellen:

1.

Klik in de rechterbovenhoek van het editorvenster op het instellingenpictogram. Een contextmenu wordt weergegeven.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/curve-editor/Timeline-Options-Menu.png)

2.

Beweeg de muis over Standaard Volgorde van Euler-hoeken , en selecteer vervolgens XYZ , XZY , YXZ , YZX , ZXY , of ZYX . Je volgorde van Euler-hoeken verandert dienovereenkomstig.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
