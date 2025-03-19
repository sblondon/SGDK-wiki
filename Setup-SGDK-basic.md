### Installation and use of SGDK from command line (Windows OS only)

* Download the SGDK archive from the [Download page](https://github.com/Stephane-D/SGDK/wiki/Download) and unzip it where it suits to you (for instance D:/sgdk).
* Define _GDK_ environment variable to your installation path in unix path format (example D:/sgdk).
* Define *GDK_WIN* which still point to your installation path but in windows format (example D:\sgdk).
* Add the bin directory of devkit `%GDK_WIN%\bin` to your PATH variable. Be careful, if you have another GCC installation you can have some conflicts when cc1 command will be called...

Now you can compile the library by using:<br>
`%GDK_WIN%\bin\make -f %GDK_WIN%\makelib.gen`

When the library is compiled you should obtain the following file:<br>
`%GDK%/lib/libmd.a`

Before compiling your own project you first need to respect the following constraint in your project source tree:
* **Sources files (.c, .s, .asm, .s80):** root directory or src directory
* **Includes files (.h, .inc):** root directory or inc directory
* **Primary resource files (.res):** root directory or res directory
* **Others resources files (.png, .bmp, .vgm, .wav...):** can be wherever you want while you are referring them correctly in your resource definition files

Then to compile your project you need to use the following command directly from your project directory:<br>
`%GDK_WIN%\bin\make -f %GDK_WIN%\makefile.gen`

Normally you should obtain a _out/rom.bin_ file that you can load in an emulator (or directly on your flash cart if you have one).