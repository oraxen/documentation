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
Below is an example of what a font-file should look like:

```json
{
  "providers": [
    {
      "type": "bitmap",
      "file": "minecraft:required/ascii_offset.png",
      "ascent": -13,
      "height": 8,
      "chars": [
        "\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000",
        "\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000",
        "\u0020\u0021\u0022\u0023\u0024\u0025\u0026\u0027\u0028\u0029\u002a\u002b\u002c\u002d\u002e\u002f",
        "\u0030\u0031\u0032\u0033\u0034\u0035\u0036\u0037\u0038\u0039\u003a\u003b\u003c\u003d\u003e\u003f",
        "\u0040\u0041\u0042\u0043\u0044\u0045\u0046\u0047\u0048\u0049\u004a\u004b\u004c\u004d\u004e\u004f",
        "\u0050\u0051\u0052\u0053\u0054\u0055\u0056\u0057\u0058\u0059\u005a\u005b\u005c\u005d\u005e\u005f",
        "\u0060\u0061\u0062\u0063\u0064\u0065\u0066\u0067\u0068\u0069\u006a\u006b\u006c\u006d\u006e\u006f",
        "\u0070\u0071\u0072\u0073\u0074\u0075\u0076\u0077\u0078\u0079\u007a\u007b\u007c\u007d\u007e\u0000",
        "\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000",
        "\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u00a3\u0000\u0000\u0192",
        "\u0000\u0000\u0000\u0000\u0000\u0000\u00aa\u00ba\u0000\u0000\u00ac\u0000\u0000\u0000\u00ab\u00bb",
        "\u2591\u2592\u2593\u2502\u2524\u2561\u2562\u2556\u2555\u2563\u2551\u2557\u255d\u255c\u255b\u2510",
        "\u2514\u2534\u252c\u251c\u2500\u253c\u255e\u255f\u255a\u2554\u2569\u2566\u2560\u2550\u256c\u2567",
        "\u2568\u2564\u2565\u2559\u2558\u2552\u2553\u256b\u256a\u2518\u250c\u2588\u2584\u258c\u2590\u2580",
        "\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u2205\u2208\u0000",
        "\u2261\u00b1\u2265\u2264\u2320\u2321\u00f7\u2248\u00b0\u2219\u0000\u221a\u207f\u00b2\u25a0\u0000"
      ]
    }
  ]
}
```

Just like with Glyphs, editing the ascent property adjusts the y-position of the text.\
This will offset the text roughly to where the hud is in the image example below.

To add in glyphs you can use both the normal placeholder via `%oraxen_glyphid%` or `<glyph:glyphid>`

If you do not wish to use custom huds, you can easily disable it by setting `update_time_in_ticks` to 0.

In case your HUD doesn't display despite being properly configured, try toggling it with: `/oraxen hud toggle` followed by your HUD's name (`/oraxen hud toggle balance`).

\
\#### Example hud.yml:

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
