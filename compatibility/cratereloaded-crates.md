---
description: Prime - HQ - Powerful - Active - Custom - Particles - Effects
---

# CrateReloaded - crates

This feature is provided to you by [yzl210](https://github.com/yzl210), don't hesitate to thank him!  
Spigot link: [https://www.spigotmc.org/resources/free-crate-reloaded-mystery-crate.861/](https://www.spigotmc.org/resources/free-crate-reloaded-mystery-crate-1-8-1-14-x.861/)

## Rewards

### Usage

`oraxen-item:(<oraxen item name> <item amount(optional, default is 1)>)`

### Example

```yaml
reward:
  rewards:
    - 'unique:(), chance:(1),   oraxen-item:(common_material 15)'
    - 'unique:(), chance:(0.1), oraxen-item:(rare_material), oraxen-item:(common_material 5)'
```

## Icon \(display\)

### Usage

`oraxen-display:(<oraxen item name> <item amount(optional, default is 1)>)`

### Example

```yaml
reward:
  rewards:
    - 'unique:(), chance:(1),    cmd:(heal {player}), oraxen-display:(heal_icon)'
    - 'unique:(), chance:(0.1), oraxen-item:(rare_material), oraxen-item:(common_material 5), oraxen-display:(rare_and_common_icon)'
```

