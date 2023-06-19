---
description: MMoItems introduces very unique attack effect
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966832308395049000/unknown.png
coverY: 0
---

# MMoItems

The compatibility with MmoItems allows you to import items created with this plugin and use them as a base for your Oraxen items (you will keep everything configured with MmoItems and add your own mechanics, textures, 3d models, etc).

To do this, simply add an mmoitem section to your item section in Oraxen

```yaml
example_mmoitem:
  displayname: "<gradient:#59A7EA:#F1D2FF>Test"

  mmoitem:
    type: SWORD
    id: FALCON_BLADE
    level: 10 # Optional
    tier: RARE # Optional
    match_level: true # Optional
```

