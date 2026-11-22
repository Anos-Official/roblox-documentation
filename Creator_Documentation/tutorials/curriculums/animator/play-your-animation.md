<!-- Source: https://create.roblox.com/docs/en-us/tutorials/curriculums/animator/play-your-animation -->

Play your animation | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/tutorials/curriculums/animator/play-your-animation.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Tutorials](/docs/en-us/tutorials)

# Play your animation

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/tutorials/curriculums/animator/play-your-animation.md)

In order to play your animation in your open game, as well as store it for reuse in other projects, you must publish the animation to the cloud. This process creates a unique animationID for your animation that you can reference in scripts, which is especially important if you want to replace any of Roblox's default character animations.

In this chapter, let's go over how to export your animation by publishing it to Roblox, then swap out the template's default walk animation with your own creation.

## [Export new animation](#export-new-animation)[](#export-new-animation)

If you were to close Studio right now, you would lose all of your work on your animation because your animation doesn't have an animationID  that Studio can reference for your projects. To fix this, you must export your animation to Roblox so that Studio can connect the animation to your account.

To export your new animation:

1.

In the Animation Editor , click on the ⋯  and select Publish to Roblox . The Asset Configuration  window displays.

 ![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-island-of-move/publish-animations/Publish-Highlight.png)

2.

In the Asset Configuration  window, give your animation a name and description, then click the Save  button. After a few moments, the window confirms your animation was successfully submitted.

3.

Copy your animation's animationID by clicking the icon next to the ID. A green "* ID Copied!* " text pop-up displays when you have done this step correctly.

 ![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-island-of-move/publish-animations/publish-copy-id.png)

4.

Click the Close  button.

## [Replace default animation](#replace-default-animation)[](#replace-default-animation)

Every player character includes a set of default animations  that play whenever the character performs specific in-game actions, such as running, climbing, or jumping. Roblox provides these animations out-of-the-box for every game without any additional coding effort.

Default Fall Animation

Default Swim Animation

Default Climb Animation

You can swap out default animations with your own custom animations so that they play for every player that joins your game. For this lesson, let's swap out the default walking animation with your swim animation so that you can see how it looks with your avatar as soon as you start playing.

To replace the default walking animation with your custom swimming animation:

1.

Find the default walk animation.

1.

In the Explorer  window, go to the search bar, then type walk .

2.

In your search results, click on WalkAnimationID .

 ![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-island-of-move/change-the-animation/search-walk-select.png)

If you don't see the Explorer  and Properties  windows, open them from Studio's Window  menu.

2.

In the Properties  window, click the Value  field and paste your animation ID by pressing Ctrl V  or ⌘ V , depending on your computer.

 ![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-island-of-move/change-the-animation/set-animation-value.png)

Need to Get the Animation ID?

 If your animationID didn't paste into the Value field, you need to get your animation's animationID again. To do this:

1.

Go to the [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

In the horizontal navigation, select Development Items , then click the Animations  button. All animations you have ever published display here.

 ![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-island-of-move/change-the-animation/Animations-Button.png)

3.

Select your animation. The animation's Configure  page displays.

4.

In the left-hand navigation, click the vertical three dots icon, then select Copy Asset ID  from the contextual menu.

 ![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-island-of-move/change-the-animation/CopyAssetID.png)

[Next](/docs/en-us/tutorials/curriculums/animator/test-and-save)[Previous](/docs/en-us/tutorials/curriculums/animator/work-with-the-animation-editor)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
