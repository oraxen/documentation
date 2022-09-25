---
description: >-
  Currently, Oraxen supports the addition of one custom hud element. This is
  done through the Action Bar, meaning that any other plugin using it might
  interfere. In the future we will work on adding Mul
cover: >-
  https://cdn.discordapp.com/attachments/758785982005903431/1002544517158801418/unknown.png
coverY: 0
---

# Custom HUD

### Configuration

Below is an example of a "balance" hud defined in `hud.yml`.\
Keep in mind, this implementation of `shift` is a bit different from the normal one Oraxen provides.\
`<shift:-10>` moves your hud elements 10 pixels to the left, whilst `<shift:10>` moves it 10 pixels to the right.

`font` is useful for adjusting the height of your text elements.\
Essentially this is the same as glyphs work, but will let you use normal text and placeholders.\
In the example below, we used a font that had its ascent set to -12.\
This font file will be included in the `Oraxen/pack/fonts` folder, and can be used as reference to adjust/make your own.

To add in glyphs you can use both the normal placeholder via `%oraxen_glyphid%` or `<glyph:glyphid>`



If you do not wish to use custom huds, you can easily disable it by setting `update_time_in_ticks` to 0.\


#### Example hud.yml:

```yaml
update_time_in_ticks: 40
huds:
  balance:
    permission: "oraxen.hud.balance"
    display_text: "<shift:100><font:balance_hud>%vault_eco_balance%<font:default><glyph:coin>"
    disabled_whilst_in_water: true # Oxygen can be hidden if this is placed right above food
    enabled_by_default: true
    enable_for_spectator_mode: true # By default, this is set to false
```

\


<figure><img src="https://cdn.discordapp.com/attachments/758785982005903431/1002544517158801418/unknown.png" alt=""><figcaption><p>Result of above example</p></figcaption></figure>
