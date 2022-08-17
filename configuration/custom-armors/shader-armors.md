---
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966825489098489856/unknown.png
coverY: 0
---

# Shader Armors

## Optifine & Iris

Oraxen's custom armor mechanic is designed to work in Vanilla Minecraft. It's not compatible with Optifine or Iris out of the box.  
Since other shaders will take priority over the ones in Oraxen's Resourcepack, you need to do some additional steps.  

{% hint style="danger" %}
If you are using Iris, and not Optifine, for shaders, you will also need the [CIT Resewn](https://modrinth.com/mod/cit-resewn) mod.  
This mod adds the CIT, or Custom Item Texture, system from Optifine to Iris.  
{% endhint %}

### Setup for custom shader armor

First step is to create the folders `Oraxen/pack/optifine/cit/armors/`.  

You then want to copy your `armor_layer_1.png` and `armor_layer_2.png` files to this folder.  
In this example we would copy `emerald_armor_layer_1.png` and `emerald_armor_layer_2.png` to this folder.  
Next, rename these files to `emerald_armor_layer_1.png` and `emerald_armor_layer_2.png` into `emerald_layer_1` and `emerald_layer_2`.

Finally, you need to create a file called `emerald.properties` in this folder.  
Open this in NotePad or any other text editor.  
Then add the following lines:

```properties
type=armor
items=minecraft:leather_helmet minecraft:leather_chestplate minecraft:leather_leggings minecraft:leather_boots
texture.leather_layer_1=emerald_layer_1
texture.leather_layer_1_overlay=emerald_layer_1
texture.leather_layer_2=emerald_layer_2
texture.leather_layer_2_overlay=emerald_layer_2
nbt.CustomModelData=1
```
Of course, you will need to replace `emerald` with your armor name, and CustomModelData with the one your armor is tied to.  
If you don't know what CustomModelData your armor has, you can use the following command: `/oraxen iteminfo emerald_helmet`
Though it is recommended to specify this yourself in the armors config file, you can let Oraxen distribute this automatically like all other items.  

<b>Then you are done!</b>  
Your final folder should look somehting like this.
Simply start up your server and the armor should work both with and without shaders!

![](https://cdn.discordapp.com/attachments/896841738621177896/967258812954329118/IMG\_20220422\_220105.png)
