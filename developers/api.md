---
description: How to integrate your plugin with Oraxen
cover: >-
  https://www.techyon.es/media/news/full-stack-developer-cu%C3%81les-son-las-principales-competencias_1637600851_21.jpg
coverY: 0
---

# API

## Add Oraxen to your plugin

In order to use Oraxen API, you need to add Oraxen to your dependencies.\
Below are repository and dependency information.\
Replace `VERSION` with the Oraxen version you wish to use.\
The [latest release](https://github.com/oraxen/oraxen/releases/latest) can be found here.\

## Jitpack

## With Maven
#### Repository (jitpack)
```markup
<repository>
  <id>jitpack.io</id>
  <url>https://jitpack.io</url>
</repository>
```

#### Dependency
Because maven decides to be weird, you will need to exclude a lot of imports from Oraxen.\
This is not an issue when using Gradle
```markup
<dependency>
    <groupId>com.github.oraxen</groupId>
    <artifactId>oraxen</artifactId>
    <version>VERSION</version>
    <scope>provided</scope>
    <exclusions>
        <exclusion>
            <groupId>gs.mclo</groupId>
            <artifactId>mclogs</artifactId>
        </exclusion>
        <exclusion>
            <groupId>com.ticxo</groupId>
            <artifactId>PlayerAnimator</artifactId>
        </exclusion>
        <exclusion>
            <groupId>me.gabytm.util</groupId>
            <artifactId>actions-spigot</artifactId>
        </exclusion>
        <exclusion>
            <groupId>net.kyori</groupId>
            <artifactId>*</artifactId>
        </exclusion>
        <exclusion>
            <groupId>com.jeff_media</groupId>
            <artifactId>*</artifactId>
        </exclusion>
    </exclusions>
</dependency>
```

### With Gradle Kotlin
#### Repository (jitpack)
```kotlin
maven("https://jitpack.io")
```

#### Dependency
```kotlin
compileOnly("com.github.oraxen:oraxen:VERSION")
```

### With Groovy
#### Repository (jitpack)
```groovy
maven { url 'https://jitpack.io' }
```

#### Dependency
```groovy
compileOnly 'com.github.oraxen:oraxen:VERSION'
```

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
OraxenItems.isAnItem(itemID);
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

#### Get access to the assets/ folder&#x20;

```java
ResourcePack.getAssetsFolder();
```

### Mechanics:

Oraxen allows you to add your own mechanics to the plugin, it is a little bit more complex than the rest, that's why there is a [dedicated tutorial](mechanics.md#how-does-the-mechanic-system-work).
