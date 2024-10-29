---
description: How to create custom armors without replacing existing stuff?
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966823919917080626/unknown.png
coverY: 0
---

# Custom Armors
Just like other items, armor have a texture for when it is held or in your inventory, but also a texture for when a player equips it.\
Oraxen comes with three ways to add custom armor: COMPONENTS, TRIMS & SHADERS.\
COMPONENTS is for all 1.21.2+ servers and is the optimal choice for all supported servers.\
TRIMS is designed around the Armor-Trim system added in Minecraft 1.20, and will not work on earlier versions.\
SHADERS utilizes core-shaders, which were added in 1.17 (Disabled for all 1.21.2+ servers)

**Component** method is recommended for all servers 1.21.2+ in every scenario.\
There is no benefit to using Trims or Shader-methods for these servers.

**Armor-Trim** method is recommended if your server is 1.20-1.21.1 and only allows 1.20+ players.\
It has the benefit of not breaking with shaders / requiring extra mods to work.\
It also is not locked to only LEATHER armor-materials, by default using CHAINMAIL.

**Core-Shader** method is recommended if your server is below 1.20 or allow players on older versions.\
Compared to armor-trims this method breaks with shaders in Optifine & Iris mods.\
To fix this Oraxen generates CIT-textures into the pack.\
This works out-of-the-box with Optifine, but players using Iris will also need [CIT Resewn](https://modrinth.com/mod/cit-resewn).
