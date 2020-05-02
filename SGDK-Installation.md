Note that this concerns only Windows OS (refer to README file for others OS)

1. Download the SGDK archive from the [Download page](https://github.com/Stephane-D/SGDK/wiki/Download) and unzip it where it suits to you (for instance D:/sgdk).
2. Define _GDK_ environment variable with your installation path **in unix path format** (example D:/sgdk).
3. Define _GDK_WIN_ which still point to your installation path but **in windows path format** (example D:\sgdk).
4. Add the _bin_ directory of SGDK (%GDK_WIN%\bin) to your PATH variable. Be careful, if you have another GCC installation you can have some conflicts when internal cc1 command will be called...
5. Now verify everything is properly setting up by trying to compile the library typing this command:
<pre>%GDK_WIN%\bin\make -f %GDK_WIN%\makelib.gen</pre>
You should see compilation logs then at the end you should obtain the following file
<pre>%GDK%/lib/libmd.a</pre>

Before compiling your own project you first need to respect the following constraint in your project source tree:
  * sources files (C, S, ASM, S80): root directory or _src_ directory
  * includes files (H, INC): root directory or _inc_ directory
  * primary resource files (C, S, RC, RES): root directory or _res_ directory
  * others resources files (TFC, TFD, PCM, RAW, WAV, BIN, BMP, PNG): can be wherever you want while you are referring them correctly in your resource definition files

Then to compile your project you need to use the following command directly from your project directory :
<pre>%GDK_WIN%\bin\make -f %GDK_WIN%\makefile.gen</pre>

Normally you should obtain a rom.bin file in the out directory that you can load in an emulator (or directly on the hardware if you are a lucky owner of a flash cart).