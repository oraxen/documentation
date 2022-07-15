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
  code: 3000 #To get the unicodes use this page 
  texture: default/chat/heart
  ascent: 8
  height: 8
```

{% embed url="https://unicode-table.com/en/search?q=3000" %}{% embed url="https://docs.oraxen.com/usage/commands#print-glyphs" %}

## Emoji List
To make a glyph appear under `/oraxen emoji list` you need to specify that it is one, like below.  
If not specified, this will default to `false`
```yaml
heart:
  texture: default/chat/heart
  is_emoji: true
```

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
It is essential and deleting the file would break the plugin

## PlaceHolderApi

### What's my glyph placeholder?

When you define a glyph in font.yml, you define a subsection. For example:



```
heart:
  code: 3000  
  texture: default/chat/heart
  ascent: 8
  height: 8
```

The section name is the glyph id. In this example the glyph id is `heart`, the placeholder is `%oraxen_glyphid%`, so in this example: `%oraxen_heart%`

### How do I use this in Luckperms

To use a glyph in a luckperms prefix, you need to get the raw unicode.  
You can use the following command to get the unicode from any glyph:  
`/oraxen printglyph glyph_id`  
This will copy the unicode to your clipboard.  
You can also replace glyph_id with `all` to get a list of all your glyphs.  
Below you can see what this looks like.  
If you click, say `[dye_menu]` it will copy its unicode and you can simply paste it where you need it.  
The glyph is also shown when you hover over the glyph-id.
![](https://user-images.githubusercontent.com/36164338/178945511-447ce8f7-28be-4687-bc02-8ef9b3f935ab.png)


### How do I use a glyph in name/lore of an item?
Any glyph can be used in name and lore of your item configurations.

```
<glyph:heart>
```

Where heart is replaced by your glyph section name.
