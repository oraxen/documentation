## Custom Armor - Core Shaders
Oraxen alters this second texture by using colored leather armor and shaders.\
Armor has like every item a texture in the inventory and in the hand, but it also has a second texture when worn on the body\
This second appearance has some limitations and requires some practice. We will use a trick with leather armor and colors.

{% hint style="danger" %}
If you are using shaders via either the Optifine or Iris mod, you will need some additional steps.\
For Optifine, everything is handled automatically.\
For Iris, you also need [CIT Resewn](https://modrinth.com/mod/cit-resewn), everything else is handled for you.
{% endhint %}

![A: item appearance    B: body appearance](../../.gitbook/assets/stuff.png)

{% hint style="danger" %}
You must be careful when naming your armors to get the textures detected correctly.

If you want to create an **amethyst** armor set, then your item sections must be:  
\- **amethyst**_helmet  
\- **amethyst**_chestplate  
\- **amethyst**_leggings  
\- **amethyst**_boots  
\
And in [step 2](./#2-name-your-textures-correctly) you'll be able to create the textures:  
\- **amethyst**_armor_layer_1.png  
\- **amethyst**_armor_layer_2.png
{% endhint %}

#### How to configure your armor?

For this we will be using the below config example for reference:
```yaml
ruby_helmet:
  displayname: "<gradient:#FA7CBB:#F14658>Ruby Helmet"
  material: LEATHER_HELMET
  Pack:
    generate_model: true
    parent_model: "item/generated"
    textures:
      - default/armors/ruby_helmet
      - default/armors/ruby_helmet
```
{% hint style="info" %}
Make sure that the items ID, or the first line in the above example, follows the pattern `armorname_armortype`.  
For the rest of the above set it would be `ruby_chestplate`, `ruby_leggings` and `ruby_boots`.  
{% endhint %}

{% hint style="info" %}
This is also why LEATHER is the only material that works.\
Custom Armor can not be made with Diamond as the base material.\
To get custom armor amounts, simply add Attribute Modifiers.\
{% endhint %}

### How to change the equipped appearance?

Now the fun begins. We're going to use a vanilla shader to associate an armor style with a specific color.  
Thanks to [Ancientkingg](https://twitter.com/ancientkingg) for developing the shader used by Oraxen.

### 1) Create your textures

You'll have to create two textures for your armor. You can download the ruby example here:  
[https://oraxen.com/resources/armor\_rest.png](https://media.discordapp.net/attachments/758785982005903431/1009559045893537802/ruby_armor_layer_1.png)\
[https://oraxen.com/resources/armor\_leggings.png](https://media.discordapp.net/attachments/758785982005903431/1009559063815786626/ruby_armor_layer_2.png)

{% hint style="danger" %}
Make sure your armors resolution fits the value set in settings.yml.\
By default armor_resolution is set to 16. This means that your textures must be 64x32 pixels.\
If you want to use a higher resolution, you'll have to change the value in settings.yml.
For example armor_layer files with 128x64 pixels must have a resolution of 32 in settings.yml.\
You cannot have some at 64x32 and some at 128x64, it is either or.

Also make sure that the bit-depth of your textures is 32 bits.\
Anything else means not fully transparent, and the pixels the shader uses will be black.\
This will not break Optifine/Iris versions but will break all vanilla versions.
{% endhint %}

![](../../.gitbook/assets/leggings.png)


![](../../.gitbook/assets/armor.png)

{% hint style="success" %}
You can make your texture **emissive** (no optifine required) by adding another file with the same name ending in **\_e.png**. For example `ruby_armor_layer_1_e.png`  
This texture will be treated as an emissivity map, where the alpha of the pixel will be treated as the amount of emissivity.
{% endhint %}

### 2) Name your textures correctly

To get your textures registered correctly, their name need to contain `armor_layer_X`.  
For example:
`ruby_armor_layer_1.png` and`ruby_armor_layer_2.png`
You can put them in any folder of the pack textures, `~/textures/default/armors` is suggested.

