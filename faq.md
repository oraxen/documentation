---
description: A summary of the most common questions about Oraxen
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966825489098489856/unknown.png
coverY: 0
---

# Frequently Asked Questions

## Is Oraxen a mod?

No Oraxen is not a mod in the usual sense of the word. It's a minecraft plugin that allows you to add items, blocks and that kind of cool stuff to the game with an automatically installed texture pack.

## Oraxen is using its own texture pack, can I still use mine?

You can merge any resourcepacks into Oraxens generated pack.\
Oraxen will then send the pack to all players with the merged packs.\
Simply copy your packs assets-folder and paste it into Oraxen/pack/assets.\\

## I use Bungee/Velocity but the pack keeps reloading when players switch servers?

This is because the player technically leaves one server and joins another. Therefore, Minecraft removes and sends the resourcepack.\
If you want to prevent this you can get [BungeePackLayer](https://www.spigotmc.org/resources/%E2%9C%82%EF%B8%8F-bungee-pack-layer-optimize-resource-pack-sending.94978/).\
This is a Bungee/Velocity plugin which will prevent the pack from being resent, unless it is different.\
A pack will be different if the config files on all servers are not identical.

## Can I disable the default assets and configs Oraxen comes with?

Yes, `settings.yml` contains options to disable both of these.\
Note: Required configs and assets will still be generated, but most will be disabled.

## Does Oraxen replace items?

The goal of Oraxen is to add things to the game without losing features, so the short answer is no, however minecraft has some limitations (you can't really add blocks or armors for example), so we had to make a choice (a choice that can be undone by disabling the related mechanics):\
\- new blocks will use vanilla unused noteblocks variations: this can create issues in constructions made using those unusual variations.

## When I add an item, it breaks the textures of others already created

By default, Oraxen automatically set a custom model data to your items and generate it in the most optimized way.\
Every item, which do not use the same model, need to have a different model data, so when you add another item, it might break the others if you manually set the same.

{% hint style="info" %}
Don't forget to reload the plugin with `/o reload all` **AND** your resource pack using `/o pack send @a`(you can also disconnect and reconnect to the server)
{% endhint %}

## My textures work when I use optifine but not in vanilla

It is no longer possible to use upper case in textures or model names with vanilla since minecraft 1.11, however optifine still supports it. Please never use upper case to avoid problems.

## How to update Oraxen?

Here is a great video that can help you: [https://youtu.be/LkansZwVaPY](https://youtu.be/LkansZwVaPY)

## How to hide item tooltips?

[https://github.com/lolgeny/item-tooltip-remover](https://github.com/lolgeny/item-tooltip-remover)

## I would like to suggest a new feature or report an issue

First option: Login to github and submit an issue to the official repo: [git.io/oraxen](https://github.com/Th0rgal/Oraxen)

Second option: Join [the discord](https://discord.gg/4Qk5kBT9UX), get your Oraxen rank and go to the support or requests channel.

### I just want to use Oraxen's mechanics.

Go to settings.yml and set these options

```yaml
  upload:
    enabled: false
Pack:
  generation:
    generate: false
    compression: BEST_COMPRESSION
    protection: false
  dispatch:
    send_pack: false
  enable_configs_updater: false
Misc:
  reset_recipes: false
  auto_update_items: false
```

The configurations do not go in that order, once this is done, delete what is inside the Oraxen/pack, Oraxen/Items/ and Oraxen/glyphs paths.
