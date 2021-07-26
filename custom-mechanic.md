---
description: >-
  This mechanism allows you to realize an extremely customizable mechanism
  without programming
---

# Custom mechanic

## How does it work?

The mechanics let you create sub-sections composed of 3 parts:

* **Event**: when is this mechanic triggered? e.g. when you right click on a block
* **Conditions**: a set of conditions that must be satisfied. e.g. having a permission
* **Actions**: a set of actions to perform. e.g. send a command or a message

## A comprehensive example

```yaml
Mechanics:
  custom:
    test:
      event: "CLICK:right:all"
      conditions:
        - "HAS_PERMISSION:example.permission"
      actions:
        - "COMMAND:console:give <player> cooked_beef 1"
```

In this example, the subsection `test` defines a custom mechanic triggered when someone right click \(on a block or in the air\). If this player has the permission `example.permission`, the console will perform the give command and replace &lt;player&gt; by the player name.

