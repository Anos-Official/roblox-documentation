<!-- Source: https://create.roblox.com/docs/nl-nl/ui/in-experience-containers -->

In-game UI-containers | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Gebruikersinterface](/docs/nl-nl/ui)

# In-game UI-containers

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

In-game UI-containers houden [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  vast die je binnen de 3D-wereld van je game wilt weergeven.

-

Een [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui)  maakt het mogelijk om UI-objecten op het oppervlak van een onderdeel in de 3D-wereld weer te geven, terwijl ook basisgebruikersinteractie mogelijk is.

-

Een [BillboardGui](/docs/nl-nl/reference/engine/classes/BillboardGui)  is een container voor UI-objecten die in de 3D-ruimte verschijnen, maar altijd naar de camera zijn gericht.

## [Oppervlakte UI](#oppervlakte-ui)[](#oppervlakte-ui)

Vergelijkbaar met [Decals](/docs/nl-nl/reference/engine/classes/Decal)  en [Textures](/docs/nl-nl/reference/engine/classes/Texture) , zijn UI-objecten zoals [TextLabels](/docs/nl-nl/reference/engine/classes/TextLabel)  en [ImageLabels](/docs/nl-nl/reference/engine/classes/ImageLabel)  die aan een [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui)  zijn gekoppeld, gericht in dezelfde richting als het oppervlak waarop ze zich bevinden, bewerkbaar via de [SurfaceGui.Face](/docs/nl-nl/reference/engine/classes/SurfaceGui#Face) -eigenschap.

 ![SurfaceGui op een 3D-onderdeel in de plaats met een ImageLabel-kind om een schermconsole weer te geven.](https://prod.docsiteassets.roblox.com/assets/ui/in-experience/SurfaceGui-Diagram.jpg)

Om een [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui)  toe te passen op een in-game [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) , koppel je het eenvoudig aan dat onderdeel en stel je de [SurfaceGui.Face](/docs/nl-nl/reference/engine/classes/SurfaceGui#Face) -eigenschap in. Kind UI-objecten verschijnen dan op dat vlak van het bovenliggende onderdeel.

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Part-SurfaceGui-ImageLabel.png)

![](https://prod.docsiteassets.roblox.com/assets/studio/properties/SurfaceGui-Face-Top.png)

Alternatief kun je de [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui)  in een container zoals [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui)  plaatsen en vervolgens de [Adornee](/docs/nl-nl/reference/engine/classes/SurfaceGui#Adornee) -eigenschap instellen op een willekeurige [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) , evenals de doel [Face](/docs/nl-nl/reference/engine/classes/SurfaceGui#Face) . Het instellen van [Adornee](/docs/nl-nl/reference/engine/classes/SurfaceGui#Adornee)  overschrijft de directe ouderrelatie, waardoor er meer flexibiliteit in plaatsing is, aangezien het vanuit een script tijdens runtime kan worden ingesteld.

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/StarterGui-SurfaceGui.png)

![](https://prod.docsiteassets.roblox.com/assets/studio/properties/SurfaceGui-Adornee-Face.png)

Interactieve UI-elementen zoals [ImageButtons](/docs/nl-nl/reference/engine/classes/ImageButton)  en [TextButtons](/docs/nl-nl/reference/engine/classes/TextButton)  binnen een [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui)  ontvangen alleen gebruikersinvoer als ze zijn gekoppeld aan de [PlayerGui](/docs/nl-nl/reference/engine/classes/PlayerGui)  van de speler, meestal door de [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui)  in [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui)  te plaatsen zoals hierboven opgemerkt. Bovendien moet de [CanQuery](/docs/nl-nl/reference/engine/classes/BasePart#CanQuery) -eigenschap van het onderdeel true  zijn, zodat het interactieve UI-element invoer kan ontvangen.

Om te helpen bij het kiezen van het juiste vlak voor een [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui) , klik met de rechtermuisknop op het doelonderdeel en selecteer Toon Oriëntatie Indicator . Dit toont een blauwe cirkel met een F  en een lijn die aan de [Front](/docs/nl-nl/reference/engine/enums/NormalId#Front) -zijde van het object is bevestigd, en een groene pijl die in de richting van de [Top](/docs/nl-nl/reference/engine/enums/NormalId#Top) -zijde van het object wijst.

### [Grootte en positie](#grootte-en-positie)[](#grootte-en-positie)

Het "canvas" van een [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui)  beslaat het volledige [Face](/docs/nl-nl/reference/engine/classes/SurfaceGui#Face)  van het bovenliggende of [Adornee](/docs/nl-nl/reference/engine/classes/SurfaceGui#Adornee) -onderdeel. Als beste praktijk wordt aanbevolen om schaal  waarden te gebruiken voor de [grootte](/docs/nl-nl/ui/position-and-size#grootte)  en [positie](/docs/nl-nl/ui/position-and-size#positie)  van kind UI-objecten zoals [ImageLabels](/docs/nl-nl/reference/engine/classes/ImageLabel) . Je kunt ook een [UIAspectRatioConstraint](/docs/nl-nl/reference/engine/classes/UIAspectRatioConstraint)  toepassen op kinderen van de [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui)  om hun gewenste beeldverhouding te behouden, ongeacht de grootte van het vlak.

### [Occlusiemodus](#occlusiemodus)[](#occlusiemodus)

De [AlwaysOnTop](/docs/nl-nl/reference/engine/classes/SurfaceGui#AlwaysOnTop) -eigenschap bepaalt of de [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui)  bovenop 3D-inhoud wordt weergegeven of door deze wordt occludeerd. Wanneer ingesteld op false  (standaard), wordt de [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui)  weergegeven zoals andere 3D-inhoud en wordt deze occludeerd door andere 3D-objecten. Wanneer ingesteld op true , wordt deze altijd bovenop 3D-inhoud weergegeven en wordt deze niet beïnvloed door [helderheid/licht](#helderheid-en-lichtinvloed)  in de 3D-omgeving.

### [Helderheid en lichtinvloed](#helderheid-en-lichtinvloed)[](#helderheid-en-lichtinvloed)

[Brightness](/docs/nl-nl/reference/engine/classes/SurfaceGui#Brightness)  en [LightInfluence](/docs/nl-nl/reference/engine/classes/SurfaceGui#LightInfluence)  werken samen om te bepalen hoe omgevingslicht de UI-inhoud van de [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui)  beïnvloedt.

[Brightness](/docs/nl-nl/reference/engine/classes/SurfaceGui#Brightness)  bepaalt de factor waarmee uitgezonden licht wordt geschaald in een bereik van 0  tot 1000 , zodat je de [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui)  kunt afstemmen op zijn omgeving. Bijvoorbeeld, een videobillboard kan worden verhelderd in een donkere kamer door [Brightness](/docs/nl-nl/reference/engine/classes/SurfaceGui#Brightness)  in te stellen op 10 .

[LightInfluence](/docs/nl-nl/reference/engine/classes/SurfaceGui#LightInfluence)  controleert hoeveel de [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui)  wordt beïnvloed door verlichting in de plaats, in een bereik van 0  tot 1 . Dit op 1  instellen betekent dat omringende verlichting volledige controle heeft over het uiterlijk, terwijl het instellen op 0  betekent dat de verlichting geen effect heeft.

Helderheid = 0 Helderheid = 10

![](https://prod.docsiteassets.roblox.com/assets/ui/in-experience/SurfaceGui-Brightness-0.jpg)

Let op dat [Brightness](/docs/nl-nl/reference/engine/classes/SurfaceGui#Brightness)  niet toegankelijk is in Studio en geen effect heeft wanneer [LightInfluence](/docs/nl-nl/reference/engine/classes/SurfaceGui#LightInfluence)  1  is of [AlwaysOnTop](/docs/nl-nl/reference/engine/classes/SurfaceGui#AlwaysOnTop)  true  is.

### [Afstandszichtbaarheid](#afstandszichtbaarheid)[](#afstandszichtbaarheid)

[MaxDistance](/docs/nl-nl/reference/engine/classes/SurfaceGui#MaxDistance)  controleert hoe ver van de camera de [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui)  wordt weergegeven voordat deze stopt met renderen. Een waarde van 0  betekent dat er geen limiet is en dat deze oneindig ver weg zal renderen. De standaardwaarde van 1000  werkt goed voor de meeste gevallen.

Voor [SurfaceGuis](/docs/nl-nl/reference/engine/classes/SurfaceGui)  die buiten verschijnen, wordt aanbevolen dat [MaxDistance](/docs/nl-nl/reference/engine/classes/SurfaceGui#MaxDistance)  hoog genoeg is om ervoor te zorgen dat de UI van de container voldoende klein op het scherm is wanneer deze verschijnt of verdwijnt, waardoor het plotselinge pop-in/out-effect wordt geminimaliseerd.

### [Weergavevolgorde](#weergavevolgorde)[](#weergavevolgorde)

Als er meerdere [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui) -containers op hetzelfde vlak bestaan, kun je ze stapelen op basis van de Z-index via hun [ZOffset](/docs/nl-nl/reference/engine/classes/SurfaceGui#ZOffset) -eigenschap (het wijzigen hiervan "tilt" of "sink" de container visueel niet van het oppervlak).

## [Billboard UI](#billboard-ui)[](#billboard-ui)

De [BillboardGui](/docs/nl-nl/reference/engine/classes/BillboardGui) -container toont UI-objecten in de 3D-ruimte, maar in tegenstelling tot [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui)  zijn kinderen van een [BillboardGui](/docs/nl-nl/reference/engine/classes/BillboardGui)  altijd naar de camera gericht. Deze container is nuttig voor het weergeven van frontale informatie boven in-game objecten zoals gezondheidsmeters of namen boven spelerspersonages, markeringen om spelers naar een object in de 3D-wereld te leiden, en meer.

 ![BillboardGui met een TextLabel die de schermconsole beschrijft waarboven het zweeft.](https://prod.docsiteassets.roblox.com/assets/ui/in-experience/BillboardGui-Diagram.jpg)

Om een [BillboardGui](/docs/nl-nl/reference/engine/classes/BillboardGui)  te koppelen aan een in-game [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  of [Attachment](/docs/nl-nl/reference/engine/classes/Attachment) , koppel je het eenvoudig aan dat onderdeel of die bevestiging en, indien gewenst, pas je de [grootte/positie](#grootte-en-positie-1)  aan.

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Part-BillboardGui-ImageLabel.png)

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Part-Attachment-BillboardGui-ImageLabel.png)

Alternatief kun je de [BillboardGui](/docs/nl-nl/reference/engine/classes/BillboardGui)  in een container zoals [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui)  plaatsen en vervolgens de [Adornee](/docs/nl-nl/reference/engine/classes/BillboardGui#Adornee) -eigenschap instellen op een willekeurige [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  of [Attachment](/docs/nl-nl/reference/engine/classes/Attachment) . Deze methode biedt meer flexibiliteit in plaatsing, aangezien [Adornee](/docs/nl-nl/reference/engine/classes/BillboardGui#Adornee)  vanuit een script tijdens runtime kan worden ingesteld, bijvoorbeeld om een [BillboardGui](/docs/nl-nl/reference/engine/classes/BillboardGui)  boven het hoofd van spelerspersonages te plaatsen tijdens runtime.

Interactieve UI-elementen zoals [ImageButtons](/docs/nl-nl/reference/engine/classes/ImageButton)  en [TextButtons](/docs/nl-nl/reference/engine/classes/TextButton)  binnen een [BillboardGui](/docs/nl-nl/reference/engine/classes/BillboardGui)  ontvangen alleen gebruikersinvoer als ze zijn gekoppeld aan de [PlayerGui](/docs/nl-nl/reference/engine/classes/PlayerGui)  van de speler, meestal door de [BillboardGui](/docs/nl-nl/reference/engine/classes/BillboardGui)  in [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui)  te plaatsen zoals hierboven opgemerkt.

### [Grootte en positie](#grootte-en-positie-1)[](#grootte-en-positie-1)

Voor de grootte van de billboard stellen de [schaal](/docs/nl-nl/ui/position-and-size#grootte)  componenten van de [Size](/docs/nl-nl/reference/engine/classes/BillboardGui#Size) -eigenschap de studgrootte van de billboard in de 3D-ruimte in. Bijvoorbeeld, een instelling van {10, 0},{2, 0}  ([UDim2.fromScale(10, 2)](/docs/nl-nl/reference/engine/datatypes/UDim2#fromScale) )  vormt een billboard met een 10:2 beeldverhouding die groter of kleiner schaalt, afhankelijk van de afstand tot de camera.

Voor positionering verschuift de [StudsOffset](/docs/nl-nl/reference/engine/classes/BillboardGui#StudsOffset) -eigenschap het billboardcanvas op de X -as (links/rechts), Y -as (omhoog/omlaag) en Z -as (vooruit/achteruit) ten opzichte van de camera.

Bij het maken van een grootte-schaal [BillboardGui](/docs/nl-nl/reference/engine/classes/BillboardGui)  die een [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel)  bevat, is het nuttig om de [TextScaled](/docs/nl-nl/reference/engine/classes/TextLabel#TextScaled) -eigenschap van het label in te schakelen, zodat de tekst samen met het billboardcanvas schaalt naarmate de afstand tot de camera verandert.

### [Occlusiemodus](#occlusiemodus-1)[](#occlusiemodus-1)

De [AlwaysOnTop](/docs/nl-nl/reference/engine/classes/BillboardGui#AlwaysOnTop) -eigenschap bepaalt of de [BillboardGui](/docs/nl-nl/reference/engine/classes/BillboardGui)  bovenop 3D-inhoud wordt weergegeven of door deze wordt occludeerd. Wanneer ingesteld op false  (standaard), wordt de [BillboardGui](/docs/nl-nl/reference/engine/classes/BillboardGui)  weergegeven zoals andere 3D-inhoud en wordt deze occludeerd door andere 3D-objecten. Wanneer ingesteld op true , wordt deze altijd bovenop 3D-inhoud weergegeven en wordt deze niet beïnvloed door [helderheid/licht](#helderheid-en-lichtinvloed-1)  in de 3D-omgeving.

### [Helderheid en lichtinvloed](#helderheid-en-lichtinvloed-1)[](#helderheid-en-lichtinvloed-1)

[Brightness](/docs/nl-nl/reference/engine/classes/BillboardGui#Brightness)  en [LightInfluence](/docs/nl-nl/reference/engine/classes/BillboardGui#LightInfluence)  werken samen om te bepalen hoe omgevingslicht de UI-inhoud van de [BillboardGui](/docs/nl-nl/reference/engine/classes/BillboardGui)  beïnvloedt.

[Brightness](/docs/nl-nl/reference/engine/classes/BillboardGui#Brightness)  bepaalt de factor waarmee uitgezonden licht wordt geschaald in een bereik van 0  tot 1000 , zodat je de [BillboardGui](/docs/nl-nl/reference/engine/classes/BillboardGui)  kunt afstemmen op zijn omgeving. Bijvoorbeeld, een videobillboard kan worden verhelderd in een donkere kamer door [Brightness](/docs/nl-nl/reference/engine/classes/BillboardGui#Brightness)  in te stellen op 10 .

[LightInfluence](/docs/nl-nl/reference/engine/classes/BillboardGui#LightInfluence)  controleert hoeveel de [BillboardGui](/docs/nl-nl/reference/engine/classes/BillboardGui)  wordt beïnvloed door verlichting in de plaats, in een bereik van 0  tot 1 . Dit op 1  instellen betekent dat omringende verlichting volledige controle heeft over het uiterlijk, terwijl het instellen op 0  betekent dat de verlichting geen effect heeft.

LightInfluence = 1 LightInfluence = 0

![](https://prod.docsiteassets.roblox.com/assets/ui/in-experience/BillboardGui-LightInfluence-1.jpg)

Let op dat [Brightness](/docs/nl-nl/reference/engine/classes/BillboardGui#Brightness)  niet toegankelijk is in Studio en geen effect heeft wanneer [LightInfluence](/docs/nl-nl/reference/engine/classes/BillboardGui#LightInfluence)  1  is of [AlwaysOnTop](/docs/nl-nl/reference/engine/classes/BillboardGui#AlwaysOnTop)  true  is.

### [Afstandszichtbaarheid](#afstandszichtbaarheid-1)[](#afstandszichtbaarheid-1)

[MaxDistance](/docs/nl-nl/reference/engine/classes/BillboardGui#MaxDistance)  controleert hoe ver van de camera de [BillboardGui](/docs/nl-nl/reference/engine/classes/BillboardGui)  wordt weergegeven voordat deze stopt met renderen. Een waarde van 0  of inf  (standaard) betekent dat er geen limiet is en dat deze oneindig ver weg zal renderen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
