---
description: Various options impacting the plugin in its generality
---

# Plugin settings

## Cosmetic configurations

You can change the name and prefix of the plugin \(used in messages\) in the Plugin section. You can use & codes 

## Pack

Oraxen integrates with Polymath \(a custom web server written in Python especially to be compatible\). You can download the source code [here](https://github.com/Th0rgal/Polymath/) and host it yourself or use the provided instance \(atlas\). You can also integrate with [your own custom hosting service](../developers/custom-hosting-service.md).

## Pack receiving

This section allows you to easily perform actions depending on the resource pack status of your players.

You can send message \(through a KICK, the chat, an actionbar or a title\) and specify a delay and a period \(between the different messages if you are using an actionbar or a title\).

```yaml
receive:
  enabled: true

  loaded:
    actions:
      message:
        enabled: true
        # KICK / CHAT / ACTION_BAR / TITLE
        type: ACTION_BAR
        # Delay before the first message to appear, this is in seconds
        delay: 0
        # You only need a period if you send multiple messages of type ACTION_BAR or TITLE
        period: -1
        # Click and Hover elements are only available by using the CHAT type
        messages:
          - "&a&lResourcePack successfully loaded!"

      # If you need to send commands
      commands:
        console: []
        player: []
        opped_player: []

  accepted:
    actions:
      message:
        enabled: true
        # KICK / CHAT / ACTION_BAR / TITLE
        type: TITLE
        # Delay before the first message to appear, this is in seconds
        delay: 0
        # You only need a period if you send multiple messages of type ACTION_BAR or TITLE
        period: 3
        # Click and Hover elements are only available by using the CHAT type
        messages:
          - "&a&lResourcePack accepted!"
          - "Thank you"
      # If you need to send commands
      commands:
        console: []
        player: []
        opped_player: []

  denied:
    actions:
      message:
        enabled: true
        # KICK / CHAT / ACTION_BAR / TITLE
        type: CHAT
        # Delay before the first message to appear, this is in seconds
        delay: 0
        # You can put any value here because this is a CHAT message
        period: -1
        # Click and Hover elements are only available by using the CHAT type
        messages:
          - "<red>You refused the ResourcePack, but you need it in order to see the new items. Please </red><click:run_command:/oraxen pack><hover:show_text:\"<green>Display more informations\"><green><bold>CLICK HERE</bold></hover></click> <red>or type <bold>/o pack"
      # If you need to send commands
      commands:
        console: []
        player: []
        opped_player: []

  failed_download:
    actions:
      message:
        enabled: true
        # KICK / CHAT / ACTION_BAR / TITLE
        type: CHAT
        # Delay before the first message to appear, this is in seconds
        delay: 0
        # You can put any value here because this is a CHAT message
        period: -1
        # Click and Hover elements are only available by using the CHAT type
        messages:
          - "<red>You failed to download the ResourcePack, but you need it in order to see the new items. Please </red><click:run_command:/oraxen pack getpack><hover:show_text:\"<red>/!\\ loading the resourcepack from the game can cause lags\"><red><bold>CLICK HERE</bold></hover></click> <red>to retry or type <bold>/o pack</bold> and download it from the internet"
      # If you need to send commands
      commands:
        console: []
        player: []
        opped_player: []
```



