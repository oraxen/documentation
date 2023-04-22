---
description: How to add new glyphs to the game?
cover: https://i.imgur.com/T76ianD.png
coverY: 0
---

# Glyphs

## What is a glyph?

A glyph is a textured unicode symbol. It can be used in any texts (chat, item name, lore and more). They can be used to do very, very powerful things (custom inventories, extra bars) but their simplest use is to be emoji.

## How to add a Glyph?

You first need to create a png texture. For example the heart.png file contained in `default/chat`.

![heart.png](<../../.gitbook/assets/heart (1).png>)

You can then add your section to any yaml file from the glyphs directory. The code must be different for every glyph. This is the number that corresponds to the number of the unicode character that will be used. The texture is the path and name of the texture file. Height allows you to set the displayed character scale while ascent defines the vertical shift of the displayed result.

```yaml
heart:
  texture: default/chat/heart
  ascent: 8
  height: 8
```

## My glyphs don't work?

This is likely due to misconfiguration of the glyphs' config.  
Please check your console for any errors, as it should tell you exactly which glyph is misconfigured and how it is.
![](https://user-images.githubusercontent.com/62521371/185404681-e0c1a881-e30b-446a-9f33-20dd88bae27c.png)

## Emoji List
To make a glyph appear under `/oraxen emojis` you need to specify that it is one, like below.  
If not specified, this will default to `false`
```yaml
heart:
  texture: default/chat/heart
  is_emoji: true
```
It will also, by default, only show emojis the player has the permission for.  
In `settings.yml` you can toggle the `only_show_emojis_with_permission` setting.  
This will show all emojis to every player, and adds a hover-message indicating if they have permission or not.
![img](https://cdn.discordapp.com/attachments/758785982005903431/1002564595099111474/unknown.png)
## How to use it in the chat?

You need to add a chat subsection to your glyph section:

```yaml
chat:
  placeholders:
    - "<3"
  permission: "oraxen.emoji.heart"
```

The placeholders can be used in chat by players with the required permission (if permission is specified, it is not mandatory).

## How to make glyphs tabcomplete?
Simply set `tabcomplete: true` in the chat-section.  
If not specified, this will default to `false`
```yaml
chat:
  tabcomplete: true
  tab_icon_texture: "something" # Not recommended to change from default unless you know how
  tab_icon_signature: "something" # Not recommended to change from default unless you know how
  placeholders:
    - "<3"
  permission: "oraxen.emoji.heart"
```
You can also change the icon displayed in tablist if you want to.  
Simply change the `tab_icon_texture` and `tab_icon_signature` fields.  
Unless you know how to get textures and signatures, it is recommended to leave them unspecified.

## Do not remove shifts.yml
This file is used elsewhere in the default pack and removing it improperly will make the plugin fail to load.  
There is no real reason to delete this file. It will simply be recreated on startup.  
If you know what you are doing, changes made inside the file will not be overwritten, only if deleting the file.
Same applies to `interface.yml`. They are used in for example language files, so deleting them means those fail.

### My shift glyph does not move anything?
This is commonly because the shift-glyphs are set to use a transparent image.\
For example, if you edit the null.png in `Oraxen/pack/textures/required` to be transparent.\
Shifts cannot use a transparent image, and your image used for them needs to be atleast a 1x1 pixel.\

## PlaceholderAPI

### What's my glyph placeholder?
The section name is the glyph id. In this example the glyph id is `heart`, the placeholder is `%oraxen_glyphid%`, so in this example: `%oraxen_heart%`

### How do I use this in Prefixes / Luckperms
To add a glyph to a luckperms prefix, commonly to display ranks, simply add `%oraxen_glyph_id%` to your prefix solution of choice.\
For example, if using LuckPerms, you can use the command: `/lp group default meta setprefix %oraxen_glyph_id%` and it will replace it with the glyph.\
Keep in mind your chatplugin must support PlaceholderAPI for this to work.\
An alternative, though not adviced, is to use the raw unicode as described below.


### How do I get the raw unicode of a glyph?
You can use the following command to get the unicode from any glyph:  
`/oraxen printglyph glyph_id`  
This will copy the unicode to your clipboard.  
You can also replace glyph_id with `all` to get a list of all your glyphs.  
Below you can see what this looks like.  
If you click, say `[dye_menu]` it will copy its unicode, and you can simply paste it where you need it.  
The glyph is also shown when you hover over the glyph-id.
![](https://user-images.githubusercontent.com/36164338/178945511-447ce8f7-28be-4687-bc02-8ef9b3f935ab.png)

### How do I use a glyph in name/lore of an item?
Any glyph can be used in name and lore of your item configurations.

```
<glyph:heart>
```

Where heart is replaced by your glyph section name.
