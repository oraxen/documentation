---
description: How to create custom recipes using Oraxen
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966826759293136996/unknown.png
coverY: 0
---

# Recipes

Recipes are ways that already exist in minecraft that allow players to create items from others. The craft table allows you to craft swords, armors and more, the crafts of these items are called ShapedRecipes because they are recipes with a particular shape. There are also ShapelessRecipes (you just have to put the ingredients in any order to get your result) or FurnaceRecipes (to obtain the item by burning the ingredient in a furnace). The objective of oraxen is to be able to support them all but for the moment only shaped recipes are supported.

## How to create a recipe?

You can see the list of commands and permissions required in the [wiki page](commands.md#create-recipes).

### First step: open a builder inventory

Start by typing **/o recipe builder SHAPED**, it will open you a crafting table:

Then place the ingredients in the order you want in the left part. Place the wanted result in the slot on the right.

### Damn, I'm missing an ingredient, can I close the inventory?

Absolutely, you can close the inventory at any time, to reopen it simply type **/o recipes open** (you will find the items you left in it).

### I finished my craft, how to load it?

You must register your craft. To do this, you must choose a name, then type the command **/o recipes save your\_name**. Unfortunately Oraxen does not yet know how to load these crafts in game, it will be necessary to wait for the server to restart before using them.

{% hint style="info" %}
You can also use **/o recipes save \<name> \<permission>** so that crafting your item with the name \<name> requires the permission \<permission>
{% endhint %}

## How to edit my recipe?

You can simply edit the configuration with the name of your craft type (shaped.yml for example), then find your craft and change the ingredients, result or permission.
