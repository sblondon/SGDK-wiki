For those who don't want to read the whole thing, here's a youtube video explaining the process (thanks Matteus):
https://youtu.be/cDEGpLxKDK0

**Here's how to use SGDK within Code::Blocks IDE**
  * Define "GDK" environment variable to your installation path in unix path format (example D:/apps/sgdk).
  * Define "GDK\_WIN" which still point to your installation path but in windows format (exemple D:\apps\sgdk).
  * Download Code::Blocks and install it ( http://www.codeblocks.org/ )
  * Launch Code::Blocks and go to the Setting --> Compiler and debugger menu

![https://github.com/Stephane-D/SGDK/wiki/images/cb_01.jpg](https://github.com/Stephane-D/SGDK/wiki/images/cb_01.jpg)


  * Create a new compiler configuration by doing a copy of the basic GNU GCC Compiler. Name it as you want ("Sega Genesis Compiler" here).

![https://github.com/Stephane-D/SGDK/wiki/images/cb_02.jpg](https://github.com/Stephane-D/SGDK/wiki/images/cb_02.jpg)


  * "Toolchain executables" tab, enter the mini dev kit path (as you set in GDK\_WIN) in the "Compiler's installation directory". Unfortunately it does not accept variable name so you have to enter it to its own. Then set the executable filename as on the picture :

![https://github.com/Stephane-D/SGDK/wiki/images/cb_03.jpg](https://github.com/Stephane-D/SGDK/wiki/images/cb_03.jpg)


**At this point we already finished the compiler configuration :)**

**Now here's how to do your own project and compile it :**

  * Do a new project

![https://github.com/Stephane-D/SGDK/wiki/images/cb_04.jpg](https://github.com/Stephane-D/SGDK/wiki/images/cb_04.jpg)


  * Choose a empty project type and click on "Go" button

![https://github.com/Stephane-D/SGDK/wiki/images/cb_05.jpg](https://github.com/Stephane-D/SGDK/wiki/images/cb_05.jpg)


  * Click on Next...

![https://github.com/Stephane-D/SGDK/wiki/images/cb_06.jpg](https://github.com/Stephane-D/SGDK/wiki/images/cb_06.jpg)


  * Choose a name and a directory for your project, others box are automatically filled but you can modify them if you want, then click on Next.

![https://github.com/Stephane-D/SGDK/wiki/images/cb_07.jpg](https://github.com/Stephane-D/SGDK/wiki/images/cb_07.jpg)


  * Choose the genesis compiler you just set up ("Sega Genesis Compiler" here). Uncheck the "Debug" configuration which is useless here and rename the "Release" configuration to "default" as this is the only used here. Change the outputs directory to "out\" then click on finish.

![https://github.com/Stephane-D/SGDK/wiki/images/cb_08.jpg](https://github.com/Stephane-D/SGDK/wiki/images/cb_08.jpg)


  * Open the contextual menu on the project and choose "Properties..."

![https://github.com/Stephane-D/SGDK/wiki/images/cb_09.jpg](https://github.com/Stephane-D/SGDK/wiki/images/cb_09.jpg)


  * Use the provided makefile.gen file in the devkit as the project makefile. Don't forget to check the "This is a custom Makefile" checkbox. Then click to the "Project's build options" button.

![https://github.com/Stephane-D/SGDK/wiki/images/cb_10.jpg](https://github.com/Stephane-D/SGDK/wiki/images/cb_10.jpg)


  * Select the "default" configuration in left column, check if the Selected compiler is the good one (Sega Genesis Compiler here) and go to the last tab "Make". Then modify the make commands as here :

![https://github.com/Stephane-D/SGDK/wiki/images/cb_11.jpg](https://github.com/Stephane-D/SGDK/wiki/images/cb_11.jpg)


  * Validate your changes and now you can add files to your project, your files should be localized in your project directory as following :
```
sources files (C, S) : root directory or "src" directory
includes files (H, INC) : root directory or "inc" directory
resources files (S, ASM, TFC, TFD, PCM, RAW, WAV, BIN, BMP, RC, RES) : root directory or "res" directory
```

![https://github.com/Stephane-D/SGDK/wiki/images/cb_12.jpg](https://github.com/Stephane-D/SGDK/wiki/images/cb_12.jpg)


  * Compile your project in the "Build" menu, "Build" command or press Ctrl+F9 keys. If all is correctly setup you should obtain a rom.bin file in the out directory of your project directory :)