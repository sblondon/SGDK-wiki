SGDK uses a generic makefile to compile the project. In order to be properly recognized by the makefile you need to organize your project folder structure as following:

**project root**
* **src** = source files (sub-folder supported up to 2 depth levels, ex: _src/engine/enemy/*_)
* **inc** = include files
* **res** = resource files
* **out** = output files (will be created automatically)

**where**
  * source files can be _.c_ (C source file), _.s_ (68k assembly source file) or _.s80_ (Z80 assembly source file)
  * include files can be _.h_ (C include file) or _.inc_ (assembly include file)
  * primary resource files should be _.res_ (resource definition file compiled by _rescomp_ tool, see [bin/rescomp.txt](https://raw.githubusercontent.com/Stephane-D/SGDK/master/bin/rescomp.txt) file)
  * other resources files can be located anywhere while you are referring them correctly in your _.res_ file.
    * _.bmp_ = image file (indexed colors only)
    * _.png_ = image file (indexed colors only)
    * _.vgm_ = VGM music dump file (Megadrive only)
    * _.xgm_ = XGM music file
    * _.wav_ = WAV sound file (used for SFX)
    * _.bin_ = binary data file
    * _.c_ = C source file
    * _.s_ = 68k assembly source file

***

**The makefile supports 3 different profiles:**
* _release_ --> release / optimized build (default)
* _debug_ --> debug build containing symbols and displaying errors in Gens KMod log (see [Tuto Introduction](https://github.com/Stephane-D/SGDK/wiki/Tuto-Introduction) page)
* _asm_ --> used to generate assembly listing

**So to compile your project you need to use the following command directly from your project folder:**

```console
SGDK_PATH\bin\make -f SGDK_PATH\makefile.gen
```

Don't forget that `SGDK_PATH` refer to the full path where you installed SGDK (don't forget to also specify the drive letter - ex `D:\SGDK`).

Note that if you omit the profile it will use the _release_ one by default, if you want to use the debug build you will need to use:

```console
SGDK_PATH\bin\make -f SGDK_PATH\makefile.gen debug
```

Normally if everything went right you should obtain a **_rom.bin_** file in the _out_ folder.
You can directly load this _rom.bin_ file into an emulator (or put on your flash cart if you have one) to test it.

You can now continue to the [tutorials section](Tuto-Introduction) to start the serious things. :)