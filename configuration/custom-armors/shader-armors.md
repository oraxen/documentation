---
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966825489098489856/unknown.png
coverY: 0
---

# Shader Armors

## Optifine

Oraxen armors are designed to work in Minecraft Vanilla but with Optifine shaders enabled the armors are distorted and we are going to see how to add compatibility to this.

### Configure Your Oraxen armor

In this case we are going to go for a basic example of Oraxen

```yaml
emerald_helmet:
  displayname: "<gradient:#89E59D:#37C6BA>Emerald Helmet"
  material: LEATHER_HELMET
  color: 3, 252, 136 #rgb
  Mechanics:
    durability:
      value: 437 # 20% more than diamond helmet
  AttributeModifiers:
    # - name: You don't really care about the name but it can be useful for some developers
    # - attribute: Get the list here: https://hub.spigotmc.org/javadocs/spigot/org/bukkit/attribute/Attribute.html
    # - operations: 0 for ADD_NUMBER, 1 for ADD_SCALAR, 2 for MULTIPLY_SCALAR_1;
    # - uuid: put a random uuid, generate one here: https://www.uuidgenerator.net/
    # - slot: HAND, OFF_HAND, FEET, LEGS, CHEST or HEAD
    - { name: "oraxen", attribute: GENERIC_MAX_HEALTH, amount: 2, operation: 0,
        uuid: 3a25f0b5-dbda-4e38-b097-9e75e37ae464, slot: HEAD }
    - { name: "oraxen", attribute: GENERIC_ARMOR, amount: 3, operation: 0,
        uuid: 3a25f0b5-dbda-4e38-b097-9e75e37ae464, slot: HEAD }
    - { name: "oraxen", attribute: GENERIC_ARMOR_TOUGHNESS, amount: 2, operation: 0,
        uuid: 3a25f0b5-dbda-4e38-b097-9e75e37ae464, slot: HEAD }
  Pack:
    generate_model: true
    parent_model: "item/generated"
    textures: # duplicate because we use the overlay of the leather armor
      - custom/default/armors/emerald_helmet
      - custom/default/armors/emerald_helmet
    custom_model_data: 50
```

In this case we created our ready-made armor with the CustomModelData 50 and our textures are located in `Oraxen/pack/textures/custom/default/armors` and I have these textures

![](https://cdn.discordapp.com/attachments/896841738621177896/967256019761762356/IMG\_20220422\_214959.png)

And I have everything ready

### Create the directory in your Oraxen folder

Create `Oraxen/pack/optifine/cit/armors/`directory And there I will create a copy of `emerald_armor_layer_1` and `emerald_armor_layer_2` and paste them in that folder but now with the names `emerald_layer_1` and `emerald_layer_2` and create a new file named `emerald.properties`

Inside that file we will add this

```properties
type=armor
items=leather_helmet\ leather_chestplate\ leather_leggings\ leather_boots
texture.leather_layer_1=emerald_layer_1
texture.leather_layer_1_overlay=emerald_layer_1
texture.leather_layer_2=emerald_layer_2
texture.leather_layer_2_overlay=emerald_layer_2
nbt.CustomModelData=50
```

In \
`texture.leather_layer_1=` and \
`texture.leather_layer_1_overlay=` we specify the texture layer\_1=. we specify texture layer\_1 \
`texture.leather_layer_2=` and \
`texture.leather_layer_2_overlay=` we specify the texture layer\_2 and e and at the end with \
`nbt.CustomModelData=` we specify the CustomModelData of the armor and this has to be done 1 time for the whole armor.\
And we'll be all set!

![](https://cdn.discordapp.com/attachments/896841738621177896/967258812954329118/IMG\_20220422\_220105.png)
