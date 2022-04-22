---
cover: >-
  https://images-ext-2.discordapp.net/external/lXJpPHHy3JFqjn9qU_JpNHjaP2edFMFvnQjuYvTghYE/https/mcmodels.net/wp-content/uploads/2022/01/image-1.png
coverY: 0
---

# Custom Gui

#### With Oraxen ghyph you can create custom GUI's and here is an example

```yaml
customshop:
  texture: custom/default/custom/gui_tienda.png
  ascent: 13
  height: 256
  code: 5088
```

The textures must be maximum 256x256 and normally they will look a bit uneven in the GUI, so you must use the Oraxen shifts that in your case is `%oraxen_shift_8%` or `%oraxen_shift_16%` and before that you must use the letter `&f` in the configuration.

![](https://images-ext-2.discordapp.net/external/lXJpPHHy3JFqjn9qU\_JpNHjaP2edFMFvnQjuYvTghYE/https/mcmodels.net/wp-content/uploads/2022/01/image-1.png)

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

{% hint style="info" %}
To add a custom CustomModelData use after the `pack`
{% endhint %}

```yaml
    custom_model_data: 321
```
