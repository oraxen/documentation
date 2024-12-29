---
hidden: true
---

# CustomBlockExpansion

This is an addon for Oraxen that adds several new CustomBlock types.\
It allows for custom doors, trapdoors, stairs, slabs and transparent blocks.\
Below will be examples for each of the different types

{% hint style="warning" %}
This is currently not released fully, but is available in the Discord for verified Oraxen-Buyers Note that each of the types are currently limited to only 4 variations.
{% endhint %}

{% hint style="danger" %}
This addon relies on Waxed Copper Blocks to work.\
The addon attempts to re-add this logic by marking "Fake Waxed Copper" blocks.\
If you do not care about letting players wax copper, you can disable this in `plugins/Oraxen_CustomBlockExpansion/config.yml` for some performance gain.
{% endhint %}

{% hint style="danger" %}
Care should also be taken to convert your existing world.\
As of 1.21, trial chambers generate with Waxed Copper blocks, which might cause some unintended issues.\
Please use the WorldConverter tool below to fix your world
{% endhint %}

### Custom Stairs

```yaml
custom_stair:
  material: PAPER
  itemname: Custom Stair
  Pack:
    generate_model: true
    parent_model: block/stairs
    textures:                      # Example if one wants different textures
      bottom: block/reinforced_deepslate_bottom
      side: block/reinforced_deepslate_side
      top: block/reinforced_deepslate_top
  Mechanics:
    custom_stair:
      custom_variation: 1          # 1-4 are available
      model: custom_stair          # the itemid of your item, unless you provided a model not textures
```

### Custom Slabs

```yaml
custom_slab:
  material: PAPER
  itemname: Custom Slab
  Pack:
    generate_model: true
    parent_model: block/slab
    textures:
      bottom: block/reinforced_deepslate_bottom
      side: block/reinforced_deepslate_side
      top: block/reinforced_deepslate_top
  Mechanics:
    custom_slab:
      custom_variation: 1          # 1-4 are available
      model: custom_slab          # the itemid of your item, unless you provided a model not textures
```

### Custom Doors

Door-setup is a bit different than the other blocks, as it requires two configs.\
This is because the item-model in hand will look incorrect if it uses the block-parent-models\
The second config is just so that Oraxen generates the necessary models\
If you provide your own json-model, you can skip the second config\\

ItemConfig for held item:

```yaml
custom_door:
  material: PAPER
  itemname: Custom Door
  Pack:
    generate_model: true
    parent_model: item/generated   # This is used for the item when held in hand
    textures:
      - item/oak_door        # The texture to use for the item in hand
  Mechanics:
    custom_door:
      custom_variation: 1          # 1-4 are available
      model: custom_door_placed    # The itemid of the second config, that generates the block-model
```

ItemConfig for placed-block:

```yaml
custom_door_placed:
  # Handles the generation of the model the placed blocks should use
  # This is the same as all other block-types use in their Pack section
  # But split apart due to how held door-items work
  Pack:
    generate_model: true
    parent_model: block/door_bottom_left        # Default parent-model for doors
    textures:
      bottom: block/reinforced_deepslate_bottom
      top: block/reinforced_deepslate_top
  # Extra properties to prevent item from being "registered" as an OraxenItem
  injectID: false
  excludeFromInventory: true
  excludeFromCommands: true
```

### Custom Trapdoors

```yaml
custom_trapdoor:
  material: PAPER
  itemname: Custom Trapdoor
  Pack:
    generate_model: true
    parent_model: block/template_orientable_trapdoor_bottom
    textures:
      texture: block/reinforced_deepslate_side
  Mechanics:
    custom_trapdoor:
      custom_variation: 1         # 1-4 are available
      model: custom_trapdoor      # The itemid of the second config, that generates the block-model
```

### Custom Transparent

This type allows for transparent blocks, useful for leaves etc.\
For normal blocks that do not require transparency, use [NoteBlock Mechanic](../mechanics/custom-block-mechanics/noteblock-mechanic/)

```yaml
custom_grate:
  material: PAPER
  itemname: Custom Grate
  Pack:
    generate_model: true
    parent_model: block/cube_all
    textures:
      - block/reinforced_deepslate_side
  Mechanics:
    custom_grate:
      custom_variation: 1          # 1-4 are available
      model: custom_grate          # The itemid of the second config, that generates the block-model
```
