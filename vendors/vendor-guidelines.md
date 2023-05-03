---
description: Guidelines for vendors to follow when creating packs for Oraxen.
---

# Vendor Oraxen Guide

## Introduction
Oraxen has several ways to let you integrate your MCModels pack with it.\
This guide will cover the different ways you can do this.\
Depending on the type of pack, be that Furniture, Custom Blocks or Custom Items, you will need to use slightly different configs.\
In your downloadable pack it is recommended to have a dedicated folder for Oraxen configs and other files.\
This makes it easy for users to simply drag and drop files into their Oraxen folder.\

## Common Pack-structure guidelines
Both the `model` and `textures`-properties are the relative path to `plugins/Oraxen/pack/models(or textures)/`.\
So the above model file would be located in `plugins/Oraxen/pack/models/packname_or_something/model_file.json`.\
If you want to use another namespace, you should put your files into `plugins/Oraxen/pack/assets/NAMESPACE/models(or textures)/`.\
Then in the config the format for `model` and `textures` are `NAMESPACE:filepath`.

No model, texture or filepath should at any point contain Capital Letters or spaces.\
This is not formatting that resourcepacks past 1.13 support (though Optifine does).\
1. `assets/namespace/models/SOMETHING/my model.json` X
2. `assets/namespace/models/something/my model.json` X
3. `assets/namespace/models/something/my_model.json` ✓

Textures should also be a maximum of 256x256 pixels.\
This is all basic resourcepack stuff, but it has happened enough that I feel a need to point it out.\

Whenever possible it is recommended to not import paper.json and other base-material files.\
These are the Nr.1 issue in support and can be avoided by making very basic OraxenItem configs.\
Essentially, Oraxen generates these into the final pack, if one or more OraxenItem configs uses that material.\
This will make it easier to properly handle CustomModelData and mitigate most support issues for this.

## Common config properties
CustomModelData is the most common pitfall of pack-conflicts.\
Several packs tend to use the same materials and same CustomModelData values.\
Oraxen has several methods it handles this.\
1. If the config has no specified Pack.custom_model_data, Oraxen will assign the highest unused value based on the `material`
   1. This value is not saved to the config, see below point, and vendors are adviced to leave it as such
   2. If the `automatically_set_model_data` setting in `settings.yml` is enabled, this value will be saved to the config
   3. Vendors should have this disabled and not specify a value for the CustomModelData in the configs, to let Oraxen assign an unused one
2. Due to ModelEngine using `LEATHER_HORSE_ARMOR` as it's default property, it is adviced to not use this for configs.
   1. Use another dyeable item like `TIPPED_ARROW` or `POTION` for best compatibility
3. If you are making Custom Armor, be aware that different resolutions cannot be combined
   1. Meaning any pack that adds 128x64 armor will not work with 64x32 armor
   2. The user should also be informed that they need to change the `armor_resolution` setting to match the pack they are using
   3. This should be set to the height-pixel count of the armor_layer files / 2. (128x64 = 32, 64x32 = 16 (default))
   4. Armor is very strict on formatting, and you are adviced to make sure you follow the guidelines in the [Armor](../configuration/custom-armors/README.md) section.

## Custom Items
Custom Items are the most common type of pack, and the easiest to integrate with Oraxen.\
All you really need is a config file for your items, and a folder for all resourcepack files.\
The config file should be put in Oraxen/items and can be named whatever.\
For clarity, it is recommended to name it the same as your pack.\
The config file should look something like this:
```yaml
my_example_item:
  displayname: "<red>My Example Item"
  material: PAPER
  Pack:
    generate_model: false
    model: packname_or_something/model_file
```

This is the most basic of examples.\
If you are using 2D items, your `Pack`-section should look like this instead:
```yaml
Pack:
  generate_model: true
  parent_model: "item/generated"
  textures:
    - packname_or_something/texture_file
```

Optionally, the textures-property can take a specific base-name:
```yaml
Pack:
  generate_model: true
  parent_model: "item/generated"
  textures:
    top: packname_or_something/top
    bottom: packname_or_something/bottom
    side: packname_or_something/side
```
Mostly used directional custom blocks, as you can specify the side, top, bottom textures more easily.\
Basically this relies on the `parent_model`, so if you have a custom entry there, you can also use this.
`parent_model` follows the same structure as `model` and `textures`, so you can use `NAMESPACE:filepath` if you want to.

## Custom Blocks
Custom Blocks are essentially just Custom Items, with one of the Block Mechanics added.\
This means that you can use the same config as above, but with the addition of the `Mechanics`-section.\
There are 2 types of Block-Mechanics, `noteblock` and `stringblock`.\
`noteblock` is essentially for anything that should be a normal block, like stone, wood, dirt, etc.\
`stringblock` is primarily aimed towards plants, flowers and other decorations as they have no collision.\

### NoteBlock
The `noteblock`-mechanic is the most common one, and is used for most blocks.\
The config for this should look something like this:
```yaml
my_example_block:
  displayname: "<red>My Example Block"
  material: PAPER
  Pack:
    generate_model: true
    parent_model: "block/cube_all"
    textures:
      - something/texture_file
  Mechanics:
    noteblock:
      custom_variation: 1
      model: something/model_file
```

The `custom_variation`-property is used to distinguish between all the custom blocks and must be unique.\
Unlike `custom_model_data` this is not automatically assigned, and you must specify it yourself.\
The decision here is that since it is placed in the world, the user should have control over it.\
Perhaps in the future it will be assigned automatically. If you include a README, you should make note of this.\

The `model`-property is the same as the one in the `Pack`-section, and follows the same rules.\
If had `generate_model` enabled as you specified textures, the model would be your item-id, so `my_example_block`.\
There are also additional sub-mechanics, like custom sounds, hardness and more.\
You can read more about them in the [NoteBlock Mechanics](../mechanics/noteblock-mechanic/README.md) and its other pages.

### StringBlock
The `stringblock`-mechanic is used for blocks that should not have collision.\
This is primarily used for plants, flowers and other decorations.\
The config for this should look something like this:
```yaml
my_example_block:
  displayname: "<red>My Example Block"
  material: PAPER
  Pack:
    generate_model: true
    parent_model: "block/cross"
    textures:
        - something/texture_file
  Mechanics:
    stringblock:
      custom_variation: 1
      model: something/model_file
```
As you can see it is very similar to the `noteblock`-mechanic.\
The sub-mechanics can be found in the [StringBlock Mechanics](../mechanics/stringblock-mechanic/README.md) and its other pages.


## Custom Furniture
Furniture is mostly used when wanting to make 3D modelled stuff like chairs, tables etc.\
The config for this should look something like this:
```yaml
my_example_furniture:
  displayname: "<red>My Example Furniture"
  material: PAPER
  Pack:
    generate_model: false
    model: packname_or_something/model_file
  Mechanics:
    furniture:
      type: DISPLAY_ENTITY
      hitbox:
        width: 1.0
        height: 1.0
      display_entity_properties:
        display_transform: FIXED
      barrier: true
```
There are a few more properties as you can see.\
The `type`-property is used to specify what type of furniture it is.\
The options are `DISPLAY_ENTITY`, `ITEM_FRAME`, `GLOW_ITEM_FRAME` and `ARMOR_STAND`.\
`DISPLAY_ENTITY` is a new type as of 1.19.4, and will only work on 1.19.4 servers and above.\
It is recommended to set this to it either way, as it will be automatically converted to `ITEM_FRAME` on older versions.\
This type has more properties and allows for better hitboxes and performance.\

The `hitbox`-property is used to specify the hitbox of the furniture.\
This is only useful on 1.19.4+ servers, and spawns what is called an Interaction Entity.\
Think of it like just a hitbox, used for detecting hitting and interacting with the furniture.\
This one does however not have collision, for that you need the `barrier`-property.\

The `display_entity_properties`-property is used to specify the properties of the `DISPLAY_ENTITY`.\
The `display_transform`-property is used to specify the transform of the item.\
The options are `FIXED`, `HEAD`, `BODY`, `LEFT_ARM`, `RIGHT_ARM`, `LEFT_LEG`, `RIGHT_LEG` and `GROUND`.\
Essentially this is all the options in BlockBenches `Display`-tab.\
If you want compatibility between ITEM_FRAME and DISPLAY_ENTITY, you should use `FIXED`.\
ItemsAdder would be the same as using `HEAD` due to ArmorStands being its preferred entity-type.\
You can find the rest of the [Display-Entity Properties](../mechanics/furniture-mechanic/display_entity_furniture.md).

The `barrier`-property is used to specify if the furniture should have collision or not.\
This will place a normal barrier block at the furniture origin.\
You can place multiple barriers by following this format:
```yaml
Mechanics:
  furniture:
    barriers:
        - { x: 0, y: 0, z: 0 }
        - { x: 0, y: 1, z: 0 }
```    

## Custom Sounds
Some packs might include custom sounds for ambience, mobs or other things.\
When possible it is recommended to use another namespace for this.\
This is because Oraxen creates a sounds.json based on the `sound.yml` file by default, and this can cause conflicts.\
If the usecase allows for custom namespaces, simply add your sounds.json to `Oraxen/pack/assets/namespace/` and add the sound-files to `Oraxen/pack/assets/namespace/sounds`-folder.\

If the usecase needs to be in the normal minecraft namespace, you should not include a sounds.json.\
Instead add entries into Oraxens sound.yml file for optimal compatibility.\
Then simply add the sound-files into the `Oraxen/pack/assets/minecraft/sounds` folder.\
