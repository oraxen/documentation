---
description: All the subtleties of item creation
---

# Items \(advanced\)

## Vanilla options

### displayname

Allows you to change the name displayed on the top of an item.

```yaml
  displayname: "&c&lExample" #example name
```

### material

Allows you to change the item type

```yaml
  material: WOODEN_SWORD
```

### injectID

Allows Oraxen to know recognise the item, it is by default set to true and you should not have to change it. If you do it anyway, the mechanics of the items will no longer work.

```yaml
  injectID: false
```

### excludeFromInventory

This option allows you to exclude an item from the oraxen inventory. It will no longer be displayed but you can still get it using [oraxen give command](../usage/commands.md#get-the-items). It is useful for items used in  other plugins like inventory icons.

```yaml
  excludeFromInventory: true
```

### durability

Allows you to change the number of damage of a item \(not very useful\)

```yaml
  durability: 10
```

### unbreakable

This will make your item unbreakable \(for real, using minecraft dedicated property\).

```yaml
unbreakable: true
```

### ItemFlags

Allows you to set ItemFlags to an item, get the list of available flags [here](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/inventory/ItemFlag.html).

```yaml
  ItemFlags:
    - HIDE_ENCHANTS
    - HIDE_ATTRIBUTES
    - HIDE_UNBREAKABLE
    - HIDE_DESTROYS
    - HIDE_PLACED_ON
    - HIDE_POTION_EFFECTS
```

### AttributeModifiers

Allows you to add minecraft attributes to your item. They are very powerful and allow you to make an item that adds hearts, increases the player's speed, etc. Get the list of available attributes [here](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/attribute/Attribute.html).

```yaml
  AttributeModifiers:
    # - name: You don't really care about the name but it can be useful for some developers
    # - attribute: Get the list here: https://hub.spigotmc.org/javadocs/spigot/org/bukkit/attribute/Attribute.html
    # - operations: 0 for ADD_NUMBER, 1 for ADD_SCALAR, 2 for MULTIPLY_SCALAR_1;
    # - uuid: put a random uuid, generate one here: https://www.uuidgenerator.net/
    # - slot: HAND, OFF_HAND, FEET, LEGS, CHEST or HEAD
    - {name: "oraxen_speed", 
       attribute: GENERIC_MOVEMENT_SPEED, 
       amount: 0.1, 
       operation: 0, 
       uuid: 3a25f0b5-dbda-4e38-b097-9e75e37ae464, 
       slot: HAND}
```

### Enchantments

If you want to enchant your item \(even with non vanilla levels like for example sharpness 15\), you can do it with this section. Get the list of available enchants [here](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/enchantments/Enchantment.html).

```yaml
  Enchantments:
    protection: 4
    flame: 34
    sharpness: 18
```

## Pack options

Unlike most other plugins that allow you to create custom items, oraxen supports the creation of a texture pack: that is, you can define directly in the configuration what you want your items to look like and it will take care of generating the pack. For minecraft, the appearance of each item is managed by a json file called the model. Most of the items have a very simple model that simply displays a two-dimensional texture. To avoid having to write this json file \(which is repetitive and boring\), you can ask Oraxen to generate it itself.

### The pack folder

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

### Use a json model

Creating a json model can be time consuming but it allows you to create really cool things \(like 3d items\). It is really easy to integrate a json model with Oraxen : put your textures in your textures directory and your model in your models directory \(inside Oraxen folder\). Then you can ask Oraxen to put this model on one of your items:

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

## Mechanics options

This part has a dedicated page, you can consult it [here](mechanics.md).

