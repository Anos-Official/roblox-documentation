<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/libraries/table -->

table | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Bibliotheken](/docs/nl-nl/reference/engine/libraries)
2. /
3. [table](/docs/nl-nl/reference/engine/libraries/table)

Nederlands

Feedback

Engine-bibliotheek

table

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/libraries/table)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Functies

|

[clear](#clear) (table :  [table](/docs/nl-nl/luau/tables) ) : ()

 |
| --- | --- |
|

[clone](#clone) (t :  [table](/docs/nl-nl/luau/tables) ) :[table](/docs/nl-nl/luau/tables)

 |
|

[concat](#concat) (t :  [{any}](/docs/nl-nl/luau/tables#arrays) , sep :  [string](/docs/nl-nl/luau/strings) , i :  [number](/docs/nl-nl/luau/numbers) , j :  [number](/docs/nl-nl/luau/numbers) ) :[string](/docs/nl-nl/luau/strings)

 |
|

[create](#create) (count :  [number](/docs/nl-nl/luau/numbers) , value :  Variant ) :[table](/docs/nl-nl/luau/tables)

 |
|

[find](#find) (haystack :  [table](/docs/nl-nl/luau/tables) , needle :  Variant , init :  [number](/docs/nl-nl/luau/numbers) ) : Variant

 |
|

[foreach](#foreach) (t :  [table](/docs/nl-nl/luau/tables) , f :  [function](/docs/nl-nl/luau/functions) ) : ()

Verouderd

 |
|

[foreachi](#foreachi) (t :  [{any}](/docs/nl-nl/luau/tables#arrays) , f :  [function](/docs/nl-nl/luau/functions) ) : ()

Verouderd

 |
|

[freeze](#freeze) (t :  [table](/docs/nl-nl/luau/tables) ) :[table](/docs/nl-nl/luau/tables)

 |
|

[getn](#getn) (t :  [{any}](/docs/nl-nl/luau/tables#arrays) ) :[number](/docs/nl-nl/luau/numbers)

Verouderd

 |
|

[insert](#insert) (t :  [{any}](/docs/nl-nl/luau/tables#arrays) , pos :  [number](/docs/nl-nl/luau/numbers) , value :  Variant ) : ()

 |
|

[insert](#insert-t-value) (t :  [{any}](/docs/nl-nl/luau/tables#arrays) , value :  Variant ) : ()

 |
|

[isfrozen](#isfrozen) (t :  [table](/docs/nl-nl/luau/tables) ) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[maxn](#maxn) (t :  [table](/docs/nl-nl/luau/tables) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[move](#move) (src :  [table](/docs/nl-nl/luau/tables) , a :  [number](/docs/nl-nl/luau/numbers) , b :  [number](/docs/nl-nl/luau/numbers) , t :  [number](/docs/nl-nl/luau/numbers) , dst :  [table](/docs/nl-nl/luau/tables) ) :[table](/docs/nl-nl/luau/tables)

 |
|

[pack](#pack) (values... :  Variant ) :[table](/docs/nl-nl/luau/tables)

 |
|

[remove](#remove) (t :  [{any}](/docs/nl-nl/luau/tables#arrays) , pos :  [number](/docs/nl-nl/luau/numbers) ) : Variant

 |
|

[sort](#sort) (t :  [{any}](/docs/nl-nl/luau/tables#arrays) , comp :  [function](/docs/nl-nl/luau/functions) ) : ()

 |
|

[unpack](#unpack) (list :  [table](/docs/nl-nl/luau/tables) , i :  [number](/docs/nl-nl/luau/numbers) , j :  [number](/docs/nl-nl/luau/numbers) ) :[Tuple](/docs/nl-nl/luau/tuples)

 |

---

API-referentie

Functies

clear

table.clear (table :[table](/docs/nl-nl/luau/tables) ) : ()

Parameters

|

table :[table](/docs/nl-nl/luau/tables)

 |

Teruggaves

()

Codevoorbeelden

##### Tafel Leegmaken

Feedback geven

---

clone

table.clone (t :[table](/docs/nl-nl/luau/tables) ) :[table](/docs/nl-nl/luau/tables)

Parameters

|

t :[table](/docs/nl-nl/luau/tables)

 |

Teruggaves

[table](/docs/nl-nl/luau/tables)

Codevoorbeelden

##### Tabel Klonen

Feedback geven

---

concat

table.concat (

t :[{any}](/docs/nl-nl/luau/tables#arrays) , sep :[string](/docs/nl-nl/luau/strings) , i :[number](/docs/nl-nl/luau/numbers) , j :[number](/docs/nl-nl/luau/numbers)

) :[string](/docs/nl-nl/luau/strings)

Parameters

|

t :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

sep :[string](/docs/nl-nl/luau/strings)

 |
|

i :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 1 |
|

j :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[string](/docs/nl-nl/luau/strings)

Codevoorbeelden

##### Tabel Samenvoegen

Feedback geven

---

create

table.create (

count :[number](/docs/nl-nl/luau/numbers) , value : Variant

) :[table](/docs/nl-nl/luau/tables)

Parameters

|

count :[number](/docs/nl-nl/luau/numbers)

 |
|

value : Variant

 |

Teruggaves

[table](/docs/nl-nl/luau/tables)

Codevoorbeelden

##### Tabel Aanmaken

Feedback geven

---

find

table.find (

haystack :[table](/docs/nl-nl/luau/tables) , needle : Variant , init :[number](/docs/nl-nl/luau/numbers)

) : Variant

Parameters

|

haystack :[table](/docs/nl-nl/luau/tables)

 |
|

needle : Variant

 |
|

init :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

Variant

Codevoorbeelden

##### Tabel Vinden

Feedback geven

---

foreach

Verouderd

Details weergeven

---

foreachi

Verouderd

Details weergeven

---

freeze

table.freeze (t :[table](/docs/nl-nl/luau/tables) ) :[table](/docs/nl-nl/luau/tables)

Parameters

|

t :[table](/docs/nl-nl/luau/tables)

 |

Teruggaves

[table](/docs/nl-nl/luau/tables)

Codevoorbeelden

##### Tafel Bevriezen

Feedback geven

---

getn

Verouderd

Details weergeven

---

insert

table.insert (

t :[{any}](/docs/nl-nl/luau/tables#arrays) , pos :[number](/docs/nl-nl/luau/numbers) , value : Variant

) : ()

Parameters

|

t :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

pos :[number](/docs/nl-nl/luau/numbers)

 |
|

value : Variant

 |

Teruggaves

()

Codevoorbeelden

##### Tabel Invoegen Op Positie

Feedback geven

---

insert

table.insert (

t :[{any}](/docs/nl-nl/luau/tables#arrays) , value : Variant

) : ()

Parameters

|

t :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

value : Variant

 |

Teruggaves

()

Codevoorbeelden

##### Tabel Invoegen Toevoegen

Feedback geven

---

isfrozen

table.isfrozen (t :[table](/docs/nl-nl/luau/tables) ) :[boolean](/docs/nl-nl/luau/booleans)

Parameters

|

t :[table](/docs/nl-nl/luau/tables)

 |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

##### Tabel Isbevroren

Feedback geven

---

maxn

table.maxn (t :[table](/docs/nl-nl/luau/tables) ) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

t :[table](/docs/nl-nl/luau/tables)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

##### Tabel Maxn

Feedback geven

---

move

table.move (

src :[table](/docs/nl-nl/luau/tables) , a :[number](/docs/nl-nl/luau/numbers) , b :[number](/docs/nl-nl/luau/numbers) , t :[number](/docs/nl-nl/luau/numbers) , dst :[table](/docs/nl-nl/luau/tables)

) :[table](/docs/nl-nl/luau/tables)

Parameters

|

src :[table](/docs/nl-nl/luau/tables)

 |
|

a :[number](/docs/nl-nl/luau/numbers)

 |
|

b :[number](/docs/nl-nl/luau/numbers)

 |
|

t :[number](/docs/nl-nl/luau/numbers)

 |
|

dst :[table](/docs/nl-nl/luau/tables)

Standaardwaarde: src |

Teruggaves

[table](/docs/nl-nl/luau/tables)

Codevoorbeelden

##### Tafel Verplaatsen

Feedback geven

---

pack

table.pack (values... : Variant ) :[table](/docs/nl-nl/luau/tables)

Parameters

|

values... : Variant

 |

Teruggaves

[table](/docs/nl-nl/luau/tables)

Codevoorbeelden

##### Tafelpakket

Feedback geven

---

remove

table.remove (

t :[{any}](/docs/nl-nl/luau/tables#arrays) , pos :[number](/docs/nl-nl/luau/numbers)

) : Variant

Parameters

|

t :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

pos :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

Variant

Codevoorbeelden

##### Tabel Verwijderen

Feedback geven

---

sort

table.sort (

t :[{any}](/docs/nl-nl/luau/tables#arrays) , comp :[function](/docs/nl-nl/luau/functions)

) : ()

Parameters

|

t :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

comp :[function](/docs/nl-nl/luau/functions)

Standaardwaarde: nil |

Teruggaves

()

Codevoorbeelden

##### Tabel Sorteren

Feedback geven

---

unpack

table.unpack (

list :[table](/docs/nl-nl/luau/tables) , i :[number](/docs/nl-nl/luau/numbers) , j :[number](/docs/nl-nl/luau/numbers)

) :[Tuple](/docs/nl-nl/luau/tuples)

Parameters

|

list :[table](/docs/nl-nl/luau/tables)

 |
|

i :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 1 |
|

j :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: #list |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Codevoorbeelden

##### Tabel Uitpakken

Feedback geven

---

Ga naar

▼

table

[Samenvatting](#summary)

[Functies](#summary-functions)

[Functies](#functions)

[clear()](#clear)

[clone()](#clone)

[concat()](#concat)

[create()](#create)

[find()](#find)

[foreach()](#foreach)

[foreachi()](#foreachi)

[freeze()](#freeze)

[getn()](#getn)

[insert()](#insert)

[isfrozen()](#isfrozen)

[maxn()](#maxn)

[move()](#move)

[pack()](#pack)

[remove()](#remove)

[sort()](#sort)

[unpack()](#unpack)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
