### An unofficial speed-optimized fork of erdelf's Minify Everything, a mod that makes every building minifiable.

Rimworld 1.6 has made every minified object tickable. The original Minify Everything works around this by adding a switch that globally disables or enables ticking for minified objects. However, disabling it prevents ticking where it's *intentional*; and enabling it causes minified objects to throw errors instead. Also, the implementation of the original mod's global switch is a patch that runs on every thing for every tick. Even a small patch has overhead, and multiplying that patch hundreds of thousands of times has a heavy performance cost.

This mod has a couple differences from the original:

- Pre-existing minifiable objects are free to tick or not tick with their author's intent. This allows Vanilla behavior like batteries discharging while minified.
- Minified objects added by this fork are now a custom subclass of `MinifiedThing`. This lets them selectively disable ticking depending on Minify Everything's "allow ticking buildings" setting. When loading a save, newly-added minified objects are automatically converted to the custom subclass. Pre-allowed minified objects are unaffected by this fork.

### Compatibility:

- Safe to add to existing saves and/or replace the original.
- Works with submods of the original Minify Everything. The changes are all internal.
- Should be compatible with everything it was compatible with previously. I'd say it's more compatible with Vanilla and other mods now, because it won't affect their pre-allowed miniaturized objects.

Quoting the [original mod's Steam page](https://steamcommunity.com/sharedfiles/filedetails/?id=872762753):

> Note: Sometimes reinstall won't work, and you have to uninstall and install it.
>
> Note: This is extremely experimental. Sometimes it won't work exactly, but in most cases it will. You'll have to test to find out what works and what not.

This is an experimental fork of an experimental mod. I'll keep it consistent with upstream patches if they're reasonable and I have time, but use at your own risk (like any mod). You can read the author's opinions on these changes [here](https://web.archive.org/web/20260213202238/https://github.com/erdelf/MinifyEverything/pull/21).

### Regarding removal:

In the original Minify Everything, removing the mod leaves unintended minified objects in the map. In 1.6, this causes those objects to start throwing ticking errors. With this mod, newly-added minified objects are a custom subclass, so removing the mod also removes these objects from the map. This prevents the objects from throwing errors when the mod no longer prevents them from ticking.

**You can prevent the removal and still avoid ticking errors by installing unintended minified objects somewhere before removing the mod.**

### License:

Published under the [original mod's MIT License](https://github.com/Aussiemon/MinifyEverything/blob/master/license).

Feel free to contribute pull requests and issues to this fork. Don't send issues to the original repository if you're not using the original mod.