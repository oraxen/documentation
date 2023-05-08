---
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966825489098489856/unknown.png
coverY: 0
---

# Furtniture Position

If your server is using 1.19.4 or above, there is a new entity-type called Display-Entities.\
These entities have some additional properties related to furniture-position, that you should set.\
The main one being `display_transform`, which dictates what Transform it should use to display your item.\
You can get a better explanation [here](display_entity_furniture.md#Display-Entity-Properties).\
Below is an example of a furniture with the `type` set to `ITEM_FRAME` or `DISPLAY_ENTITY` with `display_transform` set to `FIXED`.

To start using furniture without it looking bad you need to adjust its position, let's say you used BlockBench to create the item then go to
![](https://hibiscuscreative.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fc051221b-af62-46a7-a988-c9fdaf3d9c47%2FUntitled.png?table=block&id=bb951dcd-f5c4-4a1d-a73b-a7cdb36d18f0&spaceId=d94d82a0-f00a-4f51-82f0-03722550c74d&width=1340&userId=&cache=v2)

Most often, furniture is done using invisible item frames. So, you’ll need to modify the translation settings for “Frame”.

![](https://hibiscuscreative.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F451c946e-fb1b-45c5-9738-be49b3fd4a5e%2FUntitled.png?table=block&id=07248014-959d-40c7-b9bd-74a038a3c361&spaceId=d94d82a0-f00a-4f51-82f0-03722550c74d&width=1440&userId=&cache=v2)

And you got it!
