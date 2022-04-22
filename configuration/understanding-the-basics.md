---
description: A simple explanation of how oraxen works
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966825489098489856/unknown.png
coverY: 0
---

# Understand the basics

As you have seen previously, Oraxen is able to generate custom items but also the texture pack that goes with them. It also makes it possible to associate these items with special powers or capabilities known as mechanics.

## Color and other minecraft formatting

In the past minecraft only supported 16 colours and most plugins used a special format with the & character. Since 1.16 any colour can be used, and given the amount of formatting possible (clickable messages for example), I didn't want to restrict the plugin to these few options. That's why Guardian allows you to use the [MiniMessage format](https://docs.adventure.kyori.net/minimessage.html#format). That's what it looks like:

`<#FF5555>This is a <#55FF55>test!`

## Content of the Oraxen folder

![Directory tree structure of Oraxen folder](../.gitbook/assets/tree.png)

### Global configurations

At root of this configuration folder you'll find two files: settings.yml which contains various settings for Oraxen and mechanics.yml which contains global mechanics settings.

### Items configurations

The subfolder items contains all your created items. You can create a new item in any files and even create new files or remove existing ones: you can also do everything in a single file, but being able to store them in folders with explicit names should help you organize yourself.

### Resourcepack

The resource pack is a crucial element of oraxen and even if it is able to generate most of the files you will need, you will still have to provide the textures of the custom items yourself, all this is managed inside the Pack folder. You'll use the **textures** subfolder for adding textures and the **models** subfolder for adding models (if you want to use 3d items for example). You can also change the basic files of the pack (pack.mcmeta, pack icon, etc.) from the root of the pack folder. If you need to override a specific file from the pack, you can create an assets folder and put for example **assets/minecraft/sounds.json**.

### Recipes

This folder contains the configurations of the different recipes you have added sorted by recipe type. For example, shaped.yml will contain all your shaped recipes. You will rarely use this folder because it is easier and faster to generate this configuration directly from the game via the oraxen recipe commands.
