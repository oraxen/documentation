---
description: >-
    Guide on how to add custom Gestures/Emotes to your server
---
{% hint style="info" %}
Can be disabled in settings.yml under `Gestures.enabled`.\
This feature will cause issues with player-head textures, so keep that in mind
{% endhint %}
# Gestures

To add gestures to your server, you need a `.bbmodel` file which will contain the different animations.\
Then all you need to do is put this file inside `plugins/Oraxen/gestures` and start your server.\
The gesture can be played through the command `oraxen gesture filename.filename.animation_name`, which will naturally tabcomplete for you.\
Below is an example:\
![](https://media.discordapp.net/attachments/564158787108208640/1081645683758608556/image.png)
![](https://media.discordapp.net/attachments/564158787108208640/1081645683993493594/image.png)
The in-game command would then be: `/oraxen gesture backflip.backflip.backflip boy0000`

{% hint style="info" %}
If you or your players are seeing only the players head when playing an animation,\
this is most likely due to using either Optifine or Iris mods for shaders.\
These mods override the files added to the initial resourcepack, and unlike Custom Armor there is not a known way around it.\
![](https://cdn.discordapp.com/attachments/564158787108208640/1081647223793795152/image.png)
{% endhint %}
