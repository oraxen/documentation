---
description: Make Oraxen compatible with other plugins directly from the oraxen source code
---

# Add Compatibility with a plugin

## How does it work?

### First Step: create a compatibility class

You need to create a class that extends

```text
CompatibilityProvider<Main class of the plugin you want to add support>
```

and put the codes which add support for the plugin in the class you created.

### Second Step: add the compatibility class to Oraxen

Use

```text
CompatibilitiesManager.addCompatibility(name of the plugin you want to add support, class you created in first step)
```

to add the class to Oraxen.

## Example

{% hint style="info" %}
 I'll use MythicMobs for this example.
{% endhint %}

### First Step: create a compatibility class

```text
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

```text
import io.th0rgal.oraxen.compatibilities.CompatibilitiesManager;
import org.bukkit.plugin.java.JavaPlugin;

public class OraxenPlugin extends JavaPlugin {

    public void onEnable() {
        CompatibilitiesManager.addCompatibility("MythicMobs", MythicMobsCompatibility.class)
    }

}

```

