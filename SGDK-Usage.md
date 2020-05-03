To be properly recognized by SGDK makefile, you need to respect the following constraints in your project folder:
  * source files: should be located in _/_ (root) or _/src_ directory.
    * .c = C source file
    * .s = 68k GAS assembly source file
    * .asm = 68k assembly source file (other format)
    * .s80 = Z80 assembly source file
  * include files: should be located in _/_  or _/inc_ directory
    * .h = C include file
    * .inc = assembly include file
  * primary resource files: should be located in _/_  or _/res_ directory
    * .c = C source file
    * .s = 68k GAS assembly source file
    * .res = resource definition file (compiled by Rescomp tool, see [bin/rescomp.txt](https://raw.githubusercontent.com/Stephane-D/SGDK/master/bin/rescomp.txt) file)
  * others resources files: can be located anywhere while you are referring them correctly in your .res file
    * .bmp = image file (indexed colors only)
    * .png = image file (indexed colors only)
    * .vgm = VGM music dump file (Megadrive only)
    * .xgm = XGM music file
    * .wav = WAV sound file (used for SFX)
    * .bin = binary data file
    * read the [bin/rescomp.txt](https://raw.githubusercontent.com/Stephane-D/SGDK/master/bin/rescomp.txt) file to have more information about supported resource files.

Then to compile your project you need to use the following command directly from your project folder:
<pre>%GDK_WIN%\bin\make -f %GDK_WIN%\makefile.gen</pre>

Normally you should obtain a **_rom.bin_** file in the _out_ directory that you can load in an emulator (or directly on the hardware if you are a lucky owner of a flash cart).

You can now continue to the [tutorials section](https://github.com/Stephane-D/SGDK/wiki/Tutorials-Introduction) to start the serious things :)