<!-- Source: https://create.roblox.com/docs/resources/the-mystery-of-duvall-drive/immersive-narrative -->

Immersive narrative | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/resources/the-mystery-of-duvall-drive/immersive-narrative.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Samples and projects](/docs/en-us/samples)
4. /
5. [The Mystery of Duvall Drive](/docs/resources/the-mystery-of-duvall-drive)

# Immersive narrative

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/resources/the-mystery-of-duvall-drive/immersive-narrative.md)

Like the [Beyond the Dark](/docs/resources/beyond-the-dark)  demo, one of our earliest decisions was to have as much of the gameplay and story told diegetically within the world itself. This can be a difficult process when you want to balance both communicating progress to the player through the user interface while also making them feel as though they really are within the world you've built. To meet these goals for our game, we broke the way we communicate information to players down into four techniques:

1.

Visual cues  - Objects, images, or arrangement of assets that passively reinforce story or give hints to the player when it makes sense for the world.

2.

Lore  - When a player clicks/taps on specific items in the house, important story information displays on the entire screen . This narrative is only visible to the player that clicked/tapped the object. The tone is always informational in tone and phrasing.

3.

Thought bubbles  - When a player clicks/taps on specific items in the house, a text dialogue "reaction" displays near the object . This narrative is only visible to the player that clicked/tapped the object. The tone is always first person and observational.

4.

Announcements  - When a player clicks/taps on a corrupted item in the house, third-person dialogue displays on every player's screen at once . This narrative sometimes transitions all players to the corrupted state of the room they are in.

In this section, we will demonstrate how we used these techniques and specific features to immerse players into our narrative while still encouraging exploration, communicating progress, and keeping gameplay both intimate to the individual player and fair in a multiplayer game.

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/overview-visual-cues.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/overview-announcement.png) An announcement on-screen overlay of the character's internal thoughts.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/overview-thought-bubble.png) A thought bubble, or object-specific dialogue, that displays when you select certain objects.

## [Visual cues](#visual-cues)[](#visual-cues)

A visual cue is an important tool to both reinforce narrative and tell players what they need to know about their objective without using words . Using an arrangement of assets, such as chalkboards, statues, and wallpaper, we were able to passively provide a depth of information about the main characters of Duvall Drive, as well as guidance on how to complete puzzles without having to include invasive UI elements. We began this process by first figuring out what we wanted to communicate to the player, then how it would make sense to communicate that within the world of our game. For example, we wanted players to understand how obsessed the grandfather was in his mission to defy death, so we left his room in disarray with a lot of his research and several walls with his scribbled thoughts.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/grandfather-room.png) Scribbles throughout the grandfather's room communicate the grandfather's compulsive nature.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/dog-statue.png) An abundance of sculptures and reference photos demonstrate how the daughter is an artist.

Our first rule was that if we wanted to use a visual cue to teach players something, it must have a reason to exist even if players aren't present. If we put a giant sign with clear instructions of what to do for a puzzle, this would seem out of place within the house. However, if we established a grandfather that is consumed with drawing on everything, including the walls of his bedroom, it is much more believable to have a chalkboard with his plan scribbled out for the player to follow.

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/chalkboard.png)

Our second rule was that we don't always need to tell players what to do or how to solve puzzles because they are insightful to their environment. For example, sometimes a fallen power line in a pool of water is enough of a visual cue to communicate that players are in danger of being electrified if they continue moving in that direction.

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/power-line.png)

## [Lore](#lore)[](#lore)

In addition to using visual cues to passively guide players, we also chose to display important story information about the family on the entire screen  as a precursor to start the room's puzzle whenever a player clicked or tapped on specific items in the house. To guide players to the objects they needed to select in order for lore to display, we used the new highlight visual effect to make specific objects stand out from their surroundings. This effect allows you to either outline and/or overlay objects with a specific color that fits to the shape of the object itself, and choose whether other objects can hide the highlight if they are closer to the camera.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/lore-1.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/lore-2.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/lore-3.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/lore-4.png)

We initially used [Highlight](/docs/reference/engine/classes/Highlight)  for every object a player could interact with, but the visual noise was overwhelming and players wouldn't clearly know what to interact with to read the lore. We decided to only use it to highlight items that were either corrupted or dangerous, and this visual feedback allowed players to easily drive the story forward.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/dog-statue-lore.png) Fun fact: we originally had lore on everything you could click on! This wasn't helpful because players weren't sure what information was important and what was just for flavor. Eventually we removed much of the lore and used visual cues to leave the rest of the narrative to the player's imagination.

After the player clicked on the object with the lore, we needed a way to display the information on top of the screen. We decided to create an overlay by using a [ScreenGui](/docs/reference/engine/classes/ScreenGui)  as our on-screen UI container with a child [Frame](/docs/reference/engine/classes/Frame)  to control the sizing and rescaling of its children [TextLabels](/docs/reference/engine/classes/TextLabel)  and [ImageLabels](/docs/reference/engine/classes/ImageLabel) . We set the positions and scale of the [TextLabels](/docs/reference/engine/classes/TextLabel)  and [ImageLabels](/docs/reference/engine/classes/ImageLabel)  properties so they fit visually together and would scale for different devices players use to access the game.

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/jacob-photo-album.png)

[TextLabels](/docs/reference/engine/classes/TextLabel)  and [ImageLabels](/docs/reference/engine/classes/ImageLabel)  affect visual elements of their respective text and images, including their color, transparency, size, and arrangement. For [TextLabels](/docs/reference/engine/classes/TextLabel)  specifically, you can adjust their [TextLabel.TextScaled](/docs/reference/engine/classes/TextLabel#TextScaled)  and [TextLabel.RichText](/docs/reference/engine/classes/TextLabel#RichText)  properties to control the layout and visual styling of text. [TextLabel.TextScaled](/docs/reference/engine/classes/TextLabel#TextScaled)  allows you to scale text to fill the entire parent UI element's space, and [TextLabel.RichText](/docs/reference/engine/classes/TextLabel#RichText)  allows you to use simple markup tags to style sections of text in bold, italics, color, or even different fonts.

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/lore-template.png)

We knew that players would be accessing this game from a variety of devices, including PC, console, and mobile devices, and they would need to be able to either click or tap the screen to interact with the game. We didn't want a bunch of buttons on the screen to distract from the narrative, so we made an invisible back button the size of the entire screen so that players could either click or tap anywhere on the lore overlay to close the content and get back to gameplay.

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/overlay-back-button.png)

## [Thought bubbles](#thought-bubbles)[](#thought-bubbles)

We needed a way for the player's character to communicate ideas to the player, such as providing additional narrative flavor or reinforcing what they needed to do. Our solution was to display thought bubbles, or text reactions from the player's character , near non-lore objects whenever the player selected them. This narrative only displays to the player that clicked or tapped the object, and the tone is always first person and observational.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/barn-owl-thought-bubbles.png) A relatively simple yet powerful system to have the world react to the player's interactions!

To create thought bubbles, we parented a [BillboardGui](/docs/reference/engine/classes/BillboardGui)  with a child [TextLabel](/docs/reference/engine/classes/TextLabel)  to non-lore objects. This allowed us to display dialogue in the 3D space near the object without the text taking up the entirety of the screen. Similar to our process in creating lore, we used the [TextLabel.RichText](/docs/reference/engine/classes/TextLabel#RichText)  property to style the text and add visual effects like another otherworldly being interrupting the player's own thoughts. The following is an example of RichText HTML used to make the image below.

"What is…this…<br/><stroke color="#dcc7ff" joins="miter" thickness="2" transparency="0.5"><font size="60"><font color="rgb(10,8,11)"><i>....hunger….void….pull…</i></font></font></stroke>

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/richtext-thought-bubble.png)

By using [TextLabels](/docs/reference/engine/classes/TextLabel)  instead of images, we kept the text readable by Roblox, and we were able to auto-localize this content and make it accessible to many more players without having to do anything! For more information on this process, see [automatic translations](/docs/production/localization/automatic-translations) .

## [Announcements](#announcements)[](#announcements)

While we wanted the player's character to have reactions to the world, we also wanted the world itself to react to their presence. To meet this goal, we included announcements, or third-person dialogue, that displays on every player's screen at once . Similar to lore, we created announcements by using a [ScreenGui](/docs/reference/engine/classes/ScreenGui)  as our on-screen UI container with a child [TextLabel](/docs/reference/engine/classes/TextLabel) . We also used the [TextLabel.RichText](/docs/reference/engine/classes/TextLabel#RichText)  property to change the dialogue's color, font, and size to help convey different "entities" talking to the players in the house.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/announcements-white.png) Announcements with plain white text were the player's character reaction that was general to an area, not an object like the lore narrative technique.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/announcements-purple.png) Announcements with purple text were the reaction from a corrupt entity.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/announcements-yellow.png) Announcements with yellow text were the reaction from a restored entity.

By using the [TextLabel.RichText](/docs/reference/engine/classes/TextLabel#RichText)  property and providing some HTML commands in it to drive changes, we were also allowed to make changes mid-sentence! For example, the following rich text markup allowed us to interrupt the player character's reaction by the corrupt entity's thoughts:

What is…this…<br/><stroke color="#dcc7ff" joins="miter" thickness="2" transparency="0.5"><font size="60"><font color="rgb(10,8,11)"><i>....hunger….void….pull…</i></font></font></stroke>

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/announcements-interrupt.png)

We had several of these types of announcements, either triggered by invisible part volumes that players walked into, or by completing certain goals. To avoid dozens of individual [ScreenGuis](/docs/reference/engine/classes/ScreenGui) , we used a separate script in the demo that allowed us to provide the text that the script would then add to a single object we named StoryNote  in our [PlayerGui](/docs/reference/engine/classes/PlayerGui)  folder. This object was a single [ScreenGui](/docs/reference/engine/classes/ScreenGui)  with a child [TextLabel](/docs/reference/engine/classes/TextLabel) . Using scripting, we could inject whatever phrases we wanted directly into the single [TextLabel](/docs/reference/engine/classes/TextLabel) , which made it a lot easier to make changes as we figured out how and what we wanted to communicate to the player!

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/storynote-object.png) StoryNote was an object we called for any instances that triggered it via script. Those same scripts provided the text and formatting we wanted for each event.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/example-script.png) Example of a script calling that object and defining the text, per event.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/blank-textlabel.png) The TextLabel was actually blank, and using scripts we injected the RichText as needed to the same object.

[Next](/docs/resources/the-mystery-of-duvall-drive/stream-in-immersion)[Previous](/docs/resources/the-mystery-of-duvall-drive/materialize-the-world)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
