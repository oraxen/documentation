---
description: How to install and setup Oraxen on Paper or Spigot
icon: play
cover: https://images.polymart.org/resource/629/default.jpg
coverY: 0
layout:
  cover:
    visible: true
    size: full
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Getting started

## What Is Oraxen?

Oraxen is a Minecraft plugin which allows the creation of new items & blocks using custom textures and models. It also handles resourcepack generation, upload and storage (using Polymath), and is entirely open source with an extensible API.

## How Does It All Work?

When a Spigot server starts with Oraxen installed, the plugin will read all the item configurations (your .yml files inside /plugins/oraxen/items) and use them to generate .json models that link your .png textures to your new items. After this, Oraxen zips the resources using an optimized algorithm and uploads it to a polymath instance. Polymath is a free and opensource software written in Python to host Minecraft resourcepacks. By default Oraxen will use an Oraxen supplied Polymath instance, hosted in Switzerland on an oracle virtual private server. Whenever a player connects to your server, Oraxen will link them to the polymath instance which then sends them the resourcepack.

## Install Oraxen In Seconds!

Installing Oraxen is a fairly straight forward process:&#x20;

* Drop the Oraxen and [ProtocolLib](https://www.spigotmc.org/resources/protocollib.1997/) .jar files into your /plugins/ folder.
* Restart your server.

That's it! Although, we highly recommend heading into your settings.yml config and making any desired adjustments (then restarting once more) before continuing!

{% hint style="info" %}
Oraxen has been tested with Spigot and Paper 1.18 -> 1.21.4
{% endhint %}

For Minecraft 1.21.2+, using the latest version of Oraxen is advised. Oraxen is developed and designed for use with the [Paper](https://papermc.io/downloads/paper) server software. For older Minecraft versions, start by installing Oraxen 1.183.0 to get compatible configuration files. You can then update the jar file accordingly.
