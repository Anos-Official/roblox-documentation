<!-- Source: https://create.roblox.com/docs/en-us/cloud/guides/configs -->

Experience configs | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/cloud/guides/configs.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Open Cloud API](/docs/en-us/cloud)

# Experience configs

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/cloud/guides/configs.md)

The configs API lets you manage [experience configs](/docs/en-us/production/configs)  programmatically rather than using Creator Hub or Studio. This guide covers a typical flow:

-

Create or update a draft config.

-

Publish it.

-

Get the latest config values.

-

Roll back to a prior value using version history.

Values you publish are available in your experience right away. In server scripts, use [ConfigService](/docs/en-us/reference/engine/classes/ConfigService)  to read configs and react to real-time updates. [ConfigService:GetConfigAsync()](/docs/en-us/reference/engine/classes/ConfigService#GetConfigAsync)  and [ConfigSnapshot:GetValue()](/docs/en-us/reference/engine/classes/ConfigSnapshot#GetValue)  let you read values, and [ConfigSnapshot.UpdateAvailable](/docs/en-us/reference/engine/classes/ConfigSnapshot#UpdateAvailable)  with [ConfigSnapshot:Refresh()](/docs/en-us/reference/engine/classes/ConfigSnapshot#Refresh)  or [ConfigSnapshot:GetValueChangedSignal()](/docs/en-us/reference/engine/classes/ConfigSnapshot#GetValueChangedSignal)  lets you respond when values change. For Luau code samples and further details, see [Add configs to your code](/docs/en-us/production/configs#add-configs-to-your-code)  and [Refresh snapshots](/docs/en-us/production/configs#refresh-snapshots)  in the experience configs guide.

Before you start, [generate an API key](/docs/en-us/cloud/auth/api-keys)  or [configure an OAuth 2.0 app](/docs/en-us/cloud/auth/oauth2-overview) . Read operations require the universe:read  scope. Write operations (drafts, publish, restore) need universe:write .

All endpoints use your universe ID, which you can find on the [Creator Dashboard](https://create.roblox.com/dashboard/creations) . Click the experience tile overflow menu and Copy Universe ID .

For the full endpoint reference, request and response schemas, and error codes, see the [Cloud API reference](/docs/en-us/cloud/reference/features/configs) .

## [Repositories](#repositories)[](#repositories)

Requests to the configs endpoints use a repository  in the path and an entries  object in the request body. For example, this request adds a draft config:

```

PATCH /creator-configs-public-api/v1/configs/universes/<UNIVERSE_ID>/repositories/<REPOSITORY>/draft

{

  "entries": {

    "enableNewTutorial": true

  }

}

```

-

Repositories  differ by product and separate configs by system.

-

Entries  are the config key-value pairs. You send and receive a single flat object of keys and values.

This guide covers in-experience configs, so all requests use InExperienceConfig  for repository. Repositories will eventually expand to cover additional products and use cases.

| Use case | | Repository |
| --- | --- |
| In-experience configs | | InExperienceConfig |

## [Create or update configs](#create-or-update-configs)[](#create-or-update-configs)

Before going live, config changes are staged as drafts. You can either set the entire config in one operation or apply partial updates until you're happy with it:

-

Starting from scratch or replacing everything  — Use the overwrite endpoint so that the payload is the full desired state. Any key you omit is treated as removed.

-

Changing only some keys  — Use the partial update endpoint so only the keys you send are updated; everything else stays as-is.

This sample code sets bossHealth  to 100  and uses the overwrite endpoint:

Python cURL

```

import requests

API_KEY = "<API_KEY>"

UNIVERSE_ID = "<UNIVERSE_ID>"

BASE = f"https://apis.roblox.com/creator-configs-public-api/v1/configs/universes/{UNIVERSE_ID}/repositories/InExperienceConfig"

headers = {"x-api-key": API_KEY, "Content-Type": "application/json"}

# Optional: send previousDraftHash if you have an existing draft and want optimistic concurrency

payload = {

    "entries": {

        "bossHealth": 100

    }

}

r = requests.put(f"{BASE}/draft:overwrite", headers=headers, json=payload)

r.raise_for_status()

draft = r.json()

draft_hash = draft["draftHash"]  # Keep this for publishing

print("Draft staged. draftHash:", draft_hash)

```

The response includes the draftHash  value. You need this hash in order to publish. If you prefer to only tweak a few keys in your draft, use the PATCH method on the /draft  endpoint and only send the entries (keys) you want to change.

### [About draft hashes](#about-draft-hashes)[](#about-draft-hashes)

A draft hash  is an opaque identifier for the current state of your draft. The API returns it after any read or write operation to a draft (create, update, overwrite, reset, restore).

When updating or publishing drafts, you can send previousDraftHash  in the request body. If the hash doesn't match the server's current draft (e.g. someone else published or edited in the meantime), the request fails. You can then re-read the updated draft, get the new hash, and retry or merge changes.

Always save the draftHash  from the last draft response before calling publish or before making another draft change if you use previousDraftHash .

## [Publish your changes](#publish-your-changes)[](#publish-your-changes)

When you're happy with the draft, publish it so the new values go live. Pass draftHash  from the draft response, message  for version history purposes, and deploymentStrategy  (either GradualRollout  for a 15-minute rollout or Immediate ). The following sample code deploys the config immediately:

Python cURL

```

publish_payload = {

    "draftHash": draft_hash,

    "message": "Set boss health to 100",

    "deploymentStrategy": "Immediate"

}

r = requests.post(f"{BASE}/publish", headers=headers, json=publish_payload)

r.raise_for_status()

result = r.json()

print("Published. configVersion:", result["configVersion"])

```

After a successful publish, the draft is cleared, and your experience receives the new config according to the deployment strategy. The response includes the new config version:

```

{

  "configVersion": 6

}

```

## [Get your published config](#get-your-published-config)[](#get-your-published-config)

To confirm the change went through, fetch the latest published config. Use the values-only endpoint when you only need keys and values; use the full endpoint when you also need metadata (descriptions, last-accessed time, etc.). This sample code uses the values-only endpoint, with the full endpoint commented out:

Python cURL

```

# Values only (same shape RCC and your game see)

r = requests.get(BASE, headers=headers)

r.raise_for_status()

config = r.json()

boss_health = config["entries"].get("bossHealth")

print("Published bossHealth:", boss_health)  # Should be 100

# Or with full metadata:

# r = requests.get(f"{BASE}/full", headers=headers)

```

Verify that entries.bossHealth  (or your key) matches what you published.

## [View history and roll back](#view-history-and-roll-back)[](#view-history-and-roll-back)

Every publish creates a revision, just like a version control system. You can list revisions to see who changed what and when, then restore to a previous revision if you need to roll back.

This sample code calls the revisions endpoint and prints the results. Each revision includes revisionId , version , time , publishedBy , message , and changes  (the key, the "before" value, and the "after" value).

Python cURL

```

r = requests.get(f"{BASE}/revisions", headers=headers, params={"MaxPageSize": 10})

r.raise_for_status()

data = r.json()

for rev in data["revisions"]:

    print(rev["version"], rev["time"], rev["message"], "— revisionId:", rev["revisionId"])

```

To roll back, call the restore endpoint with the revisionId  you want to revert to. That clears the current draft and stages a revert commit; it does not  publish. To publish, you must call publish  with the returned draftHash , just like publishing a new change.

Python cURL

```

REVISION_ID = "1234567890"  # From the list above

r = requests.post(f"{BASE}/revisions/{REVISION_ID}/restore", headers=headers)

r.raise_for_status()

restore_draft = r.json()

restore_hash = restore_draft["draftHash"]

# Publish the revert

publish_payload = {

    "draftHash": restore_hash,

    "message": "Rollback to previous config",

    "deploymentStrategy": "Immediate"

}

r = requests.post(f"{BASE}/publish", headers=headers, json=publish_payload)

r.raise_for_status()

print("Rollback published. configVersion:", r.json()["configVersion"])

```

## [Limitations](#limitations)[](#limitations)

| Limit | | Maximum |
| Keys per repository | | 100 |
| Key length | | 256 characters |

Requests that exceed these limits will fail. For type-specific value limits (e.g. string vs JSON) in your experience, see [Limits](/docs/en-us/production/configs#limits)  in the experience configs guide.

For full details on all the endpoints in this guide, see the [Cloud API reference](/docs/en-us/cloud/reference) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
