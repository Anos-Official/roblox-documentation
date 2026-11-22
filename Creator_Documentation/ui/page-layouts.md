<!-- Source: https://create.roblox.com/docs/en-us/ui/page-layouts -->

Page layouts | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/ui/page-layouts.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [User interface](/docs/en-us/ui)
6. /
7. Layout structures

# Page layouts

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/ui/page-layouts.md)

When you parent a [UIPageLayout](/docs/en-us/reference/engine/classes/UIPageLayout)  to a UI container, every sibling [GuiObject](/docs/en-us/reference/engine/classes/GuiObject)  becomes a unique page that you can transition to through scripting. This layout is useful when you want to create user interfaces such as tabbed modals, tutorials, or character customization screens.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/UIPageLayout.png)

After you create multiple pages within the [UIPageLayout](/docs/en-us/reference/engine/classes/UIPageLayout) , you need to use scripting to transition from page to page. For example, the following code, pasted into a client‑side sibling [Script](/docs/en-us/reference/engine/classes/Script)  of the layout, transitions forward and then backward between the pages every two seconds.

```

local frame = script.Parent

local pageLayout = frame:FindFirstChildWhichIsA("UIPageLayout")

task.wait(2)

pageLayout:Next()

task.wait(2)

pageLayout:Next()

task.wait(2)

pageLayout:Previous()

task.wait(2)

pageLayout:Previous()

```

If you want to view pages while editing in Studio, you can use the [Command Bar](/docs/en-us/studio/overview#command-bar)  to navigate from one page to another, letting you review where you need to make changes without having to play your game each time.

1.

In the [Explorer](/docs/en-us/studio/explorer)  window hierarchy, select the [UIPageLayout](/docs/en-us/reference/engine/classes/UIPageLayout)  object.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/UIPageLayout.png)

2.

Open the [Command Bar](/docs/en-us/studio/overview#command-bar) .

3.

Input any of the following commands and press Enter .

| Action | | Command |
| --- | --- |
| Next Page | | game:GetService("Selection"):Get()[1]:Next() |
| Previous Page | | game:GetService("Selection"):Get()[1]:Previous() |
| First Page | | game:GetService("Selection"):Get()[1]:JumpToIndex(0) |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
