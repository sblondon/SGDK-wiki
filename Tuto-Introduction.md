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
Another important point to know is that **SGDK heavily relies on _resources_** which are compiled through _rescomp_ tool. You can read the [rescomp.txt](https://raw.githubusercontent.com/Stephane-D/SGDK/master/bin/rescomp.txt) file to know which kind of resource you can use and how to declare them then check the **'sample' folder** from SGDK and in particular the **[sprite sample](https://github.com/Stephane-D/SGDK/tree/master/sample/sprite)** which is a good showcase of SGDK usage in general (functions and resources).

If you feel ready then you can continue on the [Hello World tutorial](Tuto-Hello-World) !