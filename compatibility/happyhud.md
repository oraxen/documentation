---
description: HappyHUD lets you make really customizable HUDs
---

# HappyHUD Compatibility

This will just detail how to properly make HappyHUD compatible with Oraxen in a few easy steps.\
To do so follow these steps:

1. Set `action_bar: false` in settings.yml
2. Set `hide_scoreboard_numbers: false` in settings.yml
3. Delete `Oraxen/pack/shaders/core/render_text.vsh` and `render_text.json` if they exist.
4. In HappyHud's config, enable `copy-resource-pack` and set `path: "../Oraxen/pack/assets"` (HappyHUD 2.7-SNAPSHOT and
   above)

{% hint style="danger" %}
If you really want to also hide scoreboard numbers,\
you can manually merge Oraxens shader file into HappyHUDs\
in `HappyHUD/pack/minecraft/shaders/core/`.
{% endhint %}
