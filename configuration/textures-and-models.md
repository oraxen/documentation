---
description: How to customize your item appearance?
---

# Item Appearance

This folder \(./plugins/Oraxen/pack\) contains your pack. It works like a normal minecraft texture pack but simpler. You can drag your textures into the textures folder and your models into your models folder. You can also create sub-folders inside these folders to make it cleaner but it's not necessary. When the plugin generates the resource pack it appears in this folder under the name pack.zip.

### Create a simple 2d item

Put the textures that you need in the textures directory of the pack folder. You can then ask Oraxen to generate the model by superposing the textures :

```yaml
  Pack:
    generate_model: true
    parent_model: "item/handheld"
    textures:
      - example_image1.png #png extension is not needed
      - example_image2.png
```

The parent\_model field is required by minecraft. In fact this will allow your item to inherit the rendering properties of an item template from minecraft. You can look at the minecraft default models in order to find new ones but I personnaly use item/handheld for weapons like swords and item/generated for simple items or gems like amethysts.

You can also use an alternative way of declaring textures, especially nice when using block parent-models.\
```yaml
Pack:
  generate_model: true
  parent_model: "block/cube"
  textures:
    top: example_image.png
    side: example_image2.png
```

### Use a json model

Creating a json model can be time consuming but it allows you to create really cool things \(like 3d items\). It is really easy to integrate a json model with Oraxen : put your textures in your textures directory and your model in your models directory \(inside Oraxen/pack folder\). Then you can ask Oraxen to put this model on one of your items:

{% hint style="danger" %}
ALWAYS USE LOWER CASE FOR MODEL AND TEXTURE NAMES. Upper case is n longer supported by minecraft vanilla since 1.11 \(even though it still works for users using optifine\).
{% endhint %}

```yaml
  Pack:
    generate_model: false
    model: example_model.json #json extension is not mandatory
```

#### ⚠️ Pro tips when you use a json model!

Usually the templates you get place the textures in a folder, to make sure, open the json file and look at the first few lines, you should find something similar:

```javascript
{
	"__comment": "Designed by HighBridRed for Oraxen",
	"textures": {
		"particle": "custom/bonesword_palette",
		"texture": "custom/bonesword_palette",
		"bonesword_palette": "custom/bonesword_palette"
	},
	...
```

As you can see, the path to the texture is **custom/bonesword\_palette**, that means minecraft will be looking for a texture called **bonesword\_palette.png** in the folder "custom", so you need to create this folder inside "Oraxen/pack/textures". You can also remove "custom/" and keep the texture name only, so you just have to drag and drop it inside the textures folder without creating a subfolder.

### Use a blocking json model \(for shield\)

If you want to use a custom model for a shield, you need to specific the blocking model which will be used when a user right click using your shield, hopefully this is easy with Oraxen. Here is what it can look like:

```yaml
  Pack:
    generate_model: false
    model: example_shield.json #json extension is not mandatory
    blocking_model: example_shield_blocking.json #json extension is not mandatory
```

