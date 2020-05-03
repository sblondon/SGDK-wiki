SGDK uses a generic makefile to compile project. In order to be properly recognized by the makefile you need to organize your project folder structure as following:<br>
<br>
**project root**<br>
* **src** = source files<br>
* **inc** = include files<br>
* **res** = resource files<br>
* **out** = output files (will be created automatically)<br>

where
  * source files can be .c (C source file), .s (68k assembly source file) or .s80 (Z80 assembly source file)
  * include files can be .h (C include file) or .inc (assembly include file)
  * primary resource files should be .res (resource definition file compiled by _rescomp_ tool, see [bin/rescomp.txt](https://raw.githubusercontent.com/Stephane-D/SGDK/master/bin/rescomp.txt) file)
  * others resources files can be located anywhere while you are referring them correctly in your .res file.
    * .bmp = image file (indexed colors only)
    * .png = image file (indexed colors only)
    * .vgm = VGM music dump file (Megadrive only)
    * .xgm = XGM music file
    * .wav = WAV sound file (used for SFX)
    * .bin = binary data file
    * .c = C source file
    * .s = 68k assembly source file

You can read the [bin/rescomp.txt](https://raw.githubusercontent.com/Stephane-D/SGDK/master/bin/rescomp.txt) file to have more information about supported resource files.

**Then to compile your project you need to use the following command directly from your project folder:**
<pre>%GDK_WIN%\bin\make -f %GDK_WIN%\makefile.gen</pre>

Normally if everything went right you should obtain a **_rom.bin_** file in the _out_ folder.
You can directly load this _rom.bin_ file into an emulator (or put on your flash cart if you have one) to test it.

You can now continue to the [tutorials section](Tuto-Introduction) to start the serious things :)