# Display Furniture

{% hint style="error" %}
This page is only relevant to server-versions 1.19.4 and above.\
Display Entity Furniture will only show for players on 1.19.4 and above.\
ViaVersion will not fix this.\
Oraxen must also be version 1.154.0 or above
{% endhint %}

{% hint style="error" %}
Keep in mind that changing old furniture configs is not a good idea.\
Already placed furniture that use ItemFrames will not be updated automatically and might break if the config changes.\
If you want to change the config, you should remove the furniture and place it again.\
In the future, we might make a command, system or plugin-addon to migrate old furniture to DisplayEntities / new configs
{% endhint %}

Display-Entities are a new entity type introduced in 1.19.4.\
It comes in a few different types: Item, Block and Interaction.\
Oraxen makes use of Item Display Entities and Interaction Entities for its furniture mechanic.\
With it, you can configure a bunch of stuff you previously could not.\
In addition to more options, it will also not cull, meaning it will not unrended at certain angles.\
This might lead to lower FPS for some players, but furniture will not vanish.

Below is an example of such a config:
```yml
cart:
  displayname: "<gray>Cart"
  material: PAPER
  Mechanics:
    furniture:
      type: DISPLAY_ENTITY
      hitbox:
        width: 0.4
        height: 0.3
      display_entity_properties:
        display_transform: NONE
        brightness:
          block: 15
          sky: 0
      barrier: true
  Pack:
    generate_model: false
    model: default/cart
```

### Furniture Type
First off, `type` is a new property added in Oraxern 1.154.0.\
It allows you to specify if you want to use the old ItemFrame type, or new Display Entity type.\
If your server allows players on versions below 1.19.4, we suggest sticking with ItemFrame, as the other will not be visible.\
If this property is not specified, it will default to ITEM_FRAME.\
The available options are: `ITEM_FRAME`, `GLOW_ITEM_FRAME` & `DISPLAY_ENTITY`

### Hitbox
Hitbox is also a new property as of Oraxen 1.154.0.\
This is regarding the new Interaction entity type.\
This entity is completely, has no collision and only functions as a hitbox.\
It can be used in addition to the old barrier mechanic.\
It has a `width` and a `height` property for defining the hitbox.\
![](https://media.discordapp.net/attachments/743544047733440582/1085341928004005918/image.png?width=998&height=910)

### Display Entity Properties
This section will detail the many options this new entity-type adds.\
Some are more useful than others, but I have added more or less all of them.\
Under `display_entity_properties` you can define these settings:\
`display_transform`, `tracking_rotation`, `brightness`, `view_range`, `shadow_radius`, `shadow_strength`, `scale`

The `display_transform` dictates how the model will be displayed.\
By default it is set to `NONE`, which will show it as it looks when you open the model in BlockBench.\
As some other plugins might use ArmorStands and add the furniture to its head, you can set this option to `HEAD` for the same effect.\
There is also: `FIRSTPERSON_LEFTHAND`, `FIRSTPERSON_RIGHTHAND`, `FIXED`, `GROUND`, `GUI`, `THIRDPERSON_LEFTHAND`, `THIRDPERSON_RIGHTHAND`.\
All of these will be displayed ingame as shown in BlockBench's Display Tab under the specified type.\
Look at [Furniture Position](furniture_position.md) for an example on FIXED (ItemFrame Position)

The `tracking_rotation`-property defines whether you want the furniture to "track" the player.\
This is mainly for stuff like billboard and leaderboards you want the player to see, not normal furniture.\
Options are:\
`FIXED` - No rotation\
`VERTICAL` - Pivots around vertical axis\
`HORIZONTAL` - Pivots around horizontal axis\
`CENTER` - Pivots around center point

The `brightness`-property is a way to have your furniture emit light.\
It has a `block` and `sky` property for the different types of lighting Minecraft has.
Config should look like this:
```yaml
display_entity_properties:
  brightness:
    block: 15
    sky: 0
```

The `scale`-property is a way to scale the furniture.\
It has a `x`, `y` and `z` property for scaling on each axis.
Config should look like this:
```yaml
display_entity_properties:
  scale:
    x: 1
    y: 1
    z: 1
```

`view_range`, `shadow_radius`, `shadow_strength` should be self-explanatory.
