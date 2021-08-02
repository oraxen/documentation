---
description: How to create custom armors without replacing existing stuff?
---

# Custom Armors

Armor has like every item a texture in the inventory and in the hand, but it also has a second texture when worn on the body. This second appearance has some limitations and requires some practice. We will use a trick with leather armor and colors.

![A: item appearance    B: body appearance](../.gitbook/assets/stuff.png)

## How to change the item appearance?

Because I'm using a simple 2d texture in the inventory, I will use the oraxen model generator. Since we use leather armor, we need to specify the overlay of a texture. That's why I wrote my texture name two times.

![~/pack/textures/default/armors/ruby\_helmet.png](../.gitbook/assets/helmet.png)

I also specified a RGB color: `252, 3, 28`, which is equals to in hexadecimal: `#FC031C`. It's a beautiful red but I could've used anything. 

```yaml
  displayname: "<gradient:#FA7CBB:#F14658>Ruby Helmet"
  material: LEATHER_HELMET
  color: 252, 3, 28
  Pack:
    generate_model: true
    parent_model: "item/generated"
    textures: # duplicate because we use the overlay of the leather armor
      - default/armors/ruby_helmet
      - default/armors/ruby_helmet
```

{% hint style="info" %}
You can use [this tool](https://www.rapidtables.com/convert/color/index.html) to convert colors from RGB to hex and vice versa
{% endhint %}

## How to change the body appearance?

