---
description: A summary of the most common questions about Oraxen
---

# Frequently Asked Questions

## Is Oraxen a mod?

No Oraxen is not a mod in the usual sense of the word. It's a minecraft plugin that allows you to add items, blocks and that kind of cool stuff to the game with an automatically installed texture pack.

## Oraxen is using its own texture pack, can I still use mine?

If you are a player: yes Oraxen is using a server resource pack which does not replace anything: you can still use your own. If you are a server owner who is already using a resourcepack: yes but you'll need to integrate your pack in Oraxen \(just drag and drop your files in the /pack folder of Oraxen\) ...or integrate the oraxen pack with yours \(but then you'ld have to do it everytime and that's a little stupid\).

## Does Oraxen replace items?

The goal of Oraxen is to add things to the game without losing features, so the short answer is no, however minecraft has some limitations \(you can't really add blocks or armors for example\), so we had to make a choice \(a choice that can be undone by disabling the related mechanics\):  
- by default leather amors will look a little different on body \(they will keep the same texture inside inventory though\)  
- new blocks will use vanilla unused mushroom stem block variations: this can create issues in constructions made using those unusual variations and look buggy if you place two mushroom stem blocks side-by-side \(this is just a display bug and that would be fixed by right clicking or disconnecting\).

## When I add an item, it breaks the textures of others already created

By default oraxen automatically set a custom model data to your items and generate it in the most optimized way.  Every item need to have a different model data, so when you add another item, it might break the others. In order to avoid this "issue" \(which is not really an issue for test servers, but might be problematic for a production servers\), enable the option `automatically_set_model_id` in **settings.yml**.

{% hint style="info" %}
Don't forget to reload the plugin with `/o reload` **AND** your resource pack using `/o pack getpack`\(you can also disconnect and reconnect to the server\)
{% endhint %}

## My textures work when I use optifine but not in vanilla

It is no longer possible to use upper case in textures or model names with vanilla since minecraft 1.11, however optifine still supports it. Please never use upper case to avoid problems.

## How to update Oraxen?

Here is a great video that can help you: [https://youtu.be/LkansZwVaPY](https://youtu.be/LkansZwVaPY)

## I would like to suggest a new feature or report an issue

First option: Login to github and submit an issue to the official repo: [git.io/oraxen](https://github.com/Th0rgal/Oraxen)

Second option: Join [the discord](https://discord.gg/4Qk5kBT9UX), get your Oraxen rank and go to the support or requests channel.







