# Simply Optimized
A very light base Fabric modpack to heavily optimize the game without any QoL improvements.

[![Modrinth](https://img.shields.io/modrinth/dt/sop?color=1bd96a&label=Modrinth&style=for-the-badge)](https://modrinth.com/modpack/sop/versions) [![Discord](https://img.shields.io/discord/977987490742935652?color=5865F2&label=Discord&style=for-the-badge)](https://discord.gg/WSQdQZUjeR) ![grad](https://i.imgur.com/f1jZ0cr.png)
---


The Simply Optimized modpack intends to be the very base of mods/configurations for performance. You can add any mods on top of it at your own taste. It only contains essential and lesser known rendering optimization mods and a few mods to speed up other things like usually slow loading times. For each new release, I try to bring the performance up and the mod count down, picking out the best solutions possible.

*for some reason, every second optimization modpack implies this, but when i look at the mods i see a lot of QoL that is not related to optimization at all-*

One of its purposes may be to be recommended to people new to Fabric who just want a selection of mods for the top performance without much else - instead of listing the mods manually, you can just link them here!

I can confidently claim this is the best optimization modpack in terms of performance as of now.

*Works on Quilt without issue! just replace Fabric API with QSL and you're good to go!*

---



#### I've seen a modpack called Fabulously Optimized, is it related in any way?

FO adds many more mods and is more invasive to the game (with it you have smooth transitions, scrolling, zoom, and a few more QoL features). It has everything you may have gotten used to, and is good for Optifine players who are looking for Fabric alternatives: FO has them all in one place. You probaly won't need any new mods with it.

SO, although inspired by FO, purely focuses on performance, has a lot less mods in it (it's the barest bones of a client) which results in lower loading times and easier maintainability. With it you are expected to add all the content, visual and QoL mods you need yourself (this modpack's here to speed up the process of client optimization).


---


<details><summary>Included mods (17)</summary>
<p>

\* = minor

- [Very Many Players](https://modrinth.com/mod/vmp-fabric)* by [ishland](https://modrinth.com/user/ishland) (mostly for servers - but even on clients, brings a good small perfomance boost in entity-heavy scenarios.)

- [FastLoad](https://modrinth.com/mod/fastload)* by [FluffyBumblebees](https://modrinth.com/user/FluffyBumblebees) (makes the world creation/loading fast, decreasing the radius of firstly loaded chunks and applying some pre-rendering optimizations)

- [More Culling](https://modrinth.com/mod/moreculling)* by [fxmorin](https://modrinth.com/user/fxmorin) (culls more block faces for a small but welcome perfomance boost)

- [Memory Leak Fix](https://modrinth.com/mod/memoryleakfix) by [fxmorin](https://modrinth.com/user/fxmorin) (helps with memory usage and hugely with load times)

- [Iris](https://modrinth.com/mod/iris) by [coderbot](https://modrinth.com/user/coderbot) (*added here for the entity batching optimization that is very important, **to be replaced if a separate mod comes out***)

<details><summary>The Iris sutiation</summary>
<p>

Iris is known to bring a huge gain in areas such as minigame lobbies with the entity batching system, but its various other changes required to make shaders work bring a small, but noticable perfomance pelnaty basically everywhere else - all with shaders disabled. It would be ideal to have a separate mod for entity batching, as Iris here is a double-edged sword. However, in the situations when it is at a loss your FPS is probaly higher than the monitor's refresh rate anyway, so it stays in the pack. Anyone who would maintain [Entity Batching as a separate mod](https://github.com/coderbot16/batched-entity-rendering) is welcome to do so and I'll replace Iris with such mod ASAP if I can.

Iris will be yeeted when Sodium 0.5 is out (it's supposed to have this without iris i think)
</p>

</details>

- [C2ME](https://modrinth.com/mod/c2me-fabric) by [ishland](https://modrinth.com/user/ishland) (chunk loading optimizations (server-side))

- [Enhanced Block Entities](https://modrinth.com/mod/ebe) by [FoundationGames](https://modrinth.com/user/FoundationGames) (reimplements block (tile) entities for performance)

- [Entity Culling](https://modrinth.com/mod/entityculling) by [tr7zw](https://modrinth.com/user/tr7zw) (culls (=not renders) 90% unneeded entities in most cases)

- [Fabric API](https://modrinth.com/mod/fabric-api) (needed for most mods to function)

- [FerriteCore](https://modrinth.com/mod/ferrite-core) by [malte0811](https://modrinth.com/user/malte0811) (memory management optimizations)

- [Krypton](https://modrinth.com/mod/krypton) by [astei](https://modrinth.com/user/astei) (networking optimizations)

- [LazyDFU](https://modrinth.com/mod/lazydfu) by [astei](https://modrinth.com/user/astei) (makes Data Fixer Upper only cache when needed, greatly reducing load times and some lag spikes)

- [Lithium](https://modrinth.com/mod/lithium) by the [caffeinemc team](https://github.com/CaffeineMC/lithium-fabric) (much known - server-side optimizations)

- [Smooth Boot](https://modrinth.com/mod/smoothboot-fabric) by [UltimateBoomer](https://modrinth.com/user/UltimateBoomer) ("improves minecraft CPU sheduling", the result of which is game startup not crazily lagging the whole system)

- [Sodium](https://modrinth.com/mod/sodium) by the [caffeinemc team](https://github.com/CaffeineMC/sodium-fabric) (much known - rendering engine optimizations)

- [Starlight](https://modrinth.com/mod/starlight) by [spottedleaf](https://modrinth.com/user/spottedleaf) (much known - lighting engine rewrite)

- [Debugify](https://modrinth.com/mod/debugify) by [isxander](https://modrinth.com/user/isxander) (adds a lot of patches that would have otherwise takes a lot of small mods, partially enabled for optimization-related patches) 

</p>
</details>

## Post-install

After you install the modpack, you may take a few extra things to squeeze the top performance out of it. This section covers advanced topics most of the time so it may not be absolutely correct. If you find the information inaccurate, tell this to me in Discord!

<details><summary>Click to expand!</summary>
<p>

<details><summary>Optimize the JVM flags!</summary>
<p>

*Please note that this is for advanced players only. If you don't really understand this section, you probaly don't need to. Changing these arguments may not only result in a performance increase, but also in a decrease, and little testing has been done regarding what you see below*

For high-end PCs *(powerful CPU + fast RAM)*:

```-XX:+UnlockExperimentalVMOptions -XX:+UseShenandoahGC -XX:ShenandoahGCMode=iu -XX:+UseLargePages -XX:+UseNUMA -XX:+AlwaysPreTouch -XX:-UseBiasedLocking -XX:+DisableExplicitGC```

For low-end PCs *(little performance impact, +2-5 FPS, you probaly can go with the defaults)*:

 ```-XX:+UnlockExperimentalVMOptions -XX:+UseLargePages -XX:+DisableExplicitGC -XX:G1MixedGCCountTarget=1```

Don't forget to set your `-XmsXG` and `-XmxYG` flags to the amount of RAM you desire to give to Minecraft! Setting them both to the same value is said to improve performance as well.

</p>
</details>

------

<details><summary>Use optimized JVM distributions</summary>
<p>

In addition to optimized JVM flags, you may also use an optimized JVM. [GraalVM](https://www.graalvm.org/downloads/) is a good one, with even the cut-down CE edition giving a 2.8% FPS boost with entity rendering and (!) 39% boost in GUI rendering in my rough benchmarks (over Adoptium JRE).


</p>
</details>

------


<details><summary>Use adaptive V-Sync (or none at all)</summary>
<p>

The usual V-Sync, whlist useful for reducing useless load and increasing the output quality, always tries to sync rendering to your screen's refreshing, no matter if it hurts the performance. If you have a 60hz monitor with vsync, if the game in a given situation can output 55 FPS it will only show 30, as it's the only way it can sync correctly.

The solution to the issue in this given situation is either

 - capping the FPS at 60 without V-Sync (which would cause screen tearing) or

- using adaptive V-Sync which has the best of both worlds, only trying to sync if the possible framerate is equal to or above the refresh rate, therefore not hindering your performance.

A good way to get it ATM is the [Sodium Extra](https://modrinth.com/mod/sodium-extra) mod.

You also (probaly) can enable Adaptive V-Sync in the GPU's control panel, for either Nvidia or AMD GPUs (AMD has FreeSync or Enhanced Sync)

Note that the display latency may still be higher than without V-Sync at all.

</p>
</details>

</p>
</details>


## Versioning

The version format is x.y.z,

where the x of a version is the revision (a mod list change), the y is the patch (an update to a mod or a change to a config), the z is the hotpatch (there might be a few hotpatches in the span of an hour since the release of a patch in case i keep forgetting something and i need to fix it last minute)

Whenever SO comes out for a new major Minecraft release, this is to be reset to 1.0, this approach will make things less linear and more like they are in reality - each MC version will probaly have an unique set of essential performance mods. Due to this, the MC version will always be specified in the name and the version number.

