---
description: How to add a custom hud element
cover: >-
https://cdn.discordapp.com/attachments/758785982005903431/1002544517158801418/unknown.png
coverY: 0
---

## Custom Huds

Currently, Oraxen supports the addition of one custom hud element.  
This is done through the Action Bar, meaning that any other plugin using it might interfere.  
In the future we will work on adding Mulitple Hud support for both the Action Bar and Boss Bar.

## Configuration
Below is an example of a "balance" hud defined in `hud.yml`.  
Keep in mind, this implementation of `shift` is a bit different from the normal one Oraxen provides.  
`shift:-10` moves your hud elements 10 pixels to the left, whilst `shift:10` moves it 10 pixels to the right.  

`font` is useful for adjusting the height of your text elements.  
Essentially this is the same as glyphs work, but will let you use normal text and placeholders.  
In the example below, we used a font that had its ascent set to -12.  
This font file will be included in the `Oraxen/pack/fonts` folder, and can be used as reference to adjust/make your own.

If you do not wish to use custom huds, you can easily disable it by setting `update_time_in_ticks` to 0.

```yaml
update_time_in_ticks: 40
huds:
  balance:
    permission: "oraxen.hud.balance"
    display_text: "<shift:160><font:balance_hud>%vault_eco_balance%<font:default>%oraxen_coin%"
    disabled_whilst_in_water: true # Oxygen can be hidden if this is placed right above food
    enabled_by_default: true
    enable_for_spectator_mode: true # By default, this is set to false
```
![hud](https://cdn.discordapp.com/attachments/758785982005903431/1002544517158801418/unknown.png)

## Commands
Players can toggle the hud on/off with the `/oraxen hud toggle <hud_name>` command.

