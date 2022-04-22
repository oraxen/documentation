---
description: Make Oraxen compatible with other plugins directly from the oraxen source code
cover: https://i.insider.com/61dc71461025b20018bb0597?width=700
coverY: 0
---

# Add Compatibility with a plugin

## How does it work?

### First Step: create a compatibility class

You need to create a class that extends

```
CompatibilityProvider<Main class of the plugin you want to add support>
```

and put the codes which add support for the plugin in the class you created.

### Second Step: add the compatibility class to Oraxen

Use

```
CompatibilitiesManager.addCompatibility(name of the plugin you want to add support, class you created in first step)
```

to add the class to Oraxen.

## Example

{% hint style="info" %}
&#x20;I'll use MythicMobs for this example.
{% endhint %}

### First Step: create a compatibility class

```
import io.lumine.xikage.mythicmobs.MythicMobs;
import io.lumine.xikage.mythicmobs.api.bukkit.events.MythicDropLoadEvent;
import io.th0rgal.oraxen.compatibilities.CompatibilityProvider;

public class MythicMobsCompatibility extends CompatibilityProvider<MythicMobs>{

    @EventHandler
    public void onMythicDropLoadEvent(MythicDropLoadEvent event) {
    
    }
    
}
```

### Second Step: add the compatibility class to Oraxen

```
import io.th0rgal.oraxen.compatibilities.CompatibilitiesManager;
import org.bukkit.plugin.java.JavaPlugin;

public class OraxenMythicMobsCompatibilityPlugin extends JavaPlugin {

    public void onEnable() {
        CompatibilitiesManager.addCompatibility("MythicMobs", MythicMobsCompatibility.class)
    }

}

```
