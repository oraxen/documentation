---
description: How to integrate your plugin with Oraxen
cover: >-
  https://www.techyon.es/media/news/full-stack-developer-cu%C3%81les-son-las-principales-competencias_1637600851_21.jpg
coverY: 0
---

# API

## Add Oraxen to your plugin

In order to use Oraxen API, you need to add the jarfile to your classpath. You can use the jarfile downloaded on spigot or build it yourself from sources. You can also use github packages or jitpack.

## Jitpack

### With Maven

#### Repository (jitpack)

```markup
	<repositories>
		<repository>
		    <id>jitpack.io</id>
		    <url>https://jitpack.io</url>
		</repository>
	</repositories>
```

#### Dependency

```markup
	<dependency>
	    <groupId>com.github.oraxen</groupId>
	    <artifactId>oraxen</artifactId>
	    <version>-SNAPSHOT</version>
	    <scope>provided</scope>
	</dependency>
```

### With Gradle

#### Repository (jitpack)

```groovy
	allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}
```

#### Dependency

```groovy
	dependencies {
	        compileOnly 'com.github.oraxen:oraxen:-SNAPSHOT'
	}
```



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

### Place custom block [BlockMechanicFactory](https://github.com/oraxen/Oraxen/blob/master/src/main/java/io/th0rgal/oraxen/mechanics/provided/block/BlockMechanicFactory.java)

#### Set an OraxenBlock

You can set the model of a block by providing a block and the itemID of an item that implements the Block  mechanic.

```java
BlockMechanicFactory.setBlockModel(block, itemID);
```



### Add resources to the pack

#### Get access to the assets/ folder&#x20;

```java
ResourcePack.getAssetsFolder();
```

### Mechanics:

Oraxen allows you to add your own mechanics to the plugin, it is a little bit more complex than the rest, that's why there is a [dedicated tutorial](mechanics.md#how-does-the-mechanic-system-work).
