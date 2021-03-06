# Linen

A set of free and open mappings for Alpha versions of Minecraft.

(So basically Yarn but for Alpha)

## Usage
To use linen-deobfuscated Minecraft for Minecraft modding or as a dependency in a Java project, you can use [loom](https://github.com/fabricmc/fabric-loom) Gradle plugin. See [fabric wiki tutorial](https://fabricmc.net/wiki/tutorial:setup) for more information.

To obtain a deobfuscated Minecraft jar, [`./gradlew mapNamedJar`](#mapNamedJar) will generate a jar named like `<minecraft version>-named.jar`, which can be sent to a decompiler for deobfuscated code.

## Contributing

Please remember that copying and pasting mappings from alternate projects under more restrictive licenses (such as MCP, Spigot's or Mojang's obfuscation maps)
is **completely forbidden** without explicit permission from the owners of said mappings to distribute the names under the CC0 license.
This includes using the names from those mappings for inspiration. Discussing the naming approaches used in said projects
is also not welcome - you have been warned. However, it is a good idea to consult name changes with other people - use pull requests or our community spaces to ask questions!

Please have a look at the [naming conventions](/CONVENTIONS.md) before submitting mappings.

### Getting Started

1. Fork and clone the repo
2. Run `./gradlew linen` (Linux, macOS) or `gradlew linen` (Windows) to open [Enigma](https://github.com/FabricMC/Enigma), a user interface to easily edit the mappings
3. Commit and push your work to your fork
4. Open a pull request with your changes

## Gradle
Linen uses Gradle to provide a number of utility tasks for working with the mappings.

### `linen`
[`setupLinen`](#setupLinen) and download and launch the latest version of [Enigma](https://github.com/FabricMC/Enigma) automatically configured to use the merged jar and the mappings.

Compared to launching Enigma externally, the gradle task adds a name guesser plugin that automatically map enums and a few constant field names.

### `build`
Build a GZip'd archive containing a tiny mapping between official (obfuscated), [intermediary](https://github.com/FabricMC/intermediary), and yarn names ("named") and packages enigma mappings into a zip archive..

### `mapNamedJar`
Builds a deobfuscated jar with linen mappings and automapped fields (enums, etc.). Unmapped names will be filled with [intermediary](https://github.com/FabricMC/Intermediary) names.

### `decompileCFR`
Decompile the mapped source code. **Note:** This is not designed to be recompiled.

### `download`
Downloads the client and server Minecraft jars for the current Minecraft version to `.gradle/minecraft`

### `mergeJars`
Merges the client and server jars into one merged jar, located at `VERSION-merged.jar` in the mappings directory where `VERSION` is the current Minecraft version.

### `setupLinen`
[`download`](#download) and [`mergeJars`](#mergeJars)
