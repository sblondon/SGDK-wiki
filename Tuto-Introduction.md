### Disclaimer ###
First, you need to know that SGDK uses C language (assembly is also possible but not necessary) so it's highly recommended to be familiar with C programming before trying to develop with SGDK ! Trying to learn C language at same time than learning _Sega Mega Drive_ programming is definitely too difficult and you will end nowhere.<br>
It's also important to have, at least, a basic knowledge about the _Sega Mega Drive_ hardware (specifically the video system). If that's not the case then i recommend you to read these documents:
* [Sega Mega Drive graphics guide](https://megacatstudios.com/blogs/press/sega-genesis-mega-drive-vdp-graphics-guide-v1-2a-03-14-17) page from Mega Cat Studios.
* [Sik's Blog](https://plutiedev.com): more dedicated to assembly programming but explain a lot (and quite nicely) about the Sega Mega Drive hardware.
* [Mega Drive Architecture](https://www.copetti.org/projects/consoles/mega-drive-genesis): a nice article explaining the Mega Drive architecture.
* [Genesis Software Manual](https://segaretro.org/images/a/a2/Genesis_Software_Manual.pdf) which contains absolutely everything you need to know about the Sega Mega Drive.

### Purpose ###
These basic tutorials aim to give you the basis to start developing on the Sega Genesis / Mega Drive using SGDK, they will help you understanding how SGDK work and how to use it efficiently but **they do not aim to learn you C language programming nor to explain you how the Sega Mega Drive works internally** so take attention to the disclaimer.<br>
<br>
Before starting you should now that **you have a doxygen in the _'doc'_ folder of SGDK giving you a description for all SGDK functions and structures**, so always dig in the doxygen (or in the SGDK _.h_ files as the doxygen is created from them) when you want to know what a specific function does as these tutorials will only show you how to use some of them.<br>
<br>
Another important point to know is that **SGDK heavily relies on _resources_** which are compiled through _rescomp_ tool. You can read the [rescomp.txt](https://raw.githubusercontent.com/Stephane-D/SGDK/master/bin/rescomp.txt) file to know which kind of resource you can use and how to declare them then you can check the **_'sample'_ folder from SGDK and in particular the [sonic sample](https://github.com/Stephane-D/SGDK/tree/master/sample/sonic)** which is a good showcase of SGDK usage in general (functions and resources).

### Debugging ###
Debugging is always an issue when you're developing on those old systems. Unfortunately emulators supposed to support GDB - _the GNU debugger_ - doesn't seem to have complete support of it, at least i was never able to use it correctly with working breakpoints and execution stepping. If someone was able to sort it out and got it working correctly then i would be really interested in knowing the process :)

Hopefully you still have [Gens KMod](https://segaretro.org/Gens_KMod), this emulator supports some advanced debugging features and one of it is really useful: the message log capability.<br> **Before being able to use it, you need to enable the option **in the _Options --> Debug..._ dialog:
![Gens KMod - active debug features](https://github.com/Stephane-D/SGDK/wiki/images/gensKMod_02.jpg)

Then you can use the _KLog_xx(..)_ methods from SGDK to log messages / values to the _Debug Message_ dialog (_CPU --> Debug --> Messages_ menu):
![Gens KMod - log example](https://github.com/Stephane-D/SGDK/wiki/images/gensKMod_01.jpg)

This will really help you in examining if a specific action happened or see variable values for instance. It becomes even better when you're building in _debug_ profile (see [SGDK Usage](https://github.com/Stephane-D/SGDK/wiki/SGDK-Usage) page) as SGDK will also log some information in the _Debug Message_ dialog which may be really useful to you. You can change the SGDK log level by changing definition of _LIB_LOG_LEVEL_ in the [config.h](https://github.com/Stephane-D/SGDK/blob/master/inc/config.h) file then recompiling the library itself in _debug_ profile.

It's not as convenient than real GDB debugging but still better than nothing :)

The problem of Gens Kmod is that it has some flaws, first it has some bugs / memory leaks and secondly it's quite inaccurate in general so be sure to always test on more accurate emulators when possible (as [BlastEm](https://www.retrodev.com/blastem/)) or directly on the real hardware. Another good emulator for its debugging features is [Regen Debug version](https://retrocdn.net/images/2/24/Regen0972D.7z), while not being as accurate than BlastEm, it's still much better then Gens KMod in that aspect and it offers some exclusive debugging features.

I hope these informations will help you in your debugging process.

If you feel ready then you can continue on the [Hello World tutorial](Tuto-Hello-World) !