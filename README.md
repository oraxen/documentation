---
description: How to install and setup Oraxen on Spigot
---

# Getting started

## What is Oraxen?

Oraxen is a minecraft plugin which allows to easily exploit new Minecraft  1.14 features in order to create new items with custom textures. It handles the resourcepack generation, upload \(using Polymath\) , is fully open source and has an extensible API.

## How does it work?

When a Spigot server starts with oraxen installed, the plugin will read all the item configurations and use them to generate json models to link your png textures to your items. It will zip the resources using an optimized algorithm and upload it to a polymath instance. Polymath is a free and opensource software written in Python to host minecraft resourcepacks. By default oraxen will use my own instance, hosted in Switzerland on an oracle virtual private server. When a player will connect to your server, oraxen will link him to the polymath instance which will server him the resourcepack.

## Install Oraxen in seconds

Installing Oraxen is a fairly straight forward process: drop Oraxen.jar and [ProtocolLib](https://www.spigotmc.org/resources/protocollib.1997/) to your /plugins/ folder and restart your server.

{% hint style="info" %}
Oraxen has been tested with Spigot and PaperSpigot 1.14+
{% endhint %}

Don't want to use ProtocolLib? You can use Oraxen without it but you'll have to disable some mechanics. You'll get the list soon.



