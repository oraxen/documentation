---
description: How to create custom armors without replacing existing stuff?
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966823919917080626/unknown.png
coverY: 0
---

# Custom Armors

Armor has like every item a texture in the inventory and in the hand, but it also has a second texture when worn on the body. This second appearance has some limitations and requires some practice. We will use a trick with leather armor and colors.

![A: item appearance    B: body appearance](../.gitbook/assets/stuff.png)

{% hint style="danger" %}
You must be careful when naming your armors to get the textures detected correctly.

If you want to create an **amethyst** armor set, then your item sections must be:\
\- **amethyst**\_helmet\
\- **amethyst**\_chestplate\
\- **amethyst**\_leggings\
\- **amethyst**\_boots\
\
And in [step 2](custom-armors.md#2-name-your-textures-correctly) you'll be able to create the textures:\
\- **amethyst**\_armor\_layer\_1.png\
\- **amethyst**\_armor\_layer\_2.png
{% endhint %}



## How to change the item appearance?

Because I'm using a simple 2d texture in the inventory, I will use the oraxen model generator. Since we use leather armor, we need to specify the overlay of a texture. That's why I wrote my texture name two times.

![textures/default/armors/ruby\_helmet.png](../.gitbook/assets/helmet.png)

I also specified a RGB color: `252, 3, 28`, which is equals to in hexadecimal: `#FC031C`. It's a beautiful red but I could've used anything.&#x20;

```yaml
ruby_helmet: # BE CAREFUL TO NAME IT armorsetname_armorpart
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

Now the fun begins. We're going to use a vanilla shader to associate an armor style with a specific color. I warmly thank Ancientkingg for developing the shader used by Oraxen.

### 1) Create your textures

You'll have to create two textures for your armor. You can download the ruby example here:\
[https://oraxen.com/resources/armor\_rest.png](https://oraxen.com/resources/armor\_rest.png)\
[https://oraxen.com/resources/armor\_leggings.png](https://oraxen.com/resources/armor\_leggings.png)

#### One for the leggings (40x32):

![](../.gitbook/assets/leggings.png)

#### **One for the rest of the armor (64x32):**

![](../.gitbook/assets/armor.png)

#### If you want to animate your armor, you can repeat the texture multiple time (one time per frame). To get about one second, you'ld need 24 frames. Here is an example with 3 frames:

![](../.gitbook/assets/animation.png)

{% hint style="success" %}
You can make your texture **emissive** (no optifine required) by adding another filed with the same name ending in **\_e.png**. For example `ruby_armor_layer_1_e.png`\
This texture will be treated as an emissivity map, where the alpha of the pixel will be treated as the amount of emissivity.
{% endhint %}

### 2) Name your textures correctly

To get your textures registered correctly, their name need to contain the string  `armor_layer_1` if this is the layer 1 and `armor_layer_2` if this is the layer 2. For example:

`ruby_armor_layer_1.png` and`ruby_armor_layer_2.png`

You can put them in any folder of the pack textures, `~/textures/default/armors` is suggested.

