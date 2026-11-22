<!-- Source: https://create.roblox.com/docs/en-us/production/publishing/account-verification -->

Account verification | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/production/publishing/account-verification.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Platform](/docs/en-us/get-started)
4. /
5. Guidelines and policies

# Account verification

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/production/publishing/account-verification.md)

Account verification  is the process of connecting your identity on Roblox to your real world identity, either through an age check or via government ID. When you verify your account, you can distribute more of each asset type and maximize their discoverability within the [Creator Store](/docs/en-us/production/creator-store) , distribute audio assets under 10 seconds, monetize your [plugins](/docs/en-us/studio/plugins) , and access age-restricted Studio features such as [voice chat](/docs/en-us/chat/voice-chat) .

To sell priced assets, you need to verify with a [government ID](/docs/en-us/production/publishing/account-verification#verify-through-government-id)  and create a seller account. For more information, see [Creator Store - Distribute and sell assets](/docs/en-us/production/creator-store#distribute-and-sell-assets) .

## [Verify through government ID](#verify-through-government-id)[](#verify-through-government-id)

In order to verify your account with this method, you must:

-

Be at least 13 years of age.

-

Have a government-issued photo ID with your picture on it, such as a driver's license, passport, or residency permit.

-

Have a mobile device with a camera that can take photos of your face and ID.

Roblox uses advanced image processing technology to ensure your documents are legitimate. For more information on the account verification process, see [Age ID Verification FAQs](https://en.help.roblox.com/hc/en-us/articles/4407276151188) . To learn how Roblox processes your personal and biometric data, refer to the [Roblox Privacy Policy](https://en.help.roblox.com/hc/en-us/articles/115004630823-Roblox-Privacy-and-Cookie-Policy)  and [Roblox Facial Media Capture Notice](https://en.help.roblox.com/hc/en-us/articles/4412863575316-Roblox-Facial-Media-Capture-Privacy-Notice) .

To verify your account with a government-issued ID:

1.

Navigate to Settings , either on the [roblox.com](https://www.roblox.com/home)  or on the Roblox app.

1.

On web browser:  In the top-right corner, click the gear icon to display a contextual dropdown menu, then select [Settings](https://www.roblox.com/my/account#!/info) .

 ![Account settings menu on roblox.com](https://prod.docsiteassets.roblox.com/assets/publishing/account-verification/Account-Settings.png)

1.

On Roblox app:  In the bottom-right corner, click the ⋯ More  icon and select Settings .

2.

Select the Account Info  tab.

3.

Underneath your birthday, click Continue with ID .

 ![Option to verify age with selfie or ID](https://prod.docsiteassets.roblox.com/assets/publishing/account-verification/Verify-Birthday.png)

4.

Follow the instructions to complete the ID verification flow.

 ![Option to verify age with selfie or ID](https://prod.docsiteassets.roblox.com/assets/publishing/account-verification/Verify-With-ID.png)

1.

Allow camera access.

2.

Scan your ID document. Roblox detects what type of document you have.

1.

If there is a barcode on the back, scan and capture an image of the back of your ID.

3.

Capture a photo of yourself. This photo will be used to verify that you are the same person as the one on your photo ID.

5.

When verification is complete, your verified birthday displays in Settings  > Account info . Verification can take a few minutes.

## [Check verification status by script](#check-verification-status-by-script)[](#check-verification-status-by-script)

Within a [Script](/docs/en-us/reference/engine/classes/Script) , the [Player:IsVerified()](/docs/en-us/reference/engine/classes/Player#IsVerified)  method lets you check the verification status of users accessing your games, allowing you to limit access to specific content, ranked queues, or even the game itself. Because users that verify their accounts connect their Roblox identity to their real-world identity, it's much less likely they will cheat, spam, or otherwise risk being blocked from your game, making this method especially useful for competitive and ranked games.

The following script checks the verification status of each player as they join the game. If they have verified their account, the console prints true .

```

local Players = game:GetService("Players")

local function onPlayerAdded(player)

	print(player:IsVerified())

end

for _, player in Players:GetPlayers() do

	onPlayerAdded(player)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

The method also accepts an optional [Enum.VerifiedLevel](/docs/en-us/reference/engine/enums/VerifiedLevel)  parameter if you want to do more granular gating:

-

[Enum.VerifiedLevel.Low](/docs/en-us/reference/engine/enums/VerifiedLevel#Low)  — Useful for gating standard features such as in-game trading, where the goal is to deter alternate accounts.

-

[Enum.VerifiedLevel.High](/docs/en-us/reference/engine/enums/VerifiedLevel#High)  — Useful for gating high-stakes features such as ranked matchmaking queues, where you want the highest degree of integrity.

If you don't pass a parameter, the method defaults to [Enum.VerifiedLevel.Low](/docs/en-us/reference/engine/enums/VerifiedLevel#Low) , so existing implementations continue to work without changes.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
