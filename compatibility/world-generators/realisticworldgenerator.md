---
description: RWG is a paid world generator
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966833048731660338/unknown.png
coverY: 0
---

# RealisticWorldGenerator

RealisticWorldGenerator allows you to easily generate a really cool looking world. Oraxen is not supported by the plugin (this means that the plugin does not contain any specific code for oraxen, allowing you for example to use Oraxen items in the default loots like dungeons, villages, etc) but this supports custom BlockDatas, so you can add custom minerals created with Oraxen to be generated like diamond for example.\
Spigot Link: [https://www.spigotmc.org/resources/realisticworldgenerator.15905/](https://www.spigotmc.org/resources/realisticworldgenerator.15905/)

## How to create custom ores / blocks

In this example we assume that you have added a block (an amethyst ore for example) following [this example](../../mechanics/block-mechanic.md#ores) to your oraxen configuration.

### Locate the file to edit

First you need to decide on which world you want to add your new ores (or create it). When you are ready, restart your server. A new folder inside ./plugins/RealisticWorldGenerator/worlds should have appear. You can now open it and find some files called "**ores.yml**", "**biomes.yml**" and "**replacement.yml**".

Depending on which version of RWG you're using there are different ways to add custom blocks to RWG. If you're using a version lower than or equal to 4.26.5 then you need to [follow the guide exactly beneath this sentence](realisticworldgenerator.md#adding-a-ore-in-rwg--4265). If you're using a version higher than that you need to [follow the guide below](realisticworldgenerator.md#adding-custom-blocks-in-rwg--4266).

### Adding a ore in (RWG <= 4.26.5)

You need to find your custom block data. This can be achieved using any minecraft version on a server running Oraxen. Just place your block (you can get it from the oraxen inventory of give it to yourself through a command) and press F3 while looking at the block you want to add.

![](../../.gitbook/assets/amethyst.png)

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

### Adding custom blocks in (RWG >= 4.26.6)

You need to chose what you want to do. In this example I will show it with the "**ores.yml**" file but it's the same for every file mentioned above in [Locate the file to edit](realisticworldgenerator.md#Locate-the-file-to-edit)

After opening the file you only need to add the block you want to add with the "**oraxen:**" namespace infront of it instead of "**minecraft:**"\
&#x20;This can look like this:

```yaml
  amethyst:
    min: 0
    chance: 2.0
    spawn: 
      min: 1
      max: 8
    material: oraxen:amethyst_ore
    max: 18
```

When it's finished, save the file, stop the server, deletes your old region files and restart the server.
