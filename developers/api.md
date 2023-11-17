---
description: How to integrate your plugin with Oraxen
cover: >-
  https://www.techyon.es/media/news/full-stack-developer-cu%C3%81les-son-las-principales-competencias_1637600851_21.jpg
coverY: 0
---

# API

## Add Oraxen to your plugin

### Repository & Dependency Info
You can find the repository and dependency notice [here](https://github.com/oraxen/oraxen#api).

{% hint style="info" %}
All methods and better explanations of their functionality and parameters can be found in the actual Classes.\
Simply open them in your IDE to get a full list of them.
{% endhint %}

## Examples of use

Oraxen is built around an ItemsBuilder class that allows you to create items easily. When the plugin starts it parses the configurations to generate builders for each type of items. Each builder can be used to generate itemstacks.

### [OraxenItems](https://github.com/Th0rgal/Oraxen/blob/master/src/main/java/io/th0rgal/oraxen/items/OraxenItems.java) class:&#x20;

#### Get an ItemBuilder from an OraxenID

```java
OraxenItems.getItemById(itemID); // where itemID is a section in items configurations
```

#### Check if an OraxenID exists

```java
OraxenItems.exists(itemID);
OraxenItems.exists(itemStack);
```

#### Extract an OraxenID from an ItemStack

You can use to check if an ItemStack is an OraxenItem (it will return null if OraxenID doesn't exist)

```java
OraxenItems.getIdByItem(itemstack);
```

### Custom Blocks & Furniture

#### Place an OraxenBlock

Place an OraxenBlock at a given location
```java
OraxenBlocks.place(itemID, location)
```

Place an OraxenFurniture at a given location, optionally setting a player for rotation purposes
```java
OraxenFurniture.place(itemID, location, @Nullable player)
```



### Add resources to the pack

#### Adding files to the pack

```java
OraxenPack.addFilesToPack(fileArray)
```

### Mechanics:

Oraxen allows you to add your own mechanics to the plugin, it is a little bit more complex than the rest, that's why there is a [dedicated tutorial](mechanics.md#how-does-the-mechanic-system-work).
