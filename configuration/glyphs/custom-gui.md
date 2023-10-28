---
cover: >-
  https://images-ext-2.discordapp.net/external/lXJpPHHy3JFqjn9qU_JpNHjaP2edFMFvnQjuYvTghYE/https/mcmodels.net/wp-content/uploads/2022/01/image-1.png
coverY: 0
---

# Custom Gui

#### With Oraxen glyph you can create custom textured GUI's and here is an example

```yaml
customshop:
  texture: custom/default/custom/gui_tienda.png
  ascent: 13
  height: 256
```

The textures cannot be higher resolution than 256x256 and name of the texture must be all lowercase without spaces, as with all Resourcepack files.\
To adjust the horizontal position of your texture/glyph in the inventory, use the shift-tag. `<shift:-8>` for moving 8 pixels back, and `<shift:211>` for moving 211 pixels forward.

![](https://images-ext-2.discordapp.net/external/lXJpPHHy3JFqjn9qU\_JpNHjaP2edFMFvnQjuYvTghYE/https/mcmodels.net/wp-content/uploads/2022/01/image-1.png)

### How do I get the unicode for the glyph?
This really is not necessary as Oraxen will handle the `<glyph:glyph_id>` tag in any inventory / title.\
So to add this glyph in any other plugin, just set the title to be `<glyph:glyph_id>`.\
If you still want the raw unicode, you can find it in your glyphs config.

### How do I create an invisible item?

{% hint style="info" %}
Invisible elements are ideal for making clickable buttons. To create invisible elements, you will need to make an element with a transparent texture. An example here
{% endhint %}

```yaml
invisible_item:
  displayname: "<white>"
  material: PAPER
  Pack:
    generate_model: true
    parent_model: "item/generated"
    textures:
    - required/particle
```
