<!-- Source: https://create.roblox.com/docs/nl-nl/art/modeling/calisthenics-tool -->

Calisthenics Tool | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Meer informatie](/docs/nl-nl/learn)

# Calisthenics Tool

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Deze tool is niet langer in actieve ontwikkeling. Je bent vrij om de tool voor elk doel te gebruiken. De tool kan verouderd zijn of incompatibel met moderne Roblox-assets.

De Calisthenics Tool  is een aanvullende [Blender](https://www.blender.org/)  add-on die je in staat stelt om snel je asset te testen via een reeks animatiecycli om je skinninggegevens te verifiëren. Op elk moment tijdens het testen van de animatie kun je pauzeren en de skinning-tools van Blender gebruiken, zoals [Weight Painting brushes](https://docs.blender.org/manual/en/latest/sculpt_paint/weight_paint/introduction.html) , om eventuele skinningimperfecties op te lossen.

Het skinnen van je gelaagde accessoires en karakterlichamen is een cruciaal en vaak tijdrovend proces om hoogwaardige assets te creëren die bewegen en passen bij verschillende karakterlichamen. Net als de [Layered Accessory Validation Tool](/docs/nl-nl/art/accessories/validation-tool) , kan de Calisthenics Tool je tijd besparen bij het testen van je karaktermodellen na het riggen en skinnen.

De Calisthenics Tool biedt geen volledige verificatie van alle mogelijke skinningproblemen. Je moet er ook voor zorgen dat je aangepaste modellen voldoen aan de [specificaties voor karakterlichamen](/docs/nl-nl/avatar/character-bodies/specifications)  van Studio en aan eventuele toepasselijke [specificaties voor gelaagde accessoires](/docs/nl-nl/avatar/layered-accessories/specifications)  voor de beste resultaten in je game.

Loopanimatie

Renanimatie

Algemene bewegingen

## [Installatie](#installatie)[](#installatie)

De Calisthenics Tool-plugin is ontworpen voor [Blender 3.0+](https://www.blender.org/download/) . Je kunt de tool downloaden en aanpassen voor elk gebruik.

Om de Calisthenics Tool in Blender te installeren:

1.

Download de [CalisthenicsTool.zip](https://github.com/Roblox/avatar/tree/main/Tools/CalisthenicsTool)  en sla het .zip -bestand lokaal op.

2.

Ga in Blender naar Bewerken  > Voorkeuren .

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/calisthenic-tool/Blender-Preferences.png)

3.

Navigeer in de linkerzijbalk van het Voorkeuren -venster naar de sectie Add-Ons .

4.

Klik op de knop Installeren… . Een bestandsbrowser wordt weergegeven.

5.

Selecteer de .zip  en klik op Add-On installeren .

6.

Gebruik de zoekbalk om te zoeken naar "Calisthenics Tool" en selecteer de add-on.

7.

Schakel de add-on in door het vakje naast de naam van de add-on aan te vinken.

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/calisthenic-tool/Calisthenics-Tool-Addon.png)

8.

Sluit het Voorkeuren-venster. Je kunt nu toegang krijgen tot de Calisthenics Tool door de toolzijbalk in de Viewport uit te vouwen.

![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/calisthenic-tool/Toolbar-Slider.png) Gebruik de pijl aan de zijkant van de Viewport om de zijbalk te openen.

![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/calisthenic-tool/Calisthenics-Tool-Open.png) Toegang tot de Calisthenics Tool door het tabblad in het zijbalkmenu te selecteren.

## [Gebruik de Calisthenics Tool](#gebruik-de-calisthenics-tool)[](#gebruik-de-calisthenics-tool)

Na installatie kun je de Calisthenics Tool gebruiken wanneer je een [standaard R15](/docs/nl-nl/avatar/character-bodies/specifications#standaard-r15-rigs)  rigging armature met skinninggegevens wilt testen. Met de Calisthenics Tool kun je controleren hoe een karakterlichaam zou bewegen met algemene animaties, evenals referentierigide accessoires bevestigen om de bevestiging tijdens deze bewegingen te verifiëren. De tool bevat ook een optie om je karakter automatisch te exporteren, waarbij referentieanimatie- en accessoiregegevens worden verwijderd.

Je kunt de Calisthenics Tool uitproberen met een [voorbeeld karakterlichaam model](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/calisthenic-tool/Fish-Character-No-FACS.fbx) .

Voor demonstratiedoeleinden bevat dit referentiemodel geen FACS-gegevens. Als je een referentie met gezichtsanimatie nodig hebt, kun je hetzelfde model met FACS-gegevens downloaden van onze [referentiemodellen](/docs/nl-nl/avatar/character-bodies/specifications#reference-files) .

### [Test animaties](#test-animaties)[](#test-animaties)

Wanneer je je karakterlichaam model test, stel dan eerst de armature in de Calisthenics Tool in en selecteer vervolgens een van de referentieanimaties. Het is belangrijk om visueel je skinningkwaliteit te verifiëren met verschillende bewegingen en hoeken om de beste resultaten voor je model te garanderen.

Als je fouten of waarschuwingen tegenkomt bij het instellen van de armature of het afspelen van animaties, controleer dan of je model een geschikte botstructuur en naamgevingsconventie gebruikt zoals beschreven in Roblox's [vereisten voor aangepaste meshes](/docs/nl-nl/avatar/character-bodies/specifications) .

Om animaties te testen:

1.

Open een Blender-project met een bestaand karakterlichaam met een [standaard R15 rig](/docs/nl-nl/avatar/character-bodies/specifications#standaard-r15-rigs) , of importeer een geschikt karaktermodel .fbx  met Bestand  > Importeren  > FBX (.fbx) .

2.

Voor een gemakkelijkere visualisatie, verberg niet-gerenderde mesh-objecten, zoals armature, kooien en bijlagen om de referentieanimaties beter te kunnen bekijken.

3.

Stel in op welke rig je een referentieanimatie wilt testen:

1.

Selecteer in het Armature -veld van de add-on de Eyedropper.

2.

Selecteer in de Outliner het Armature -object dat de rig-gegevens van je karakter bevat.

4.

Klik op een animatiecyclus om een voorbeeld te bekijken, zoals Lopen , Rennen , Bewegen  of Stil .

5.

Druk op Stop Animatie  om de animatiegegevens te wissen.

6.

Als je onverwachte skinningdeformaties opmerkt, pauzeer dan op het frame en schakel over naar Weight Paint-modus  of gebruik de andere skinningtools van Blender om het op te lossen. Zie [Skin een humanoïde model](/docs/nl-nl/art/modeling/skin-a-humanoid-model)  voor aanvullende instructies.

### [Test accessoirebevestigingen](#test-accessoirebevestigingen)[](#test-accessoirebevestigingen)

Je kunt referentieaccessoires aan je karakterlichaam model toevoegen met de knoppen Attach Test Accessory . Deze testaccessoires helpen om te previewen hoe rigide accessoires aan je karakter worden bevestigd en hoe ze met je model kunnen bewegen. De tool bevat twee sets rigide accessoires die je op je karakter kunt toepassen.

![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/calisthenic-tool/Normal-Reference.png) Normale Grootte  - Laadt normale accessoire referenties.

![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/calisthenic-tool/Slender-Reference.png) Slanke Grootte  - Laadt slanke accessoire referenties.

Om accessoires te testen:

1.

Gebruik de volgende knoppen Attach Test Accessory  om voorbeeldaccessoires aan de bevestigingspunten van je karakter toe te voegen of te verwijderen:

-

Normale Grootte  - Voegt accessoires van normale schaal toe.

-

Slanke Grootte  - Voegt accessoires van slanke schaal toe.

-

Detach Test Accessories  - Verwijdert alle testaccessoires van je karakter.

2.

Als een accessoire niet op de verwachte locatie wordt bevestigd, verplaats dan het bijbehorende Attachment object  in de rigging armature van je karakter.

### [Exporteer modellen](#exporteer-modellen)[](#exporteer-modellen)

Wanneer je klaar bent om je model te exporteren, kun je je karakterlichaam rechtstreeks via de Calisthenics Tool exporteren. De tool wist automatisch alle testgegevens en past de juiste exportinstellingen toe.

Het gebruik van deze tool om modellen met [gezichtsanimaties](/docs/nl-nl/avatar/dynamic-heads)  te exporteren kan leiden tot onverwacht gedrag omdat de opgeslagen FACS-gegevens in conflict kunnen komen met de referentieanimaties van de tool.

Om te exporteren vanuit de Calisthenics Tool:

1.

Stel in het veld Export Pad  de exportdirectory in door op het mapicoon te klikken en naar de juiste bestandsdirectory te bladeren.

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/calisthenic-tool/Exporting-Model.png)

2.

Klik op de knop Exporteer Model . Het karaktermodel .fbx  wordt in de aangewezen map opgeslagen als Character_Model_Export.fbx .

Als je je model handmatig exporteert met Blender's .fbx -importeur in plaats van de Calisthenics Tool, zorg er dan voor dat je het volgende controleert voordat je exporteert:

-

Verwijder de testaccessoires van de Calisthenics Tool.

-

Gebruik de knop Stop Animatie  om testanimaties uit de tijdlijn te wissen.

-

Breng het model terug naar de standaardhouding zonder extra posegegevens.

-

Controleer of je instellingen voldoen aan Roblox's [Blender exportinstellingen](/docs/nl-nl/art/modeling/export-requirements) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
