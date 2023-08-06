# BurglaryDocs
- Documentation for the open source mod loader for "The Break In" called "Burglary"

## 1. Basic Addons
- Addons are just .NET assemblies.
- Whenever the preloader searches for addons, it looks in a folder, loads the assemblies, and looks through all types to see if it inherits "Addon" and has the "AddonData" attribute.

### **Step 1.**
- Make your main class inherit "Addon"
```cs
using Burglary.Addons;

namespace Example   {
    public class ThieveryMain : Addon {

    }
}
```

### **Step 2.**
- Add the "AddonData" attribute to the class.
```cs
using Burglary.Addons;
using Burglary.Addons.Attributes;

namespace Example {
    [AddonData("Example Addon","An Example Addon.","joeswanson.","1.0.0")] // recommended to use semantic versioning. this is not enforced.
    public class ThieveryMain : Addon {

    }
}
```

## ***OPTIONAL!***

### **Step 3.**
- Add the "Priority" attribute to make the addon load before others.
```cs
using Burglary.Addons;
using Burglary.Addons.Attributes;

namespace Example {
    [Priority(10)] // higher values load earlier
    [AddonData("Example Addon","An Example Addon.","joeswanson.","1.0.0")] // recommended to use semantic versioning. this is not enforced.
    public class ThieveryMain : Addon {

    }
}
```

## ***ADDON BAREBONES SOURCE REFERENCE (as of version 1.0.0; may not be updated.)***
```cs
namespace Burglary.Addons
{
    public abstract class Addon
    {
        public void Log(string message) {}
        public void Log(string message, ConsoleColor textColor) {}
        public void Log(string message, ConsoleColor textColor, ConsoleColor backColor) {}
        public void Error(string error_message) {}
        public void Warn(string warning) {}

        public virtual void OnBurglaryInitialize() { }
        public virtual void OnBurglaryUnload() { }
        public virtual void OnBurglaryLoad() { }
        public virtual void OnRegister() { }
        public virtual void OnSceneLoad(Scene scene) { }
        public virtual void OnSceneUnload(Scene scene) { }
        public virtual void OnSceneChanged(Scene before, Scene after) { }
        public virtual void OnUpdate() { }
        public virtual void OnFixedUpdate() { }
        public virtual void OnLateUpdate() { }
        public virtual void OnGUI() { }
    }
}
```
