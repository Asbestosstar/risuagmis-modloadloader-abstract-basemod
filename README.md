# risuagmis-modloadloader-abstract-basemod

Maven coordinates:
com.asbestosstar:risugamis-modloader-abstract-basemod:0.0.1

Summary:
Provides a minimal BaseMod class containing only the abstract methods that Risugami’s ModLoader requires a mod to override.

Purpose:
This artifact is a small compatibility/bootstrap helper for creating simple mods that extend Risugami’s old ModLoader BaseMod class.

Risugami’s ModLoader loads classes whose names begin with mod_, checks that they extend BaseMod, creates an instance of the mod, then calls load(). It also uses getVersion() when reporting the loaded mod name and version. This library therefore provides only the required abstract BaseMod methods:

- load()
- getVersion()

This project is not a full reimplementation of Risugami’s ModLoader API. It does not attempt to expose or cleanly wrap ModLoader’s deeper functionality, because much of the original ModLoader class depends on obfuscated Minecraft classes and version-specific internals.

This artifact is mainly intended for very basic mods that only need a clean BaseMod type so the mod class can compile and bootstrap correctly.

Basic usage:

1. Add the dependency to your project.

Maven:

<dependency>
    <groupId>com.asbestosstar</groupId>
    <artifactId>risugamis-modloader-abstract-basemod</artifactId>
    <version>0.0.1</version>
</dependency>

2. Create a mod class whose name starts with mod_.

Example:

public class mod_Example extends BaseMod {

    @Override
    public String getVersion() {
        return "1.0.0";
    }

    @Override
    public void load() {
        System.out.println("Example mod loaded.");
    }
}

3. Build your mod jar.

4. Place the mod jar where Risugami’s ModLoader expects mods to be loaded.

5. Start Minecraft with the matching Risugami ModLoader version installed.

Important limitation:
This artifact is only a minimal BaseMod abstraction. It is useful for simple bootstrap-style mods, but it should not be treated as a complete ModLoader development API. If your mod needs blocks, items, recipes, rendering, packets, GUI hooks, world generation, key bindings, or other deep ModLoader features, you will still need the actual version-specific ModLoader/Minecraft classes, many of which are obfuscated.

Intended use:
Use this when you only need a simple BaseMod class for making basic Risugami ModLoader-compatible mods without depending directly on the full decompiled ModLoader source.
