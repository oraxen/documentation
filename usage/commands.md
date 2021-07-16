---
description: A simple explanation to use the plugin commands
---

# Commands

## General informations

All the oraxen commands start with the same label. This label, oraxen, has a few aliases so if you don't want to type `/oraxen` every time you can also use `/oxn` and even `/o` .

For this tutorial we will use /o because it is the shortest, but if this command is already used by another plugin or you can't use it for any reason, just replace the label of the commands starting with a /o by /oxn or /oraxen.

## Get the items

### For testing

The main benefit of this method is that it allows you to see all the items at the same time and therefore to be more efficient \(you just have to click on an item to make it appear in your inventory\). But you can't use it to automatically give an item to another player \(for example from the shop\).

#### Usage:

```yaml
/o inv sorted # Opens an inventory containing oraxen items sorted by file
/o inv all # Opens an inventory containing all oraxen items
```

#### Permissions:

```yaml
oraxen.command.inventory.view # Allows to view the inventory visualizer
oraxen.command.inventory.give# Allows to get item from the inventory visualizer
oraxen.command.inventory.* # Gives you the two previous permissions
```

### In order to give them

This command will be mainly useful if you want to give an item to another player or when you want to automate the give. If the target of this command has its inventory full, the stack will be looted on the ground.

#### Usage:

```yaml
/o give <player> <item> <amount> # Gives amount items to player
```

#### Permission:

```yaml
oraxen.command.give # Allows you to use /o give
```

## Repair

### Repair only one item

This command can be used to repair an item you hold in your main hand. You can configure the plugin to repair only items using oraxen custom durability or also vanilla durability.

#### Usage:

```yaml
/o repair hand # Repair the item you hold
```

#### Permissions:

```yaml
oraxen.command.repair # Allows to use the /o repair command
```

### Repair all items in your inventory

This command can be used to repair every single item in your inventory \(or in your armor slots\). You can configure the plugin to repair only items using oraxen custom durability or also vanilla durability.

#### Usage:

```yaml
/o repair all # Repair all your item (inside your inventory)
```

#### Permissions:

```yaml
oraxen.command.repair # so you are also able to use /o repair hand
oraxen.command.repair.all # Allows to use the /o repair all command
```

## Manage recipes

This command allows you to add new recipes to the configuration directly from the game using recipes builder. For more information on how to use it, see [Recipes](recipes.md). 

![Recipe showcase using /o recipe show all](../.gitbook/assets/recipe_showcase.png)

#### Usage:

```yaml
/o recipe builder <builder> # Creates a recipe builder of type <builder> and opens it
/o recipe save <name> # Saves your recipe with name <name>
/o recipe show all # Show you the loaded recipes
/o recipe show <recipe> # Show you one recipe
```

#### Permission:

```yaml
oraxen.command.recipes # Allows you to create new recipes via /o recipes
```

## Pack

This command allows you to interact with the Oraxen pack: send the configured message to download it from the internet or load it directly through the game.

#### Usage:

```yaml
/o pack send <player> # Send to <player> the pack directly through the game
/o pack msg <player> # Send to <player> the configured message
```

#### Permission:

```yaml
oraxen.command.pack # Allows you to use /o pack
```

## Reload

This command allows you to reload oraxen configurations quickly and without causing bugs \(you cannot reload oraxen using plugman\). However, it should be noted that for the time being, customs crafts created with oraxen cannot be reloaded.

#### Usage

```yaml
/o reload all # Reloads items configuration, Reloads recipes configuration, regenerates the pack and upload it
/o reload items # Reloads items configuration
/o reload pack # Regenerates resourcepack and upload it
/o reload recipes # Reloads recipes configuration
```

#### Permission:

```yaml
oraxen.command.reload # Allows you to use /o reload
```

## Debug

I wish you never have to use it but if you ever have a bug with Oraxen, I will probably ask you to execute this command to get more information about your installation.

#### Usage:

It will depend on the situation and will often change with the updates of oraxen, I will explain everything.

#### Permissions:

```yaml
oraxen.command.debug # Allows you to use /o debug
```

