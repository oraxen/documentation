---
description: A summary of the most commonly asked questions
icon: question
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966825489098489856/unknown.png
coverY: 0
---

# Frequently Asked Questions

## Is Oraxen A Mod?

No, Oraxen is not a mod in the usual sense of the word. It's a minecraft plugin that allows you to add items, blocks and similar kinds of cool stuff to the game - all with an automatically installed resource pack.

## Oraxen Is Using Its Own Resource Pack, Can I Still Use Mine?

You can merge any resourcepacks into Oraxens generated pack.\
Oraxen will then send the pack to all players with the included merged packs.\
Simply copy your packs assets-folder and paste it into /Oraxen/pack/assets.

## I Use Bungee/Velocity But The Pack Keeps Reloading When Players Switch Servers?

This is because the player technically leaves one server and joins another. Therefore, Minecraft removes and sends the resourcepack.\
If you want to prevent this you can get [BungeePackLayer](https://www.spigotmc.org/resources/%E2%9C%82%EF%B8%8F-bungee-pack-layer-optimize-resource-pack-sending.94978/).\
This is a Bungee/Velocity plugin which will prevent the pack from being resent (unless it is different).\
A pack will be different if the config files on all servers are not identical.

## Can I Disable The Default Assets And Configs Oraxen Comes With?

Absolutely. Your `settings.yml` file contains options to disable both of these.\
Note: Required configs and assets will still be generated, but most will be disabled.

## How Do I Disable Or Change The Welcome Sound?

Of course, `settings.yml` contains configurable actions to perform when the pack is sent to a user, including a sound by default. The example below shows where you can disable or change the sound as you desire.

```yaml
  receive:
    enabled: true
    loaded:
      actions:
        sound:
          # Enabled by default, just switch to enabled to send
          # the below sound whenever someone joins
          enabled: true
          type: minecraft:welcome
          volume: 1.0
          pitch: 1.0
```

## Does Oraxen Replace Any Vanilla Items?

The goal of Oraxen is to add things to the game without losing features, so the short answer is no. However, Minecraft has some limitations (you can't really add new blocks or armors for example) so we had to make a choice (a choice that can be undone by disabling the related mechanics):\
\- new blocks will use vanilla unused noteblock variations: this can create issues in constructions made using those unusual variations.

## When I Add An Item, Why Does It Break The Textures Of Others Already Created?

By default (pre 1.21.4), Oraxen automatically picks custom model data values for your items and generates them in the most optimized way.\
Every item, which does not use the exact same model, needs to have a different custom model data value. When adding a new item to Oraxen and setting it's custom model data value manually, you can break other items by accidentally setting the same value on two or more different items.

{% hint style="info" %}
Don't forget to reload the plugin with `/o reload all` **AND** your resource pack using `/o pack send @a`(you can also disconnect and reconnect to the server)
{% endhint %}

## Why Do My Textures Work When I Use Optifine But Not In Vanilla?

It is no longer possible to use upper case in folder, texture or model names with vanilla resource packs since minecraft 1.11, however optifine still supports it. Please never use upper case to avoid problems.

## How Do I Update Oraxen?

Here is a great video that can help you: [https://youtu.be/LkansZwVaPY](https://youtu.be/LkansZwVaPY)

## How Do I Hide Item Tooltips?

[https://github.com/lolgeny/item-tooltip-remover](https://github.com/lolgeny/item-tooltip-remover)

## Where Do I Suggest New Features Or Report An Issue?

First option: Login to github and submit an issue to the official repo: [git.io/oraxen](https://github.com/Th0rgal/Oraxen)

Second option: Join [the discord](https://discord.gg/2ng6q3JNQ7), get your Oraxen verified rank, then go to the support channel where you can open a ticket.

## How Do I Just Use Oraxen's Mechanics?

Go to your settings.yml file and set the following options:

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

The configurations do not go in that exact order. Once you've changed these lines, delete what is inside the /Oraxen/pack, /Oraxen/items and /Oraxen/glyphs paths and restart the server.
