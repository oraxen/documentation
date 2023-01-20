---
description: Iris is a paid world generator
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966832733290627072/unknown.png
coverY: 0
---

# Iris World Generator

IrisWorldGenerator allows you to easily generate a really cool looking world. This supports custom BlockDatas, so you can add custom minerals created with Oraxen to be generated like diamond for example.\
Spigot Link: [https://www.spigotmc.org/resources/iris-world-gen-the-dimension-engine.84586/](https://www.spigotmc.org/resources/iris-world-gen-the-dimension-engine.84586/)

## How to create custom ores

In this example we assume that you have added a block (an amethyst ore for example) following [this example](../../mechanics/noteblock-mechanic/#ores) to your oraxen configuration.

### 1) Locate your dimension configuration

Go to `Iris/pack/YOUR_PACK_NAME/dimensions/YOUR_DIMENSION_NAME.json`, by default this should be: `Iris/packs/overworld/dimensions/overworld.json`

Then, open the file (or the vscode workspace to enjoy the cool vscode integration).

### 2) Add your ore!

Locate this part of the config:

```yaml
    "ORES": "All settings in regards to deposits. Contains the ores spawning in your world.",
    "deposits": [
        {
            "minHeight": 19,
            "maxPerChunk": 4,
            "maxHeight": 150,
            "minPerChunk": 1,
            "minSize": 25,
            "maxSize": 25,
            "palette": [{"block": "granite"}],
            "varience": 2
        },
```

Add your own config using the custom ore properties found at step one. For example:

```yaml
    {
      "minHeight": 2,
      "maxPerChunk": 2,
      "maxHeight": 30,
      "minPerChunk": 0,
      "minSize": 3,
      "maxSize": 6,
      "palette": [{ "block": "oraxen:amethyst_ore" }],
      "varience": 5
    },
```

You can now save the file, reset your world and restart!
