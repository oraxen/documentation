# Component Based (1.21.2+)

If using COMPONENTS as your custom-armor type, you are not limited in any way, unlike TRIMS & SHADER.\
Unlike SHADER this method does not break with shader-mods and is not restricted to LEATHER\_ARMOR items.\
It also has the benefit of not needing to be based on an armor-item at all, use PAPER if you want to.\
Every downside there has been to earlier methods is now gone, no restrictions.

## How to configure your armor?

{% hint style="info" %}
Make sure that the itemID of your OraxenItem follows the pattern `armorname_armortype`.\
For the rest of the above set it would be `ruby_chestplate`, `ruby_leggings` and `ruby_boots`.

Make sure your armor-layer files follow the format of **armorname**\_armor\_layer\_1/2.png.\
In the example below, we would need a **ruby**\_armor\_layer\_1.png & **ruby**\_armor\_layer\_2.png
{% endhint %}

Simply set the material you want, no need to specify the texture-icon twice:

```yaml
ruby_helmet:
  displayname: "<gradient:#FA7CBB:#F14658>Ruby Helmet"
  material: PAPER
  Pack:
    generate_model: true
    parent_model: "item/generated"
    textures:
      - default/armors/ruby_helmet
```

An Equippable-Component is also necessary for the armor to display correctly.\
Oraxen will automatically assign it if it has not been manually specified.\
You can optionally manually assign the component if you want to.\
The value should be `oraxen:armorname`, so in our example;

```yaml
ruby_helmet:
  Components:
    equippable:
      slot: HEAD
      model: oraxen:ruby
```
