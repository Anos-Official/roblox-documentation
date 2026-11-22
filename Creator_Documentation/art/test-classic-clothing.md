<!-- Source: https://create.roblox.com/docs/en-us/art/test-classic-clothing.md -->

---
title: "Test classic clothing"
url: /docs/en-us/art/test-classic-clothing
last_updated: 2026-06-16T15:58:05Z
description: "How to test your classic clothing items before uploading them to the Marketplace."
---

# Test classic clothing

> **Warning:** Many user-generated avatars on the Marketplace do not support 2D classic clothing. For information on creating modern 3D cosmetics, including rigid accessories and clothing items, see [Get started](/docs/en-us/avatar.md).

To ensure the best quality results, you can test your classic clothing before uploading or selling. You can test your clothes without needing to pay any fees by using [Roblox Studio](/docs/en-us/studio/setup.md).

1. From the toolbar's **Avatar** tab, click **Character**.
2. Choose a **Block Avatar** rig type from the popup menu. An avatar mannequin named **Rig** appears in the 3D workspace.
3. In the **Explorer** window, hover over the **Rig** object, click the **⊕** button and insert either a **ShirtGraphic** (T‑shirt), **Shirt**, or **Pants** object according to the clothing you want to test.
4. Locate and select the new **Shirt Graphic** or **Clothing** object parented under **Rig**._Shirt Graphic (T-shirt)__Clothing (Shirt/Pants)_
5. In the **Properties** window, locate the associated property as follows: | Clothing Type | Parent Class | Property |
| --- | --- | --- | | **T-Shirt** | `Class.ShirtGraphic` | `Class.ShirtGraphic.Graphic\|Graphic` | | **Shirt** | `Class.Shirt` | `Class.Shirt.ShirtTemplate\|ShirtTemplate` | | **Pants** | `Class.Pants` | `Class.Pants.PantsTemplate\|PantsTemplate` |
6. Click inside the property's row and select the image you uploaded to Roblox. This applies the clothing texture to the **Rig** character.

> **Success:** After testing, you can [upload and sell](/docs/en-us/art/upload-classic-clothing.md) your asset to the Marketplace.