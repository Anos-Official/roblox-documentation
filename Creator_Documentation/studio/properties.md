<!-- Source: https://create.roblox.com/docs/en-us/studio/properties -->

Properties window | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/studio/properties.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Studio](/docs/en-us/studio)

# Properties window

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/studio/properties.md)

The Properties  window, accessible from Studio's Window  menu or Home  tab toolbar, allows you to adjust certain properties of a selected object to change how the object looks and behaves. Additionally, you can manage [tags](#instance-tags)  and configure instance [attributes](#instance-attributes)  at the bottom of the window.

 ![Properties highlighted in Studio's toolbar.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Properties.png)

When you select an object, the window's header bar changes to reflect the object's class and name, and its properties are divided into sections. For example, a [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  includes sections like Appearance  and Transform  which respectively allow you to change its appearance and transform its [Size](/docs/en-us/reference/engine/classes/BasePart#Size) , [CFrame](/docs/en-us/reference/engine/classes/BasePart#CFrame) , and origin.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Sections-Example.png)

You can collapse or expand any section or subsection by clicking the small arrow to the left of its name. After you expand or collapse a section, it remains expanded or collapsed for other objects of the same class, as well as related objects that share the same property grouping.

Some properties are collapsed by default, but you can expand them by clicking the small arrow next to its name. For instance, [BaseParts](/docs/en-us/reference/engine/classes/BasePart)  contain a [Position](/docs/en-us/reference/engine/classes/BasePart#Position)  property which represents an X , Y , Z  coordinate in the 3D world. In Studio, these coordinates can be entered in two ways:

![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Input-Combined.png) All three coordinates typed into the parent Size  field, separated by commas

![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Input-Expanded.png) Property expanded and an individual size vector typed into the X , Y , and Z  fields

After you expand or collapse a property, it remains expanded or collapsed for other objects of the same class, as well as related objects that share the same property.

## [Property filter](#property-filter)[](#property-filter)

You can filter properties by typing a search query into the Filter Properties  input near the top of the window. For example, filtering by the letters "velo" finds all properties containing them, such as AssemblyLinear Velo city  and AssemblyAngular Velo city . Quickly access this input by pressing Ctrl Shift P  (Windows) or ⌘ Shift P  (Mac).

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Instance-Filtered.png)

## [Instance tags](#instance-tags)[](#instance-tags)

The Tags  section allows you to apply specific tags for use with [CollectionService](/docs/en-us/reference/engine/classes/CollectionService) . Tags are sets of strings applied to instances that replicate from the server to the client. They are also serialized when places are saved.

To add tags to an instance through the Properties  window:

1.

Select the instance, scroll to the Tags  section, and click the +  button.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Add-Tag-Button.png)

2.

In the popup window, enter a new tag name or  select a tag you've already created for any other instance from the list below the input field. The tag will appear within the Tags  section.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Set-Tag.png)

3.

If necessary, you can remove an existing tag by clicking the ×  icon.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Remove-Tag-Button.png)

## [Instance attributes](#instance-attributes)[](#instance-attributes)

Attributes  allow you to customize instances with your own data. They are similar to built-in object properties, but you can create and modify your own attributes for any instance. Key features include:

-

Attributes can be created, edited, and deleted directly within Studio or through scripting (see [properties and attributes](/docs/en-us/scripting/attributes)  for script commands to create, set, get, and delete attributes).

-

Attributes and their values are saved with your place and assets.

-

Value changes can be viewed in real time and are replicated  so that clients can access them immediately.

You can store the following types/values in attributes:

-

[string](/docs/en-us/luau/strings)

-

[boolean](/docs/en-us/luau/booleans)

-

[number](/docs/en-us/luau/numbers)

-

[UDim](/docs/en-us/reference/engine/datatypes/UDim)

-

[UDim2](/docs/en-us/reference/engine/datatypes/UDim2)

-

[BrickColor](/docs/en-us/reference/engine/datatypes/BrickColor)

-

[Color3](/docs/en-us/reference/engine/datatypes/Color3)

-

[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

-

[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

-

[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

-

[NumberSequence](/docs/en-us/reference/engine/datatypes/NumberSequence)

-

[ColorSequence](/docs/en-us/reference/engine/datatypes/ColorSequence)

-

[NumberRange](/docs/en-us/reference/engine/datatypes/NumberRange)

-

[Rect](/docs/en-us/reference/engine/datatypes/Rect)

-

[Font](/docs/en-us/reference/engine/datatypes/Font)

New attributes can be created and modified in Studio as follows:

1.

Select the instance, scroll to the Attributes  section, and click the +  button.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Add-Attribute-Button.png)

2.

In the popup window, enter the attribute Name , select its Type , and click Save .

3.

The new attribute will appear with a default value that you can change just like any other property.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Set-Attribute.png)

4.

If necessary, you can rename or delete an attribute by clicking the gear icon.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Rename-Delete-Attribute-Button.png)

## [Configurable defaults](#configurable-defaults)[](#configurable-defaults)

The configurable defaults  feature allows you to save properties from a selected [Instance](/docs/en-us/reference/engine/classes/Instance)  as the new default for that type, reset them as needed, and share them from a local file if desired. Use cases include:

-

A default [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  instance where [Anchored](/docs/en-us/reference/engine/classes/BasePart#Anchored)  is true , so that every new [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  inserted into the 3D workspace is anchored.

-

A set of default [mechanical constraints](/docs/en-us/physics/mechanical-constraints)  with physical behaviors that match the type of mechanisms you're currently building, such as massive vehicles vs. smaller machines with less mass.

-

A set of default [light](/docs/en-us/effects/light-sources)  sources ([PointLight](/docs/en-us/reference/engine/classes/PointLight) , [SpotLight](/docs/en-us/reference/engine/classes/SpotLight) , [SurfaceLight](/docs/en-us/reference/engine/classes/SurfaceLight) ), each with [Brightness](/docs/en-us/reference/engine/classes/Light#Brightness)  that suits the environment you're designing.

To set  a specific instance as the default:

1.

Select the instance in the 3D viewport or [Explorer](/docs/en-us/studio/explorer)  hierarchy.

2.

From Studio's main Edit  menu, select Save as Default [Instance] . A toast notification will indicate that the default has been updated, and newly inserted instances of that type will match the default properties.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Default-Properties-Toast.jpg)

Instance defaults are saved locally  on each machine to a DefaultInstances.rbxm  file, not to your Roblox or group account. The location of this directory can be changed in Studio's settings (Alt S  or ⌥ S ) under the Studio  tab ⟩ Instance Defaults Dir .

To reset  a configurable default instance:

1.

Select any instance of that type in the 3D viewport or [Explorer](/docs/en-us/studio/explorer)  hierarchy.

2.

From Studio's main Edit  menu, select Reset Default [Instance] . Existing instances of that type will retain their properties, but newly inserted instances will use Studio's default properties.

Note the following exceptions and behavioral rules to default instances:

-

The positional  instance properties [BasePart.Position](/docs/en-us/reference/engine/classes/BasePart#Position) , [BasePart.CFrame](/docs/en-us/reference/engine/classes/BasePart#CFrame) , [PVInstance.Origin](/docs/en-us/reference/engine/classes/PVInstance#Origin) , and [Model.WorldPivot](/docs/en-us/reference/engine/classes/Model#WorldPivot)  are not  affected by default properties, but rather are overridden by Studio insertion rules and workflows. However, [GuiObject.Position](/docs/en-us/reference/engine/classes/GuiObject#Position)  and positional properties for [Attachments](/docs/en-us/reference/engine/classes/Attachment)  ([Position](/docs/en-us/reference/engine/classes/Attachment#Position) , [WorldCFrame](/docs/en-us/reference/engine/classes/Attachment#WorldCFrame) , [WorldPosition](/docs/en-us/reference/engine/classes/Attachment#WorldPosition) ) are stored/maintained in configured defaults of those instance types.

-

Studio's Group as Model  (Ctrl G  or ⌘ G ) and Group as Folder  (Ctrl Alt G  or ⌘ ⌥ G ) actions do not  use the instance defaults for [Model](/docs/en-us/reference/engine/classes/Model)  or [Folder](/docs/en-us/reference/engine/classes/Folder) , respectively.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
