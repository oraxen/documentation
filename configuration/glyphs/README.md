---
description: How to add new glyphs to the game?
cover: https://i.imgur.com/T76ianD.png
coverY: 0
---

# 🌀 Glyphs

## What is a glyph?

A glyph is a textured unicode symbol. It can be used in any texts (chat, item name, lore and more). They can be used to do very, very powerful things (custom inventories, extra bars) but their simplest use is to be emoji.

## Configuring a Glyph

You first need to create a png texture. For example the heart.png file contained in `default/chat`.

![heart.png](<../../.gitbook/assets/heart (1).png>)

You can then add your section to any yaml file from the glyphs directory.\
A glyph has a few main properties, `texture`, `ascent`, `height` and `font`\
The texture is the path and name of the texture file in the format of `namespace:path`\
`height` is the scale of your glyph, height must also never be lower than ascent.\
`ascent` is the vertical offset of your glyph, and must be equal or lower than height.\
`font` is the font you want to use. If unspecified, `minecraft:default` will be used.\
It is generally adviced to set a font unless you want to use the glyph in Esc Menu, as that only accepts the default font.

```yaml
heart:
  texture: default/chat/heart
  ascent: 8
  height: 8
  font: namespage:fontname
```

### Multi-Bitmap glyphs

If you have a png consisting of several emotes, you can make it a multi-bitmap.\
This means you can, tie several glyphs to one image. This step requires some extra configuration to work however.\
In fonts.yml there is a section for `bitmaps`.\
Here you need to specify an `id`, which you will use in your glyph-configs.\
You also need to specify the path to the texture, as well as how many rows and columns the bitmap has.\
Below is an example of an entry in `fonts.yml`:

```yaml
bitmaps:
  example_bitmap:
    texture: example/example_bitmap
    rows: 4
    columns: 9
    ascent: 8
    height: 8
```

![](../../.gitbook/assets/example\_bitmap.png)

As you can see, the image shown above has 4 rows and 9 columns.\
The ascent and height property will be the one used for all glyphs tied to this bitmap.\
Now that you have your bitmap configured, you can link a glyphs to it.\
In your glyph config, you need to specify the bitmap id, as well as the row and column of the glyph you want to use.\
Below is an example of a glyph config using the bitmap above.

```yaml
example_glyph:
  texture: default/chat/example_glyph
  bitmap:
    id: example_bitmap
    row: 1
    column: 1
  #ascent: 8 # Not needed as bitmap specifies it
  #height: 8 # Not needed as bitmap specifies it
```

This will link the glyph to the first emoji on the first row in the image above.

### Emoji List

To make a glyph appear under `/oraxen emojis` you need to specify that it is one, like below.\
If not specified, this will default to `false`

```yaml
heart:
  texture: default/chat/heart
  is_emoji: true
```

It will also, by default, only show emojis the player has the permission for.\
In `settings.yml` you can toggle the `only_show_emojis_with_permission` setting.\
This will show all emojis to every player, and adds a hover-message indicating if they have permission or not. ![img](https://cdn.discordapp.com/attachments/758785982005903431/1002564595099111474/unknown.png)

## How to use it in the chat?

You need to add a chat subsection to your glyph section:

```yaml
chat:
  placeholders:
    - "<3"
  permission: "oraxen.emoji.heart"
```

The placeholders can be used in chat by players with the required permission (if permission is specified, it is not mandatory).

If it does not format your glyph in chat, change the `chat-handler` in settings.yml, as your chat-plugin is likely using `LEGACY` logic.

## How to make glyphs tabcomplete?

Simply set `tabcomplete: true` in the chat-section.\
If not specified, this will default to `false` Tabcompletion is currently only available for servers on 1.19.3 and above.

```yaml
chat:
  tabcomplete: true
  placeholders:
    - "<3"
  permission: "oraxen.emoji.heart"
```

## PlaceholderAPI

### What's my glyph placeholder?

The section name is the glyph id. In this example the glyph id is `heart`, the placeholder is `%oraxen_glyphid%`, so in this example: `%oraxen_heart%`\
Glyph-ID is the first line in any glyphs config, it is not the texturename or the placeholder.

### How do I use this in Prefixes / Luckperms

To add a glyph to a luckperms prefix, commonly to display ranks, simply add `%oraxen_glyphid%` to your prefix solution of choice.\
For example, if using LuckPerms, you can use the command: `/lp group default meta setprefix %oraxen_glyphid%` and it will replace it with the glyph.\
Because most plugins only parse the placeholders one time, the %luckperms\_prefix% will not be parsed again.\
You will most likely need to get the Utils-Expansion for PlaceholderAPI aswell.\
To get this, go to [this link](https://api.extendedclip.com/media/Utils-Expansion-1.0.1.jar), and place it in your plugins/PlaceholderAPI/expansions folder.\
Then in your plugin of choice use `%utils_parse:2_luckperms_prefix%` to parse the prefix again.\
\
**Keep in mind** your chatplugin must support PlaceholderAPI for this to work.\
If this does not work for whatever reason, you can always use the raw unicode from your glyph-config's `char`-property

### How do I use a glyph in name/lore of an item?

Any glyph can be used in name and lore of your item configurations, by using `<glyph:glyphid>`
