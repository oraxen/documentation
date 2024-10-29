## Custom Armor - Armor Trims
If using trims as your custom-armor type, most things is handled automatically for you.\
Unlike with Core Shader method, trims aren't limited to just using LEATHER-materials.

By default, Oraxen is set to use CHAINMAIL, but this can be changed in `settings.yml`.\
Oraxen then generates a datapack based on your configured custom armors.\
Due to it requiring a datapack, the server needs to do a full restart any time you add/remove an armor-set.

{% hint style="danger" %}
After changing `CustomArmor.armor_type` to `TRIMS` you need to:
1. Start your server to let datapack be generated
2. Stop your server
3. Start it again to enable the previously generated datapack
   {% endhint %}

### How to configure your armor?

{% hint style="info" %}
Make sure that the itemID of your OraxenItem follows the pattern `armorname_armortype`.\
For the rest of the above set it would be `ruby_chestplate`, `ruby_leggings` and `ruby_boots`.

Make sure your armor-layer files follow the format of **armorname**_armor_layer_1/2.png.\
In the example below, we would need a **ruby**_armor_layer_1.png & **ruby**_armor_layer_2.png
{% endhint %}

Simply set the material and specify the texture-icon twice
```yaml
ruby_helmet:
  displayname: "<gradient:#FA7CBB:#F14658>Ruby Helmet"
  material: CHAINMAIL_HELMET
  Pack:
    generate_model: true
    parent_model: "item/generated"
    textures:
      - default/armors/ruby_helmet
      - default/armors/ruby_helmet
```

A trim-pattern is also necessary for the armor to display correctly.\
Oraxen will automatically assign it if it has not been manually specified.\
You can optionally manually assign the `trim_pattern` if you want to.\
The value should be `oraxen:armorname`, so in our example;
```yaml
ruby_helmet:
  trim_pattern: oraxen:ruby
```