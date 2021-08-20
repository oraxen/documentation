---
description: How to add new glyphs to the game?
---

# Glyphs

## What is a glyph?

A glyph is a textured unicode symbol. It can be used in any texts \(chat, item name, lore and more\). They can be used to do very, very powerful things \(custom inventories, extra bars\) but their simplest use is to be emoji.

## How to add a Glyph?

You first need to create a png texture. For example the heart.png file contained in `default/chat`.

![heart.png](../.gitbook/assets/heart%20%281%29.png)

You can then add your section to any yaml file from the glyphs directory. The code must be different for every glyph. This is the number that corresponds to the number of the unicode character that will be used. The texture is the path and name of the texture file. Height allows you to set the displayed character scale while ascent defines the vertical shift of the displayed result.

```yaml
heart:
  code: 3000
  texture: default/chat/heart
  ascent: 8
  height: 8
```

## How to use it in the chat?

You need to add a chat subsection to your glyph section:

```yaml
chat:
  placeholders:
    - "<3"
  permission: "oraxen.emoji.heart"
```

The placeholders can be used in chat by players with the required permission \(if permission is specified, it is not mandatory\).

## How to use it in item name or lore?

Any glyph can be used in name and lore of your item configurations.

```text
<glyph:heart>
```

Where heart is replaced by your glyph section name.

