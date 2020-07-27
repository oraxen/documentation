---
description: make Oraxen compatible with other plugins.
---

# Create your own Compatibility

## How does it work?

### First Step: create a compatibility class

You need to create a class that  extends  

```text
CompatibilityProvider<Main class of the plugin you want to add support>
```

and put the codes which add support for the plugin in the class.

### Second Step: add the compatibility class to Oraxen

```text
CompatibilitiesManager.addCompatibility(name of the plugin you want to add support, class you created in first step)
```

## Example

{% hint style="info" %}
 I'll use MythicMobs for this example.
{% endhint %}

### First Step: create a compatibility class

```text
import io.lumine.xikage.mythicmobs.MythicMobs;
import io.lumine.xikage.mythicmobs.api.bukkit.events.MythicDropLoadEvent;

public class MythicMobsCompatibility extends CompatibilityProvider<MythicMobs>{

    @EventHandler
    public void onMythicDropLoadEvent(MythicDropLoadEvent event) {
    
    }
    
}
```

### Second Step: add the compatibility class to Oraxen

```text
CompatibilitiesManager.addCompatibility("MythicMobs", MythicMobsCompatibility.class)
```

