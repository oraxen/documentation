---
description: A summary of the most common questions about Oraxen
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966825489098489856/unknown.png
coverY: 0
---

# ❓ FAQ

## Oraxen is using its own resourcepack, can I still use mine?

You can merge any resourcepacks into Oraxens generated pack.\
Oraxen will then send the pack to all players with the merged packs.\
Check out the ResourcePack page for a detailed explanation

## Can I disable the default assets and configs Oraxen comes with?

Yes, `settings.yml` contains options to disable both of these.\
Note: Required configs and assets will still be generated, but most will be disabled.

### NoteBlocks & Tripwires aren't working correctly?

To allow for Custom Blocks, Oraxen **has** to override a vanilla block, like noteblocks and tripwires.\
If you do not care about Custom Blocks, you can return the vanilla behaviour by disabling these mechanics in `mechanics.yml`

## My textures work when I use optifine but not in vanilla

This usually stems from said textures or models using OptiFine only formatting.\
As of Minecraft 1.11, the ResourcePack formatting is very strict.\
Files must be all lowercase, not contain spaces and textures can't exceed 256x256 resolution.

## How to hide item tooltips?

If your server is at 1.20.5 or above, you can look at this:\
Otherwise you will need to use this, [https://github.com/lolgeny/item-tooltip-remover](https://github.com/lolgeny/item-tooltip-remover)
