<!-- Source: https://create.roblox.com/docs/nl-nl/ui/rich-text -->

Rijke tekstopmaak | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Gebruikersinterface](/docs/nl-nl/ui)

# Rijke tekstopmaak

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

UI rijke tekst  maakt gebruik van eenvoudige opmaak-tags om secties van een string in vet, cursief, onderstreept, met vulkleur, variaties in omtrek en meer te stylen. Je kunt opmaak-tags toepassen op [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel) , [TextButton](/docs/nl-nl/reference/engine/classes/TextButton)  en [TextBox](/docs/nl-nl/reference/engine/classes/TextBox)  objecten.

## [Rijke tekst inschakelen](#rijke-tekst-inschakelen)[](#rijke-tekst-inschakelen)

Je moet rijke tekst inschakelen op objectbasis via de RichText  eigenschap in het [Eigenschappen](/docs/nl-nl/studio/properties)  venster, of door de eigenschap in te stellen op true  in een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript) .

 ![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Enable-Rich-Text.png)

```

local title = Instance.new("TextLabel")

title.RichText = true

title.Text = "Gebruik een <b>vetgedrukte titel</b>"

```

Wanneer je de Text  eigenschap van een object in Studio bewerkt, toont het in- en uitschakelen van het RichText  selectievakje in het [Eigenschappen](/docs/nl-nl/studio/properties)  venster de tekststring als een definitieve weergave. Dit is nuttig om fouten in eventuele [ondersteunde tags](#ondersteunde-tags)  te identificeren en te corrigeren.

[Lokaliseren](/docs/nl-nl/production/localization)  van een spel om andere talen te ondersteunen verwijdert opmaak-tags voor rijke tekst. Om ervoor te zorgen dat de opmaak in andere talen verschijnt, moet je de tags handmatig opnieuw toepassen op je gelokaliseerde strings.

## [Ondersteunde tags](#ondersteunde-tags)[](#ondersteunde-tags)

Rijke tekst-tags zijn vergelijkbaar met XML/HTML-tags en je moet zowel een openings- als een sluitingstag rond de opgemaakte tekst opnemen.

<b>Opgemaakte tekst</b>

Je kunt ook tags in elkaar nestelen zolang je ze in de omgekeerde volgorde sluit van hoe je ze hebt geopend.

<b><i><u>Opgemaakte tekst</u></i></b>

### [Letterkleur](#letterkleur)[](#letterkleur)

<font color=""> </font>

Ik wil de <font color="#FF7800">oranje</font> snoepjes.
 Ik wil de <font color="rgb(255,125,0)">oranje</font> snoepjes.

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Color.png)

### [Lettergrootte](#lettergrootte)[](#lettergrootte)

<font size=""> </font>

<font size="40">Dit is groot.</font> <font size="20">Dit is klein.</font>

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Size.png)

### [Lettertype](#lettertype)[](#lettertype)

<font face=""> </font>

<font face="Michroma">Dit is het Michroma-lettertype.</font>

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Font-Face.png)

Lettertype- en familienaam zijn vermeld op de [Font](/docs/nl-nl/reference/engine/datatypes/Font)  enum referentiepagina.

### [Letterfamilie](#letterfamilie)[](#letterfamilie)

<font family=""> </font>

<font family="rbxasset://fonts/families/Michroma.json">Dit is het Michroma-lettertype.</font>

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Font-Face.png)

Lettertype- en familienaam zijn vermeld op de [Font](/docs/nl-nl/reference/engine/datatypes/Font)  enum referentiepagina.

### [Lettergewicht](#lettergewicht)[](#lettergewicht)

<font weight=""> </font>

Dit is normaal. <font weight="heavy">Dit is zwaar.</font>
 Dit is normaal. <font weight="900">Dit is zwaar.</font>

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Weight.png)

Lettergewicht kan een niet-hoofdlettergevoelige stringnaam zijn, inclusief Thin , ExtraLight , Light , Regular , Medium , SemiBold , Bold , ExtraBold , of Heavy ; het kan ook een getal zijn in factoren van 100 tussen 100  en 900 .

### [Lettertransparantie](#lettertransparantie)[](#lettertransparantie)

<font transparency=""> </font>

Tekst met <font transparency="0.5">50% transparantie</font>.

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Transparency.png)

### [Omtrek](#omtrek)[](#omtrek)

<stroke> </stroke>

| Parameter | | Equivalent Eigenschap | | Voorbeeldwaarden |
| --- | --- |
| color | | [UIStroke.Color](/docs/nl-nl/reference/engine/classes/UIStroke#Color) | | "rgb(255,125,0)" , "#FF7800" |
| thickness  of th | | [UIStroke.Thickness](/docs/nl-nl/reference/engine/classes/UIStroke#Thickness) | | "1" , "4" , "0.5" |
| transparency  of tr | | [UIStroke.Transparency](/docs/nl-nl/reference/engine/classes/UIStroke#Transparency) | | "0" , "0.5" , "1" |
| joins | | [UIStroke.LineJoinMode](/docs/nl-nl/reference/engine/classes/UIStroke#LineJoinMode) | | "round" , "bevel" , "miter" |
| sizing | | [UIStroke.StrokeSizingMode](/docs/nl-nl/reference/engine/classes/UIStroke#StrokeSizingMode) | | "fixed" , "scaled" |

Je hebt <stroke color="#00A2FF" thickness="2" transparency="0.25" joins="miter">25 edelstenen</stroke> gewonnen.

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Stroke.png)

Zie [UI-uiterlijkmodificatoren](/docs/nl-nl/ui/appearance-modifiers#omtrek)  voor details over <stroke>  tagparameters zoals thickness  en joins .

### [Vet](#vet)[](#vet)

<b> </b>

Tekst in <b>vetgedrukt</b>.

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Bold.png)

### [Cursief](#cursief)[](#cursief)

<i> </i>

Tekst <i>cursief</i>.

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Italic.png)

### [Onderstreept](#onderstreept)[](#onderstreept)

<u> </u>

Tekst <u>onderstreept</u>.

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Underline.png)

### [Doorhalen](#doorhalen)[](#doorhalen)

<s> </s>

Tekst met <s>doorhaling</s> toegepast.

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Strikethrough.png)

### [Regelafbreking](#regelafbreking)[](#regelafbreking)

<br/>

Nieuwe regel komt na deze zin.<br/>Volgende zin...

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Line-Break.png)

### [Hoofdletters](#hoofdletters)[](#hoofdletters)

<uppercase> </uppercase>
<uc> </uc>

<uppercase>Hoofdletters</uppercase> maken woorden luid!
 <uc>Hoofdletters</uc> maken woorden luid!

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Uppercase.png)

### [Kleine hoofdletters](#kleine-hoofdletters)[](#kleine-hoofdletters)

<smallcaps> </smallcaps>
<sc> </sc>

Mijn naam is <smallcaps>Diva Dragonslayer</smallcaps>.
 Mijn naam is <sc>Diva Dragonslayer</sc>.

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Small-Caps.png)

### [Markeren](#markeren)[](#markeren)

<mark> </mark>

Tekst <mark color="#009966" transparency="0">gemarkeerd</mark>.

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Highlighted.png)

### [Opmerking](#opmerking)[](#opmerking)

<!-- -->

Na dit is een opmerking...<!--Dit verschijnt niet in de uiteindelijke tekst--> en nu meer tekst...

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Comment.png)

## [Escape-vormen](#escape-vormen)[](#escape-vormen)

Als je bepaalde tekens zoals <  of >  wilt weergeven en ze wilt uitsluiten van beschouwing als onderdeel van rijke tekst-tags, kun je ze in hun escape-vorm  schrijven.

| Tecken | | Escape | | Voorbeeld | | Resultaat |
| < | | &lt; | | 10 &lt; 100 | | 10 < 100 |
| > | | &gt; | | 100 &gt; 10 | | 100 > 10 |
| " | | &quot; | | Ontmoet &quot;Diva Dragonslayer&quot; | | Ontmoet "Diva Dragonslayer" |
| ' | | &apos; | | Diva&apos;s huisdier is een valk! | | Diva's huisdier is een valk! |
| & | | &amp; | | Render een andere escape-vorm <b>&amp;lt;</b> door een ampersand te escapen | | Render een andere escape-vorm &lt;  door een ampersand te escapen |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
