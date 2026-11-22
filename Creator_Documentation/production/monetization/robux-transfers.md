<!-- Source: https://create.roblox.com/docs/en-us/production/monetization/robux-transfers -->

Robux transfers | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/production/monetization/robux-transfers.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Earn](/docs/en-us/production/monetization)

# Robux transfers

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/production/monetization/robux-transfers.md)

Robux transfers  let [Roblox Plus](/docs/en-us/production/monetization/roblox-plus#earn-from-robux-transfers)  subscribers send Robux directly to other users.

To support transfers in your game, call [PromptRobuxTransferAsync](/docs/en-us/reference/engine/classes/MarketplaceService#PromptRobuxTransferAsync)  to open the transfer prompt and use [BindReceiptHandler](/docs/en-us/reference/engine/classes/MarketplaceService#BindReceiptHandler)  to process transfer receipts. When a subscriber completes a transfer, your game earns 10%  of the Robux sent and the recipient receives the remaining 90% . For example, a 100 Robux transfer pays 90 Robux to the recipient and 10 Robux to your game.

Robux your game earns from transfers is eligible for the DevEx program . Roblox does not take a fee from these transfers.

When setting up transfers in your game, the amount must be between 10 and 500 Robux per transaction.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/roblox-plus/TransferRobuxPrompt.png)

As a creator, you do not have access to transfer details or control over execution. All Robux transfers are processed and managed by the Roblox platform, and all sender and recipient actions go through the same safety and eligibility checks. Inside your game, transfers are completed through a Roblox-controlled UI to ensure they are safe and policy-compliant.

## [Prompt Robux transfers](#prompt-robux-transfers)[](#prompt-robux-transfers)

To initiate a Robux transfer within your game:

1.

Call [PromptRobuxTransferAsync](/docs/en-us/reference/engine/classes/MarketplaceService#PromptRobuxTransferAsync)  from a server-side script.

2.

Pass the required parameters:

-

sender : The player initiating the transfer.

-

receiverUserId : The user ID of the recipient.

-

amount : The amount of Robux to transfer.

3.

Store the returned transferRequestId  that identifies the transfer request and can be used to log or correlate the transfer with receipts later.

The following example initiates a Robux transfer between two users:

```

local MarketplaceService = game:GetService("MarketplaceService")

local Players = game:GetService("Players")

-- Transfers Robux when a user triggers a RemoteEvent

local transferEvent = game.ReplicatedStorage:WaitForChild("RequestTransfer")

transferEvent.OnServerEvent:Connect(function(sender, receiverUserId, amount)

	-- Validates inputs

	if not sender or not sender:IsA("Player") then

		return

	end

	if typeof(receiverUserId) ~= "number" or receiverUserId <= 0 then

		warn("Invalid receiverUserId")

		return

	end

	if typeof(amount) ~= "number" or amount <= 0 then

		warn("Invalid amount")

		return

	end

	local success, result = pcall(function()

		return MarketplaceService:PromptRobuxTransferAsync(sender, receiverUserId, amount)

	end)

	if success then

		print(`Transfer initiated with TransferRequestId: {result}`)

	else

		warn(`Transfer failed: {result}`)

	end

end)

```

## [Handle transfer receipts](#handle-transfer-receipts)[](#handle-transfer-receipts)

After a successful transfer, Roblox generates receipts for both the sender and the recipient. You can process these receipts using [BindReceiptHandler](/docs/en-us/reference/engine/classes/MarketplaceService#BindReceiptHandler)  to confirm that the transfer completed successfully.

To encourage Plus subscribers to transfer Robux within your game, you can offer items or other perks for each successful transfer. If you do, process the receipt before granting the reward to ensure it's only given for completed transfers.

To process Robux transfer receipts:

1.

Use [BindReceiptHandler](/docs/en-us/reference/engine/classes/MarketplaceService#BindReceiptHandler)  to register a handler for [RobuxTransferSender](/docs/en-us/reference/engine/enums/ReceiptType#RobuxTransferSender) , which handles receipts for the user who initiated the transfer.

2.

Register a second handler for [RobuxTransferReceiver](/docs/en-us/reference/engine/enums/ReceiptType#RobuxTransferReceiver) , which handles receipts for the user who received the Robux.

3.

In each handler, inspect the receipt info, including PlayerId  and TransferRequestId . Both receipt types include a TransferRequestId  that matches the transferRequestId  returned by PromptRobuxTransferAsync .

4.

Return a [Enum.ReceiptDecision](/docs/en-us/reference/engine/enums/ReceiptDecision)  value from your handler:

-

Return [Processed](/docs/en-us/reference/engine/enums/ReceiptDecision#Processed)  after you finish handling the receipt. This marks the receipt as complete and confirms the Robux transfer was successful.

-

Return [NotProcessedYet](/docs/en-us/reference/engine/enums/ReceiptDecision#NotProcessedYet)  if the receipt can't be processed yet (for example, if the user is no longer in the server). This keeps the receipt unresolved so it can be delivered later (for example, when the user rejoins the server).

The following example registers handlers for both sender and recipient receipts:

```

local MarketplaceService = game:GetService("MarketplaceService")

local Players = game:GetService("Players")

-- Handles sender receipts (the user who sent the Robux)

local senderConnection = MarketplaceService:BindReceiptHandler(

	Enum.ReceiptType.RobuxTransferSender,

	function(receiptInfo)

		local player = Players:GetPlayerByUserId(receiptInfo.PlayerId)

		if not player then

			-- User left the server - receipt processing is deferred until user rejoins the server

			return Enum.ReceiptDecision.NotProcessedYet

		end

		print(`{player.Name} sent Robux (TransferRequestId: {receiptInfo.TransferRequestId})`)

		-- You can grant any sender-side acknowledgement or update the UI here

		return Enum.ReceiptDecision.Processed

	end

)

-- Handles recipient receipts (the user who received the Robux)

local receiverConnection = MarketplaceService:BindReceiptHandler(

	Enum.ReceiptType.RobuxTransferReceiver,

	function(receiptInfo)

		local player = Players:GetPlayerByUserId(receiptInfo.PlayerId)

		if not player then

			return Enum.ReceiptDecision.NotProcessedYet

		end

		print(`{player.Name} received Robux (TransferRequestId: {receiptInfo.TransferRequestId})`)

		-- You can grant any receiver-side benefits or update the UI here

		return Enum.ReceiptDecision.Processed

	end

)

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
