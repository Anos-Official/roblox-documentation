<!-- Source: https://create.roblox.com/docs/ui/rich-text -->

Rich text markup | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/ui/rich-text.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [User interface](/docs/ui)

# Rich text markup

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/ui/rich-text.md)

UI rich text  utilizes simple markup tags to style sections of a string in bold, italics, underline, fill color, stroke variations, and more. You can apply styling tags to [TextLabel](/docs/reference/engine/classes/TextLabel) , [TextButton](/docs/reference/engine/classes/TextButton) , and [TextBox](/docs/reference/engine/classes/TextBox)  objects.

## [Enable rich text](#enable-rich-text)[](#enable-rich-text)

You must enable rich text on a per-object basis through its RichText  property in the [Properties](/docs/studio/properties)  window, or by setting the property to true  in a [LocalScript](/docs/reference/engine/classes/LocalScript) .

 ![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Enable-Rich-Text.png)

```

local title = Instance.new("TextLabel")

title.RichText = true

title.Text = "Use a <b>bold title</b>"

```

When editing an object's Text  property in Studio, toggling the RichText  checkbox in the [Properties](/docs/studio/properties)  window displays the text string as a final render. This is useful for identifying and correcting mistakes in any [supported tags](#supported-tags) .

[Localizing](/docs/production/localization)  a game to support other languages removes rich text formatting tags. To ensure formatting appears in other languages, re-apply the tags manually to your localized strings.

## [Supported tags](#supported-tags)[](#supported-tags)

Rich text tags are similar to XML/HTML tags and you must include both an opening and closing tag around the formatted text.

<b>Formatted text</b>

You can also nest tags inside each other as long as you close them in the reverse order of how you opened them.

<b><i><u>Formatted text</u></i></b>

### [Font color](#font-color)[](#font-color)

<font color=""> </font>

I want the <font color="#FF7800">orange</font> candy.
 I want the <font color="rgb(255,125,0)">orange</font> candy.

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Color.png)

### [Font size](#font-size)[](#font-size)

<font size=""> </font>

<font size="40">This is big.</font> <font size="20">This is small.</font>

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Size.png)

### [Font face](#font-face)[](#font-face)

<font face=""> </font>

<font face="Michroma">This is Michroma face.</font>

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Font-Face.png)

Font face/family names are listed on the [Font](/docs/reference/engine/datatypes/Font)  enum reference page.

### [Font family](#font-family)[](#font-family)

<font family=""> </font>

<font family="rbxasset://fonts/families/Michroma.json">This is Michroma face.</font>

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Font-Face.png)

Font face/family names are listed on the [Font](/docs/reference/engine/datatypes/Font)  enum reference page.

### [Font weight](#font-weight)[](#font-weight)

<font weight=""> </font>

This is normal. <font weight="heavy">This is heavy.</font>
 This is normal. <font weight="900">This is heavy.</font>

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Weight.png)

Font weight can be a case-insensitive string name including Thin , ExtraLight , Light , Regular , Medium , SemiBold , Bold , ExtraBold , or Heavy ; it can also be a number in factors of 100 between 100  and 900 .

### [Font transparency](#font-transparency)[](#font-transparency)

<font transparency=""> </font>

Text at <font transparency="0.5">50% transparency</font>.

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Transparency.png)

### [Stroke](#stroke)[](#stroke)

<stroke> </stroke>

| Parameter | | Equivalent Property | | Example Values |
| --- | --- |
| color | | [UIStroke.Color](/docs/reference/engine/classes/UIStroke#Color) | | "rgb(255,125,0)" , "#FF7800" |
| thickness  or th | | [UIStroke.Thickness](/docs/reference/engine/classes/UIStroke#Thickness) | | "1" , "4" , "0.5" |
| transparency  or tr | | [UIStroke.Transparency](/docs/reference/engine/classes/UIStroke#Transparency) | | "0" , "0.5" , "1" |
| joins | | [UIStroke.LineJoinMode](/docs/reference/engine/classes/UIStroke#LineJoinMode) | | "round" , "bevel" , "miter" |
| sizing | | [UIStroke.StrokeSizingMode](/docs/reference/engine/classes/UIStroke#StrokeSizingMode) | | "fixed" , "scaled" |

You won <stroke color="#00A2FF" thickness="2" transparency="0.25" joins="miter">25 gems</stroke>.

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Stroke.png)

See [UI appearance modifiers](/docs/ui/appearance-modifiers#stroke)  for details on <stroke>  tag parameters such as thickness  and joins .

### [Bold](#bold)[](#bold)

<b> </b>

Text in <b>bold</b>.

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Bold.png)

### [Italic](#italic)[](#italic)

<i> </i>

Text <i>italicized</i>.

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Italic.png)

### [Underline](#underline)[](#underline)

<u> </u>

Text <u>underlined</u>.

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Underline.png)

### [Strikethrough](#strikethrough)[](#strikethrough)

<s> </s>

Text with <s>strikethrough</s> applied.

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Strikethrough.png)

### [Line break](#line-break)[](#line-break)

<br/>

New line occurs after this sentence.<br/>Next sentence...

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Line-Break.png)

### [Uppercase](#uppercase)[](#uppercase)

<uppercase> </uppercase>
<uc> </uc>

<uppercase>Uppercase</uppercase> makes words read loudly!
 <uc>Uppercase</uc> makes words read loudly!

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Uppercase.png)

### [Small caps](#small-caps)[](#small-caps)

<smallcaps> </smallcaps>
<sc> </sc>

My name is <smallcaps>Diva Dragonslayer</smallcaps>.
 My name is <sc>Diva Dragonslayer</sc>.

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Small-Caps.png)

### [Mark](#mark)[](#mark)

<mark> </mark>

Text <mark color="#009966" transparency="0">highlighted</mark>.

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Highlighted.png)

### [Comment](#comment)[](#comment)

<!-- -->

After this is a comment...<!--This does not appear in the final text--> and now more text...

![](https://prod.docsiteassets.roblox.com/assets/ui/rich-text/Example-Comment.png)

## [Escape forms](#escape-forms)[](#escape-forms)

If you want to render certain characters like <  or >  and exempt them from consideration as part of rich text tags, you can write them in their escape form .

| Character | | Escape | | Example | | Result |
| < | | &lt; | | 10 &lt; 100 | | 10 < 100 |
| > | | &gt; | | 100 &gt; 10 | | 100 > 10 |
| " | | &quot; | | Meet &quot;Diva Dragonslayer&quot; | | Meet "Diva Dragonslayer" |
| ' | | &apos; | | Diva&apos;s pet is a falcon! | | Diva's pet is a falcon! |
| & | | &amp; | | Render another escape form <b>&amp;lt;</b> by escaping an ampersand | | Render another escape form &lt;  by escaping an ampersand |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
