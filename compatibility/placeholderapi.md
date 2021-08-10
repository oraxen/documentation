---
description: Use oraxen glyphs in other plugins easily
---

# PlaceholderAPI

PlaceholderAPI is a plugin/library that allows servers the use of placeholders from a wide range of your favorite plugins collectively. Essentials, Factions, LuckPerms, Vault, AutoSell, GriefPrevention, etc.... You can display information from Oraxen in any plugin that supports PlaceholderAPI.

## What's my glyph placeholder?

When you define a glyph in font.yml, you define a subsection. For example:

```yaml
heart:
  code: 3000
  texture: default/chat/heart
  ascent: 8
  height: 8
```

The section name is the glyph id. In this example the glyph id is `heart`, the placeholder is `%oraxen_glyphid%`, so in this example: `%oraxen_heart%`

