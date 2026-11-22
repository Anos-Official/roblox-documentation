<!-- Source: https://create.roblox.com/docs/nl-nl/projects/rojo/partially-managed -->

Gedeeltelijk beheerd Rojo | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Projecten](/docs/nl-nl/projects)
6. /
7. [Op bestanden gebaseerde workflows](/docs/nl-nl/projects/file-based-workflows)
8. /
9. [Rojo](/docs/nl-nl/projects/rojo)

# Gedeeltelijk beheerd Rojo

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een teamworkflow voor Roblox-projecten die de code in Git houdt, de kunst versieert met pakketten, en iedereen laat werken zonder elkaars wijzigingen te overschrijven.

## [De korte versie](#de-korte-versie)[](#de-korte-versie)

-

Code  leeft in Git en komt in Studio via [Rojo](https://rojo.space) .

-

Kunst  leeft in Roblox als [pakketten](https://create.roblox.com/docs/projects/assets/packages) . De originelen bevinden zich in een Asset-plaats , en kopieën in de Dev-plaats worden automatisch bijgewerkt.

-

Iedereen werkt in zijn eigen User-plaats , en brengt vervolgens het voltooide werk naar de gedeelde Dev-plaats .

-

Stable  is een bevroren momentopname van Dev voor playtests. Prod  is het live spel.

## [Plaatsen](#plaatsen)[](#plaatsen)

Alle plaatsen zijn eigendom van de project groep . Controleer altijd of de groep is geselecteerd voordat je op Publiceren als  klikt.

| Plaats | | Doel | | Wie verandert het | | Hoe | | Naam |
| --- | --- |
| User | | Jouw persoonlijke dagelijkse werkruimte, gekopieerd van Dev | | Jij | | Rojo connect + Studio | | USER / [Naam] - [Project] - [Niveau] |
| Dev | | Gedeelde, onstabiele combinatie van ieders werk | | Iedereen, na beoordeling | | Rojo connect voor code, [Team Create](https://create.roblox.com/docs/projects/collaboration)  voor kunst | | DEV - [Project] |
| Asset | | De originele pakketten: personages, bouwkits, set dressing | | Artiesten | | Bewerken + Publiceren naar Pakket | | ASSET / [Project] - [Niveau] |
| Stable | | Bevroren momentopname van Dev, gebruikt voor playtests | | Alleen het deploy-script | | Geautomatiseerd | | STABLE / [Project] |
| Prod | | Het publieke spel | | Release-eigenaar, met goedkeuring | | Gekopieerd van Stable | | [Project] |

## [Waar dingen naartoe gaan](#waar-dingen-naartoe-gaan)[](#waar-dingen-naartoe-gaan)

Rojo is ingesteld als gedeeltelijk beheerd : Git bezit de code en configuratie, en het plaatsbestand bezit de kunst en het niveau. Elke runtime-locatie (ReplicatedStorage , ServerScriptService ) heeft twee inhoudsmapen:

| Wat | | Waar | | Bron van waarheid |
| Code (systemen, bibliotheken) | | src/…  in de repo | | Git |
| Getypte configuratie en definities (items, quests, geluiden, mechanismen) | | src/…/ManagedContent/ | | Git |
| Kunst en alles met MeshParts | | …/Content , als pakketten | | Het plaatsbestand en de Asset-plaats |
| Niveau-indeling, verlichting, terrein | | Workspace / Lighting in de Dev-plaats | | Het plaatsbestand |

### [ManagedContent: Git is de bron van waarheid](#managedcontent-git-is-de-bron-van-waarheid)[](#managedcontent-git-is-de-bron-van-waarheid)

-

Rojo bouwt het opnieuw vanaf de schijf, dus Studio-bewerkingen worden overschreven  bij de volgende synchronisatie. Bewerk de bestanden op de schijf.

-

Bestanden zijn .luau  modules, .model.json  beschrijvingen, of .rbxmx  instanties.

-

Om iets dat je in Studio hebt gebouwd naar ManagedContent te verplaatsen:

-

Klik met de rechtermuisknop en kies Opslaan als Bestand  → .rbxmx . Het XML-formaat geeft leesbare verschillen, in tegenstelling tot de binaire .rbxm .

-

Plaats het bestand onder ManagedContent/ , en commit het.

-

Gebruik het voor  alles wat code leest als configuratie. Codebeoordeling en Git-geschiedenis dekken het dan.

### [Inhoud: het plaatsbestand is de bron van waarheid](#inhoud-het-plaatsbestand-is-de-bron-van-waarheid)[](#inhoud-het-plaatsbestand-is-de-bron-van-waarheid)

-

Rojo negeert het, en het heeft geen bestanden op de schijf, dus de autocomplete van de editor kan het niet zien.

-

Het is vereist voor MeshParts , omdat Rojo ze niet kan synchroniseren.

-

Gebruik het voor  kunst die artiesten in Studio bewerken: props, personages, VFX, staging.

-

Plaats hier nooit code-beheerde configuratie.  Het wordt onzichtbaar voor beoordeling en verschillen.

-

De enige geschiedenis is de plaatsversiegeschiedenis van Roblox , dus publiceer Dev regelmatig.

### [Projectbestand](#projectbestand)[](#projectbestand)

Vertel Rojo om Content  met rust te laten met [$ignoreUnknownInstances](https://rojo.space/docs/v7/project-format/) :

```

"ReplicatedStorage": {

  "$path": "src/ReplicatedStorage",

  "Content": {

    "$className": "Folder",

    "$ignoreUnknownInstances": true

  }

}

```

Repo-indeling:

```

src/

├── ReplicatedStorage/       # gedeeld + client

│   ├── Systems/

│   ├── Libraries/

│   └── ManagedContent/

└── ServerScriptService/     # alleen server, niet gerepliceerd

    ├── Systems/

    ├── Libraries/

    └── ManagedContent/

```

## [Setup (een keer per project)](#setup-een-keer-per-project)[](#setup-een-keer-per-project)

1.

Clone de repo  en installeer de toolchain. We gebruiken [Rokit](https://github.com/rojo-rbx/rokit) : voer rokit install  uit om rojo, selene, StyLua, luau-lsp en lune te krijgen.

2.

Maak je User-plaats:

-

Open de Dev-plaats.

-

Kies Bestand → Publiceren als , selecteer de projectgroep, en maak een nieuwe plaats genaamd USER / [Naam] - [Project] - [Niveau] .

-

Sluit Dev en open je nieuwe plaats.

3.

Verbind Rojo:

-

Open de repo in je editor en voer rojo serve  uit.

-

Klik in Studio op Verbinden  in de Rojo-plugin.

Je User-plaats is een kopie van Dev, zodat de pakketten gekoppeld blijven. Ze worden bijgewerkt naar de nieuwste versie elke keer dat je de plaats opent.

## [Ingenieurs: de codecyclus](#ingenieurs-de-codecyclus)[](#ingenieurs-de-codecyclus)

1.

Maak een branch van main .

2.

Werk je User-plaats  bij vanuit Dev, zodat je begint met de nieuwste indeling en kunst:

-

Open de Dev-plaats.

-

Kies Bestand → Publiceren als , selecteer de projectgroep, en kies je bestaande User-plaats om deze te overschrijven.

3.

Werk in je User-plaats  met rojo serve  verbonden.

4.

Voer stylua  (opmaak) en selene  (linting) uit voordat je een PR opent.

5.

Open een PR en laat deze beoordelen.

6.

Zodra het is goedgekeurd, merge naar main .

7.

Synchroniseer Dev:

-

Voer git checkout main && git pull  uit.

-

Open de Dev-plaats , voer rojo serve  uit en verbind.

-

Als je wijziging lay-outwijzigingen in de plaats vereist, zoals nieuwe attributen of tijdelijke activa, voeg ze dan ook toe aan Dev. Rojo synchroniseert alleen code en ManagedContent, dus het brengt ze niet over.

Bewerk nooit handmatig een door Rojo beheerd script of ManagedContent in Studio. De volgende synchronisatie wist het.

## [Artiesten: de activacylus](#artiesten-de-activacylus)[](#artiesten-de-activacylus)

### [Een bestaand activum wijzigen](#een-bestaand-activum-wijzigen)[](#een-bestaand-activum-wijzigen)

1.

Open de Asset-plaats  en bewerk het originele pakket.

2.

Klik met de rechtermuisknop en kies Publiceren naar Pakket .

3.

De kopieën in Dev nemen de wijziging over:

-

Kopieën met AutoUpdate aan worden bijgewerkt de volgende keer dat iemand Dev opent.

-

Als Dev al open is, klik met de rechtermuisknop op een kopie en kies Krijg Laatste Pakket . Je kunt ook Update Alles  gebruiken om elke plaats in het spel bij te werken.

4.

Optioneel, voeg een versieopmerking toe onder Pakketdetails → Versies .

### [Een nieuw activum toevoegen](#een-nieuw-activum-toevoegen)[](#een-nieuw-activum-toevoegen)

1.

Bouw het in de Asset-plaats. Groepeer het als een Model , zelfs als het een enkel object is, zodat je later kinderen kunt toevoegen zonder het pakket te breken.

2.

Klik met de rechtermuisknop en kies Converteren naar Pakket .

-

Stel Eigendom in op de projectgroep . Eigendom kan later niet worden overgedragen.

3.

Selecteer zijn PackageLink  en zet AutoUpdate  aan.

4.

Voeg het toe aan Dev: ga in de [Toolbox](https://create.roblox.com/docs/projects/assets/toolbox)  naar Creations → Groep Pakketten , voeg het in en plaats het in de Workspace of Content .

### [Indeling en niveau werk](#indeling-en-niveau-werk)[](#indeling-en-niveau-werk)

-

Rangschik dingen in je User-plaats.

-

Zodra je leidinggevende goedkeurt, kopieer je de wijzigingen naar Dev. Gebruik Team Create in Dev voor gedeelde indelingsrondes.

### [Pakketregels](#pakketregels)[](#pakketregels)

-

Bewerk alleen pakketten in de Asset-plaats.  Als je een kopie in Dev bewerkt, wordt deze gemarkeerd als gewijzigd en stopt met automatisch bijwerken. Om een onbedoelde bewerking te herstellen, klik met de rechtermuisknop en kies Herstel Wijzigingen naar Pakket .

-

Verwijder of verplaats nooit een PackageLink .  Dit verandert de kopie terug in een gewoon model.

-

Geneste pakketten:  publiceer eerst het binnenste pakket, dan het buitenste.

-

Terugrollen:  ga naar Pakketdetails → Versies , kies een eerdere versie en klik op Indienen.

-

Versies vergelijken:  klik met de rechtermuisknop op het pakket en kies Pakketopties → Vergelijk Pakketversies .

-

AutoUpdate is standaard uit.  Zet AutoUpdate  aan op de PackageLink  van een kopie om deze automatisch bij te werken, of laat het uit om de kopie handmatig bij te werken.

-

Toegang:  deel pakketten met de groep zodat het hele team ze kan gebruiken en bewerken. Zie [Asset privacy](https://create.roblox.com/docs/projects/assets/privacy) .

## [Releases: Dev → Stable → Prod](#releases-dev--stable--prod)[](#releases-dev--stable--prod)

### [Dev → Stable (deploy-script)](#dev--stable-deploy-script)[](#dev--stable-deploy-script)

Schrijf een klein deploy-script; [Lune](https://lune-org.github.io/docs)  werkt hier goed voor. Voer het uit op een schema of voor elke playtest. Het moet:

1.

Download de huidige Dev-plaats , zodat deze de Content, Workspace en verlichting bevat.

2.

Verwijder elke PackageLink .  De pakketten worden gewone modellen, zodat Stable bevroren is en niet verandert wanneer artiesten nieuwe pakketversies publiceren.

3.

Publiceer het resultaat naar de Stable-plaats  met de [Open Cloud plaats publicatie-API](https://create.roblox.com/docs/cloud/guides/usage-place-publishing) . Je hebt een API-sleutel nodig met de assets  toestemming en Lezen  en Schrijven  toegang, plus de plaats-ID.

Testers krijgen een stabiele build terwijl het team blijft werken in Dev. Niemand bewerkt Stable handmatig.

### [Stable → Prod](#stable--prod)[](#stable--prod)

De release-eigenaar kopieert Stable naar Prod, en alleen met goedkeuring. Prod is live, dus niemand anders raakt het aan.

## [Communicatie](#communicatie)[](#communicatie)

Geef elk project een algemeen kanaal, een engineeringkanaal (PR-links, technische discussie) en een kunstkanaal (WIPs, beoordelingen).

## [Referentie](#referentie)[](#referentie)

-

[Pakketten](https://create.roblox.com/docs/projects/assets/packages)

-

[Asset privacy](https://create.roblox.com/docs/projects/assets/privacy)

-

[Samenwerking en Team Create](https://create.roblox.com/docs/projects/collaboration)

-

[Open Cloud plaats publicatie](https://create.roblox.com/docs/cloud/guides/usage-place-publishing)

-

[Rojo projectformaat](https://rojo.space/docs/v7/project-format/)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
