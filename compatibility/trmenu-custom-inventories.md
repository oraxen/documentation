---
description: >-
  TrMenu is a free and opensource plugin which allows you to create custom
  inventory GUIs
---

# TrMenu - custom inventories

TrMenu doesn't only support Oraxen items, it allows you to easily use them inside your configurations. That way you can create cool icons for your item or directly display the content of a kit ...or create an incredibly cool menu with a custom texture.  
Spigot Link: [https://www.spigotmc.org/resources/trmenu-1-8-1-15.74284/](https://www.spigotmc.org/resources/trmenu-1-8-1-15.74284/)

## How to use an oraxen item as icon?

An oraxen item is not a default material so instead of using a default material name, you must use `<oraxen:item_id>` which gives something like that:

```yaml
  mats: '<oraxen:your_item_id>'
```

## How to use oraxen to create custom GUIs?

This concept was inspired by [a video from SimplySarc](https://www.youtube.com/watch?v=bv_wYNs5L6M) who showed that it was possible to create items with a so big texture that it could overlap the minecraft one. This allows you to create new GUIs without removing the exististing ones.

![Here is what it can look like](../.gitbook/assets/2020-03-11-203342_647x667_escrotum.png)

I recommend that you watch his video to fully understand the concept. You can then look at the gui.yml file to see two example items for creating a custom menu.

```yaml
example_upper_section:
  displayname: "&0"
  material: DIAMOND
  excludeFromInventory: true
  Pack:
    generate_model: false
    model: upper_section
```

This is the item for the upper\_section, it is using the default upper\_section model made by SimplySarc.

