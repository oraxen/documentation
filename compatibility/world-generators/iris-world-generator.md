---
description: Iris is a paid world generator
---

# Iris World Generator

IrisWorldGenerator allows you to easily generate a really cool looking world. This supports custom BlockDatas, so you can add custom minerals created with Oraxen to be generated like diamond for example.  
Spigot Link: [https://www.spigotmc.org/resources/iris-world-gen-the-dimension-engine.84586/](https://www.spigotmc.org/resources/iris-world-gen-the-dimension-engine.84586/)

## How to create custom ores

In this example we assume that you have added a block \(an amethyst ore for example\) following [this example](../../block-mechanic.md#ores) to your oraxen configuration.

### 1\) Find your custom ore properties

Follow [this tutorial](./#find-your-ores-custom-block-data).

### 2\) Locate your dimension configuration

Go to `Iris/pack/YOUR_PACK_NAME/dimensions/YOUR_DIMENSION_NAME.json`, by default this should be: `Iris/packs/overworld/dimensions/overworld.json`

Then, open the file \(or the vscode workspace to enjoy the cool vscode integration\).

### 3\) Add your ore!

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
            "maxPerChunk": 3,
            "maxHeight": 30,
            "minPerChunk": 0,
            "minSize": 3,
            "maxSize": 6,
            "palette": [{"block": "note_block", "data": { "instrument" : "basedrum", "note" : 2, "powered" : false}}],
            "varience": 5
        },
```

You can now save the file, reset your world and restart!

