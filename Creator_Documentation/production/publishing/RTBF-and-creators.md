<!-- Source: https://create.roblox.com/docs/en-us/production/publishing/RTBF-and-creators -->

RTBF and creators | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/production/publishing/RTBF-and-creators.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Platform](/docs/en-us/get-started)
4. /
5. Guidelines and policies

# RTBF and creators

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/production/publishing/RTBF-and-creators.md)

What is RTBF?

 RTBF stands for the right to be forgotten , a principle in global privacy law that gives individuals the right to request the deletion of their personal data when it is no longer necessary. Honoring RTBF requests is a legal obligation for data controllers and is critical to maintaining user trust and regulatory compliance.

Global privacy regulations create rules for "controllers" of data, a term that means individuals or organizations that determine why and how data is processed. Privacy rules typically define "personal data" or Personally identifiable information (PII) broadly. It encompasses any information that relates to an identified or identifiable living individual. If a piece of data can be traced back to an individual user, it may be personal data subject to privacy regulations.

A fundamental principle across global frameworks is that controllers should not retain personal data indefinitely. Similarly, users can request the deletion of data that is no longer necessary. If a user requests that Roblox permanently delete their Roblox account, Roblox notifies creators so they can delete information that is no longer needed. The primary rule governing deletion is that personal data must be permanently erased after there is no longer a valid legal or business basis for processing it.

## [RTBF notifications and automation](#rtbf-notifications-and-automation)[](#rtbf-notifications-and-automation)

When an RTBF request affects one or more of your games, Roblox helps you identify and process the request in the following ways:

-

Roblox messages  — Roblox sends an automated message each day to your inbox that lists the RTBF requests requiring action and the affected games.

-

Automated data store deletion  — If you configure RTBF deletion templates for a game, Roblox uses them to automatically delete matching keys and data stores when it processes a request. For setup instructions, see [Data store right to be forgotten (RTBF)](/docs/en-us/cloud-services/data-stores/right-to-be-forgotten) .

-

Creator webhooks  — If you configure a webhook with the Right to Erasure Request  trigger, Roblox automatically invokes it for affected games. You can use the request payload in your own automation to delete personal data. For setup instructions and a sample workflow, see [Automate right to erasure using webhooks](/docs/en-us/cloud/webhooks/automate-right-to-erasure) .

For automation, first use automated data store deletion for supported data. Use a creator webhook for more complex cases, such as custom deletion logic, data store schemas that RTBF deletion templates don't support, or personal data stored outside of data stores.

Roblox always sends the daily RTBF message for affected games, regardless of whether you configure automated data store deletion or a creator webhook. You remain responsible for permanently deleting all personal data covered by an RTBF request. Review the daily message and verify that data outside configured templates or custom automation is also deleted.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
