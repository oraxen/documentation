---
description: How to integrate your plugin with Oraxen
---

# API

## Add Oraxen to your plugin

In order to use Oraxen API, you need to add the jarfile to your classpath. You can use the jarfile downloaded on spigot or build it yourself from sources. You can also use github packages or jitpack.

## Github Packages \(recommended\)

{% hint style="success" %}
You can consult the list of available packages on the [dedicated github page](https://github.com/orgs/oraxen/packages?repo_name=Oraxen)
{% endhint %}

### With Maven \(from github documentation\):

To install an Apache Maven package from GitHub Packages, edit the _pom.xml_ file to include the package as a dependency. For more information on using a _pom.xml_ file in your project, see "[Introduction to the POM](https://maven.apache.org/guides/introduction/introduction-to-the-pom.html)" in the Apache Maven documentation.

1. Authenticate to GitHub Packages. For more information, see "[Authenticating to GitHub Packages](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-apache-maven-registry#authenticating-to-github-packages)."
2. Add the package dependencies to the `dependencies` element of your project _pom.xml_ file.

   ```text
   <dependencies>
     <dependency>
       <groupId>io.th0rgal</groupId>
       <artifactId>oraxen</artifactId>
       <version>1.77.1</version>
     </dependency>
   </dependencies>
   ```

3. Install the package.

   ```text
   $ mvn install
   ```

### With Gradle \(from github documentation\):

You can install a package by adding the package as a dependency to your project. For more information, see "[Declaring dependencies](https://docs.gradle.org/current/userguide/declaring_dependencies.html)" in the Gradle documentation.

1. Authenticate to GitHub Packages. For more information, see "[Authenticating to GitHub Packages](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-gradle-registry#authenticating-to-github-packages)."
2. Add the package dependencies to your _build.gradle_ file \(Gradle Groovy\) or _build.gradle.kts_ file \(Kotlin DSL\) file.

   ```text
   dependencies {
       implementation 'io.th0rgal:oraxen'
   }
   ```

3. Add the maven plugin to your _build.gradle_ file \(Gradle Groovy\) or _build.gradle.kts_ file \(Kotlin DSL\) file.

   Example using Gradle Groovy:

   ```text
   plugins {
       id 'maven'
   }
   ```

4. Install the package.

   ```text
   $ gradle install
   ```

## Jitpack

### With Maven

#### Repository \(jitpack\)

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
	    <groupId>com.github.Th0rgal</groupId>
	    <artifactId>Oraxen</artifactId>
	    <version>-SNAPSHOT</version>
	</dependency>
```

### With Gradle

#### Repository \(jitpack\)

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
	        implementation 'com.github.Th0rgal:Oraxen:-SNAPSHOT'
	}
```



## Examples of use

Oraxen is built around an ItemsBuilder class that allows you to create items easily. When the plugin starts it parses the configurations to generate builders for each type of items. Each builder can be used to generate itemstacks.

### [OraxenItems](https://github.com/Th0rgal/Oraxen/blob/master/src/main/java/io/th0rgal/oraxen/items/OraxenItems.java) class: 

#### Get an ItemBuilder from an OraxenID

```java
OraxenItems.getItemById(itemID); // where itemID is a section in items configurations
```

#### Check if an OraxenID exists

```java
OraxenItems.isAnItem(itemID);
```

#### Extract an OraxenID from an ItemStack

You can use to check if an ItemStack is an OraxenItem \(it will return null if OraxenID doesn't exist\)

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

#### Get access to the assets/ folder 

```java
ResourcePack.getAssetsFolder();
```

### Mechanics:

Oraxen allows you to add your own mechanics to the plugin, it is a little bit more complex than the rest, that's why there is a [dedicated tutorial](mechanics.md#how-does-the-mechanic-system-work).

