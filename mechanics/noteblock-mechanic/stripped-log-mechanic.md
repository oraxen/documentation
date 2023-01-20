---
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966827878706708560/unknown.png
coverY: 0
---

# Stripped Log Mechanic

{% hint style="info" %}
only for 1.134.0+
{% endhint %}

## What is this?

This mechanic allows you to strip custom logs in to stripped version, like in vanilla.


### Configuration

```yaml
Mechanics:
    noteblock:
      custom_variation: 2
      logStrip:
        stripped_log: stripped_log #block that will change in to
```

#### Drop after stripping

```yaml
Mechanics:
    noteblock:
      custom_variation: 2
      logStrip:
        stripped_log: stripped_log #block that will change in to
        drop: bark #additonal drop after right click mechanic
```

{% embed url="https://youtu.be/ohiGtlz_who" %}
