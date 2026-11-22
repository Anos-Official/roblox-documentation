<!-- Source: https://create.roblox.com/docs/en-us/projects/update-games -->

Release game updates | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/projects/update-games.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Projects](/docs/en-us/projects)
6. /
7. [Games and places](/docs/en-us/production/publishing/publish-games-and-places)

# Release game updates

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/projects/update-games.md)

When you publish an updated version of a game to Roblox, players aren't immediately removed from old versions of the game. Instead, you can migrate players to the updated version by restarting all of your outdated servers.

If you don't restart servers, players transition to the new version of the game as the servers running old versions eventually empty and shut down. This option is non‑disruptive, but your player base might be playing different versions of the game for a prolonged period of time; if your underlying player data format changes, you should probably restart servers.

For time-sensitive updates, you might prefer to deploy early, hide content behind a [config](/docs/en-us/production/configs) , and then change the config value to release your new content.

## [Restart servers](#restart-servers)[](#restart-servers)

To restart servers for release updates:

1.

Go to [Creations](https://create.roblox.com/dashboard/creations)  and select the game you want to restart servers for.

2.

In the left-hand navigation, navigate to Configurations  > Server management .

3.

Select the places you want to restart.

4.

Click Restart Servers .

5.

In the Confirm Server Restart  dialog:

1.

Select one or both of the following restart options:

-

Restart only servers with outdated versions  to avoid restarting servers that are running the latest published place version.

-

Delay server restart  to delay the shutdown of servers and allow players a set time between 1 and 60 minutes to leave the game on their own instead of being temporarily disconnected. This is also known as server bleed-off.

2.

Click Restart .

Unless you have a game update workflow that is independent of place version, it's recommended that you always select Restart only servers with outdated versions  to avoid unnecessarily disconnecting players.

After you restart servers, Roblox:

1.

Stops all matchmaking to servers designated for shutdown. Players who join your game by clicking the Play  button will not be matched to these servers, but they can still join them by accepting invites, teleporting, or joining another user from their profile.

2.

Waits for the configured delay time, if you selected the Delay server restart  option.

3.

Automatically teleports players to the updated version of the game. All players on the same old server are sent to the same replacement server running the new version.

If you want to completely shut down your game and not allow players to reconnect after you restart your servers, you must revoke access to your game from the [public](/docs/en-us/production/publishing/publish-games-and-places#target-audience) .

## [Notifications on servers](#notifications-on-servers)[](#notifications-on-servers)

When you launch a delayed server restart, the [DataModel.ServerRestartScheduled](/docs/en-us/reference/engine/classes/DataModel#ServerRestartScheduled)  event will fire on affected servers with the following arguments:

-

restartTime  — A [DateTime](/docs/en-us/reference/engine/datatypes/DateTime) . The earliest time the server is scheduled to shut down.

-

source  — This will always be [Enum.CloseReason.DeveloperUpdate](/docs/en-us/reference/engine/enums/CloseReason#DeveloperUpdate)  for your published updates.

-

attributes  — An optional JSON object you can use to provide custom information about the restart, such as the update reason, urgency, etc.

In your server scripts, you can subscribe to this event to provide players with information about the upcoming restart. You might choose to provide a countdown timer in your UI, prompt players to save their progress, or teleport them to updated servers at the most convenient time.

Servers will also be notified when Roblox needs to restart servers for infrastructure maintenance reasons. The same [DataModel.ServerRestartScheduled](/docs/en-us/reference/engine/classes/DataModel#ServerRestartScheduled)  event fires, with source  as [Enum.CloseReason.RobloxMaintenance](/docs/en-us/reference/engine/enums/CloseReason#RobloxMaintenance)  and attributes  as an empty dictionary.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
