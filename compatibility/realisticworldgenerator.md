---
description: RWG is a paid world generator
---

# RealisticWorldGenerator

RealisticWorldGenerator allows you to easily generate a really cool looking world. Oraxen is not supported by the plugin \(this means that the plugin does not contain any specific code for oraxen, allowing you for example to use Oraxen items in the default loots like dungeons, villages, etc\) but this supports custom BlockDatas, so you can add custom minerals created with Oraxen to be generated like diamond for example.  
Spigot Link: [https://www.spigotmc.org/resources/realisticworldgenerator.15905/](https://www.spigotmc.org/resources/realisticworldgenerator.15905/)

## How to create custom ores

In this example we assume that you have added a block \(an amethyst ore for example\) following [this example](../configuration/block-mechanic.md#ores) to your oraxen configuration.

### Locate the file to edit

First you need to decide on which world you want to add your new ores \(or create it\). When you are ready, restart your server. A new folder inside ./plugins/RealisticWorldGenerator/worlds should have appear. You can now open it and find a file called "**ores.yml**".

### Find your ores' custom block data

You need to find your custom block data. This can be achieved using any minecraft version on a server running Oraxen. Just place your block \(you can get it from the oraxen inventory of give it to yourself through a command\) and press F3 while looking at the block you want to add.

![](../.gitbook/assets/image.png)

### Simply add a new ore using this blockdata

You can now easily add your new ore to the generation. In our example, this should look like that:

```yaml
  amethyst:
    min: 0
    chance: 2.0
    spawn:
      min: 1
      max: 8
    material: minecraft:mushroom_stem[up=false, down=false, north=false, south=false,
      west=true, east=false]
    max: 16
```

When it's finished, save the file, stop the server, deletes your old region files and restart the server.

