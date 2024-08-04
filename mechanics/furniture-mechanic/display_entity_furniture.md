# Display-Entity Furniture

Display-Entities comes in a few different types: Item, Block and Interaction.\
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
      display_entity_properties:
        display_transform: NONE
        brightness:
          block_light: 15
          sky_light: 0
      barrier: true
  Pack:
    generate_model: false
    model: default/cart
```

###
