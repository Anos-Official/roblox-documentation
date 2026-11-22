<!-- Source: https://create.roblox.com/docs/en-us/learn/more/rounded-corners -->

What it takes to round a corner | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/learn/more/rounded-corners.md | Documentation index: https://create.roblox.com/docs/llms.txt

Learn

![A tilted sword shop menu with rounded corners, a soft drop shadow, and an orange-to-purple gradient header, floating over a blurred game world.](https://prod.docsiteassets.roblox.com/assets/resources/rounded-corners/cover-finale.jpg)

# What it takes to round a corner

A shadow, a rounded menu, a gradient across a header. These are the kinds of details nobody thinks twice about... until someone has to teach a game engine how to draw them.

[

Play on Roblox](https://www.roblox.com/games/start?placeId=107426260461768)[

View the code](https://github.com/Roblox/resources/tree/main/experiences/rounded-corners)

## In this article

1. [Chapter 01 · Shadows Building a native drop shadow](#shadows)
2. [Chapter 02 · Gradients Gradients beyond the straight line](#gradients)
3. [Chapter 03 · Clipping Clipping to a curve](#clipping)

Picture this: you're making a shop menu for your Roblox game. There's a sword for sale. You sketch a panel that floats over the action, give it rounded corners and a soft shadow, and let the item cards scroll neatly under the curved edges. A gradient gives the header a little personality.

It's a perfectly ordinary menu, the kind you could mock up in Figma before lunch or put together on the web with a handful of CSS properties. Roblox, though, has to draw it while your friends are running around behind it setting things on fire, and it has to work on everything from a gaming PC to a phone with a cracked screen.

The rounded corners themselves are easy enough to draw, but keeping those scrolling item cards inside them is harder than it looks. The GPU's simplest clipping tool can cut off anything outside a rectangle, but it doesn't understand rounded corners. The shadow has to follow the frame whenever you change its shape, and the gradient has to behave when you rotate it.

These are the sorts of problems that have been keeping the Capabilities pod busy. The small team, led by engineering manager Chase Ruppert ([@DrRanchDressing](https://www.roblox.com/users/1298953044/profile) ), is part of Roblox's Digital Matter group. In August 2025, principal engineer Jonah Williams ([@jaydubs808](https://www.roblox.com/users/8302270184/profile) ) put together a proposal to fill in some of the missing pieces of Roblox's UI toolkit, from native shadows and new gradients to more flexible shapes and better clipping. That proposal has helped guide the team's work over the past year.

Jonah thinks of these effects as part of the "grammar" of 2D UI. Once you've learned to use rounded corners, shadows, and gradients in one place, you expect those same building blocks to be available elsewhere. And when one is missing, you notice.

Chapter 01  · Shadows

## Building a native drop shadow

A shadow built from the frame, instead of a picture tucked behind it.

Roblox creators have been asking for native drop shadows for more than a decade. In a 2015 DevForum post, a developer described having to upload custom shadow images or use nine-slice frames just to get the effect they wanted. The classic workaround was to paint a shadow in Photoshop, export it as a PNG, and tuck the image behind a frame. Another option involved stacking translucent [UIStroke](/docs/en-us/reference/engine/classes/UIStroke)  outlines, each a little bigger and fainter than the last, until the whole pile looked like a shadow as long as you didn't stare at it too hard.

Both could look convincing, although they came with some annoying limitations. An 800-by-800-pixel PNG, for instance, can take up roughly 2.5 megabytes of uncompressed runtime memory, which is quite a lot to spend on a gray smudge. Scaling or compressing the image to save space could introduce banding or artifacts. Unlike the frame itself, the image also couldn't automatically adapt to changes in its shape. Animate the frame's corner radius, and the shadow would keep its original outline, like a sticker. Stacked strokes fared a little better, since they could grow along with the frame, but they kept whatever corner radius they were drawn with.

The engine wasn't any wiser. As far as the renderer could tell, that smudge was just another image, no different from an icon or a picture of somebody's dog. It had no way of knowing the image was supposed to be a shadow, so it couldn't take advantage of rendering techniques designed specifically for that effect.

What the team wanted, and what senior software engineer [@luigiburger333](https://www.roblox.com/users/4541804944/profile)  helped build, was a shadow that actually belonged to the frame, one that could change whenever the frame changed without making the graphics card work overtime to keep up.

The conventional way to produce a soft shadow is to blur the shape casting it. A * Gaussian blur*  spreads opacity across the surrounding pixels according to a bell-shaped curve: the farther you get from the shape, the fainter the shadow becomes. Make the curve wider and the shadow gets softer. The results look great, but a full image blur involves sampling neighboring pixels, which can become expensive when you're drawing lots of UI elements that move and change.

There's a strange detail buried in the Gaussian curve, too. Mathematically, it never quite reaches zero. It just keeps getting closer, forever. So the shadow under your sword shop is, strictly speaking, still heading for the edge of the universe, and your graphics card would probably prefer not to follow it there.

In practice, renderers cut the blur off once it gets too faint to matter, but the team had a more ambitious question in mind: could they skip the blurring altogether?

### Blurring a rounded rectangle

The team's answer was to treat the shadow as a Gaussian blur of a rounded rectangle and work it out from the shape itself. The algorithmic approach had already been put to the test in Skia, the open-source graphics library used by Chrome, Flutter, and Android, and the team adapted it for Roblox's renderer. Rather than starting with an image, it starts with something Roblox already knows: the shape of the frame casting the shadow. Most UI frames are rectangles or rounded rectangles, so the renderer already knows their dimensions and corner radii.

To draw the shadow, the renderer creates two new outlines around the frame, one a little larger and another pulled inward. Both curve around the same corners, leaving a band between them that looks a bit like a very rectangular donut.

The outlines aren't placed arbitrarily. Each sits one and a half times the shadow's blur radius from the frame's edge, a distance equivalent to three standard deviations along the Gaussian curve. Beyond the outer outline, the shadow has faded to almost nothing, so the renderer can safely stop drawing.

The band gets divided into triangles through a process called * tessellation* . Each vertex, or corner of a triangle, gets a value describing its position along the shadow's fade. The GPU then interpolates those values across the triangles, giving each pixel a position between the inner and outer edges.

That tells the renderer * where*  the shadow should fade, but it still leaves the question of how dark each pixel should be. Working out the Gaussian curve for every pixel would mean doing the same mathematical work over and over, so the team calculated the curve ahead of time and stored the answer in a tiny texture. As the GPU draws the shadow, it looks up the opacity for each pixel instead of calculating it from scratch.

### Try the shadow playground

The companion place has a shadow playground, with a frame that uses a real UIShadow and a panel of buttons for each of its properties. Open it from the top-right corner of the experience and see what each property does.

It works on a computer, phone, or tablet. Every control is a real UIShadow property, so anything you build there works the same way in Studio.

[

Play on Roblox](https://www.roblox.com/games/start?placeId=107426260461768)

Expand video

1. 01** Blur, offset, and transparency**

Change the [BlurRadius](/docs/en-us/reference/engine/classes/UIShadow#BlurRadius) , [Offset](/docs/en-us/reference/engine/classes/UIShadow#Offset) , [Transparency](/docs/en-us/reference/engine/classes/UIShadow#Transparency) , and [Spread](/docs/en-us/reference/engine/classes/UIShadow#Spread)  of a single shadow, starting from a new [UIShadow](/docs/en-us/reference/engine/classes/UIShadow) 's default settings.

2. 02** A second layer**

Add a second, softer [UIShadow](/docs/en-us/reference/engine/classes/UIShadow)  behind the first, like the two layers under the shop menu. Its [ZIndex](/docs/en-us/reference/engine/classes/UIShadow#ZIndex)  of -2 draws it behind the first shadow. Load the sword shop shadows fills in the menu's exact values.

3. 03** The frame itself**

Change the frame's [CornerRadius](/docs/en-us/reference/engine/classes/UICorner#CornerRadius) , [Size](/docs/en-us/reference/engine/classes/GuiObject#Size) , and [Rotation](/docs/en-us/reference/engine/classes/GuiObject#Rotation)  without touching either shadow, and see both shadows update to match. For more on each property, see [Shadow](/docs/en-us/ui/appearance-modifiers#shadow)  in the UI appearance modifiers guide.

### Eight segments per corner

The first version approximated each rounded corner with just eight segments, which meant the entire shadow could be drawn with only 73 vertices and 108 triangles - hardly enough geometry to trouble a GPU. The team figured any imperfections would disappear into the shadow's soft outer edge, and for large, blurry shadows, they did. But make the shadow tight enough, and suddenly those segments weren't so hard to see.

The team also wanted to make room for more than one shadow on a frame, a technique often used by designers. Pair a small, dark shadow with a larger, softer one, and suddenly the panel has more natural depth. Supporting those layers meant figuring out which shadow should be drawn on top, something worth sorting out early rather than having to rework the renderer later.

Because the shadow is built from the frame, it goes wherever the frame goes. Give each corner a different radius? No problem. Rotate the frame or resize the whole thing? The shadow follows along. If you've ever fiddled with CSS, you'll recognize those controls. You can play around with your design and change your mind ten times without opening Photoshop once.

Players, meanwhile, won't know whether the shadow under your shop menu came from a PNG or a mesh of triangles, and they probably won't care. They'll just see a shop that looks like it's floating above the game... and then they'll buy the sword.

Chapter 02  · Gradients

## Gradients beyond the straight line

Radial and conical gradients, drawn by a shader instead of more geometry.

Gradients had the opposite problem. For shadows, adding geometry was the clever part. Gradients were already drowning in it.

Roblox has supported linear UI gradients for years. You pick a direction and a few colors, and the engine blends between them. Under the hood, the old renderer did much of the prep work on the CPU, dividing the shape into strips at the gradient's color and transparency stops, which worked well enough when the colors traveled in a straight line across a rectangle.

Things get messier when the colors stop traveling in a straight line. A radial gradient spreads outward from a center point, like a glow, while a conical gradient (sometimes called a sweep gradient) changes color as you move around a point, like the hand of a clock. Now the bands of color are rings and wedges, and trying to build them out of straight strips would mean cutting the shape into an awful lot of little pieces.

### Try the gradient playground

The companion place also has a gradient playground, with a frame that uses a real UIGradient and buttons for each of its properties. Open it from the top-right corner of the experience and experiment.

It works on a computer, phone, or tablet. Every control is a real UIGradient property, so anything you build there works the same way in Studio.

[

Play on Roblox](https://www.roblox.com/games/start?placeId=107426260461768)

Expand video

1. 01** Three gradient types**

Switch [Type](/docs/en-us/reference/engine/classes/UIGradient#Type)  between [Linear](/docs/en-us/reference/engine/enums/GradientType#Linear) , [Radial](/docs/en-us/reference/engine/enums/GradientType#Radial) , and [Conical](/docs/en-us/reference/engine/enums/GradientType#Conical) , and try them with a few sets of [Color](/docs/en-us/reference/engine/classes/UIGradient#Color)  and a fade from a [Transparency](/docs/en-us/reference/engine/classes/UIGradient#Transparency)  of 0 to 1.

2. 02** Rotation, offset, and scale**

Turn the gradient with [Rotation](/docs/en-us/reference/engine/classes/UIGradient#Rotation) , move its center with [Offset](/docs/en-us/reference/engine/classes/UIGradient#Offset) , and stretch the colors with [Scale](/docs/en-us/reference/engine/classes/UIGradient#Scale) . On a wide frame rotated to 45 degrees, [Scale](/docs/en-us/reference/engine/classes/UIGradient#Scale)  is how you get the blend all the way into the corners.

3. 03** The frame itself**

Change the frame's [CornerRadius](/docs/en-us/reference/engine/classes/UICorner#CornerRadius)  and [Size](/docs/en-us/reference/engine/classes/GuiObject#Size) . Load the sword shop header fills in the values behind the shop menu's header. For more on each property, see [Gradient](/docs/en-us/ui/appearance-modifiers#gradient)  in the UI appearance modifiers guide.

### Shader gradients

Rather than keep slicing up the shape, the team explored leaving it intact and letting a shader work out the color of each pixel directly. For a linear gradient, that means understanding how far along a line the pixel sits. For a radial one, it's the distance from the center. And for a conical gradient, it's how far around the circle you've traveled.

Each calculation gives the shader a position along the gradient, which it can use to work out what color belongs there.

Finding the right colors, though, takes work. Roblox gradients store color and transparency as two separate lists, and each can have up to twenty stops. The stops don't necessarily line up: a color might change at one point while the transparency changes somewhere else. Since the lists share their starting and ending points, combining them can leave you with as many as thirty-eight different positions to consider.

The shader still needed to find the two stops surrounding each pixel's position so it could figure out which values to blend. In an early prototype, the team tried an algorithm called * binary search* . Think of it like a game of higher-or-lower: the shader checks the middle of the list, figures out which half contains the position it's looking for, and throws the other half away. It keeps narrowing things down until it finds the right pair, without having to check every stop along the way.

It was a clever idea, but it didn't hold up on real hardware. The prototype ran slowly and crashed on low-end devices, so the team abandoned it.

Instead, they went with something much simpler. The renderer creates a miniature version of each gradient, just one pixel high, with all its colors laid out in a row. Those strips are packed together into a shared texture called an * atlas* . The shader still works out where each pixel sits along the gradient, but now, instead of searching through a list of stops, it can pick the color straight from the strip. That gives the shader much less to do, which was especially important for the lower-end Android devices the team needed to support.

Since the renderer no longer has to slice up the underlying geometry, the same approach can also be used on all sorts of shapes, including curved paths and even the shadows we talked about earlier.

### Existing gradients

There was still the question of what to do with all the gradients Roblox had already been drawing for years. Take a long, wide menu header with a diagonal gradient. Under the older calculation, rotating the gradient could leave the far corners outside the part where colors transition, filling those areas with a solid color instead. CSS and Figma handle the geometry differently, so the same-looking settings don't always produce the same result.

** Leave the old gradients alone**

You might think the obvious answer would be to change the calculation to match those common design tools. Except somebody, somewhere, has already built an entire interface around the old behavior, quirks and all. Change the math, and their UI could look different tomorrow even though they haven't touched a thing.

So the team kept the old calculation rather than risk changing interfaces creators had already built. That didn't mean creators were stuck with it, though: by adjusting a gradient's [Scale](/docs/en-us/reference/engine/classes/UIGradient#Scale) , they could stretch the colors toward the corners of a rotated header, getting something closer to what they'd expect from CSS or Figma. Meanwhile, the menu someone tuned three years ago could stay exactly as it was.

Chapter 03  · Clipping

## Clipping to a curve

Keeping scrolling cards inside a curve, without an extra texture for every panel.

Back in your shop menu, the item cards are supposed to disappear as they scroll beneath the panel's rounded corners. It sounds simple enough, except Roblox's most straightforward way of clipping UI doesn't know what to do with a curve.

Until this year, Roblox clipped UI entirely on the CPU, working out which parts of each element fell inside its container before anything reached the graphics card, and moving that work onto the GPU is what finally made it possible to clip rotated shapes at all. The GPU's simplest clipping tool is a * scissor rectangle* , which has been around for ages: you hand the GPU a rectangular boundary, and it stops drawing anything that falls outside it. It's fast and reliable, but a rectangle is the only shape it understands.

Creators get around this by pairing a [CanvasGroup](/docs/en-us/reference/engine/classes/CanvasGroup)  with a [UICorner](/docs/en-us/reference/engine/classes/UICorner) , even though [CanvasGroup](/docs/en-us/reference/engine/classes/CanvasGroup)  was built for much more than clipping.

Say you want to fade an entire menu out of view. You could gradually make each button, label, and image more transparent, but the overlapping elements might still show through each other like a stack of overhead projector slides. To avoid that, a [CanvasGroup](/docs/en-us/reference/engine/classes/CanvasGroup)  draws the whole menu into a separate image first, then fades that image as a single piece.

It's a technique called * render-to-texture* , and it's useful when you need to treat a collection of UI elements as one. The downside is that creating and storing that image takes memory and additional rendering work.

** Most creators use CanvasGroup for clipping**

When senior software engineer Emily Ma ([@ThunderBolt5140](https://www.roblox.com/users/1726941628/profile) ) looked into how creators were using [CanvasGroup](/docs/en-us/reference/engine/classes/CanvasGroup) , she did more than ask around. She talked to creators on the DevForum and at RDC, then added telemetry to the engine to see how often [CanvasGroups](/docs/en-us/reference/engine/classes/CanvasGroup)  actually needed render-to-texture. It turned out that roughly 60 percent were being used only for rounded or rotated clipping. Those creators weren't trying to fade or tint an entire interface; they just wanted to keep their content where it belonged, but the engine was doing all that extra work anyway.

On devices with limited graphics memory, those extra textures could become expensive. Under certain conditions, a [CanvasGroup](/docs/en-us/reference/engine/classes/CanvasGroup)  might even end up looking blurry or turning into a solid black rectangle. Not exactly what you want from a feature that's supposed to make your menu look nicer.

### Stencil buffers

** Stencil clipping hasn't been released yet**

The approach in this section is still in development, so some of the details may change before it ships.

For clipping alone, the team found a simpler option: a * stencil buffer* .

Imagine cutting a rounded rectangle out of a piece of cardboard and using it as a stencil. You can paint all over it, but only the paint that goes through the opening reaches the surface underneath. A stencil buffer does the same thing, except the cardboard is replaced by a hidden layer of numbers that tells the GPU where it's allowed to draw.

For your shop menu, the renderer first marks the rounded shape of the panel in that hidden layer. Then, as the item cards scroll, the GPU only draws the parts that fall inside those marks. Anything that strays outside the frame simply doesn't show up. You can even put one clipped panel inside another, and the stencil buffer keeps track of where their boundaries overlap.

With stencil clipping enabled, a [CanvasGroup](/docs/en-us/reference/engine/classes/CanvasGroup)  that only needs clipping can draw its contents directly, without going through render-to-texture at all. It all comes down to a few settings. As long as [GroupTransparency](/docs/en-us/reference/engine/classes/CanvasGroup#GroupTransparency)  stays at 0, [GroupColor3](/docs/en-us/reference/engine/classes/CanvasGroup#GroupColor3)  stays white (255, 255, 255), and there's no [UIGradient](/docs/en-us/reference/engine/classes/UIGradient)  parented to the group, the stencil can handle the clipping on its own. Change any of those, and the renderer goes back to drawing a separate texture so it can apply the effect to the group as a whole.

Those savings can add up. In one example Emily worked through, a screen with twenty clipping-only [CanvasGroups](/docs/en-us/reference/engine/classes/CanvasGroup)  could go from needing twenty offscreen textures to needing none of them.

### What's left to solve

There was a catch, though. A stencil buffer stores whole numbers, so each pixel is either inside the clipping boundary or outside it, with nothing in between. On its own, that can leave rounded edges looking jagged next to the smooth corners Roblox already draws using a technique called * signed distance fields* . Emily is working on a way to add a faint, fading fringe around those clipped edges to smooth them out.

Getting stencil clipping to work across all of Roblox's graphics platforms was another challenge. Adding support meant changes to the graphics backends used on iOS, Android, Mac, Windows, PlayStation, Xbox, and VR. Emily says that was the hardest part of the project: making sure the new approach could work everywhere Roblox runs.

Until stencil clipping ships, a [CanvasGroup](/docs/en-us/reference/engine/classes/CanvasGroup)  is still the way to keep content inside a curve, but once it does, the payoff goes beyond saving memory. The texture behind a [CanvasGroup](/docs/en-us/reference/engine/classes/CanvasGroup)  is currently capped at 1024 by 1024 pixels, and since a clipping-only group will be able to draw its contents directly instead, the team can lift that cap and let a large clipped panel like your shop menu render at full resolution.

Creators aren't going to use these features one at a time. They'll put a shadow on a rounded panel, add a gradient to its header, fill it with scrolling cards, and then decide the whole thing needs to be twice as wide. Or tilted slightly. Or squeezed onto a phone screen.

Maybe you give your sword shop a sleek, elegant menu. Someone else might use those same tools to build an elaborate spaceship dashboard, while another creator makes an interface that looks like it was drawn in crayon at two in the morning.

The renderer doesn't need to have good taste. It just needs to give creators the freedom to exercise theirs.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
