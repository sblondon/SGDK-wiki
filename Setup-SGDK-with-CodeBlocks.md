**Here's how to use SGDK within Code::Blocks IDE**
1. Download Code::Blocks and install it ( http://www.codeblocks.org/ )
2. Launch Code::Blocks and go to the Setting --> Compiler and debugger menu

![https://github.com/Stephane-D/SGDK/wiki/images/cb_01.jpg](https://github.com/Stephane-D/SGDK/wiki/images/cb_01.jpg)

3. Create a new compiler configuration by doing a copy of the basic GNU GCC Compiler. Name it as you want ("Sega Genesis Compiler" here).

![https://github.com/Stephane-D/SGDK/wiki/images/cb_02.jpg](https://github.com/Stephane-D/SGDK/wiki/images/cb_02.jpg)

4. _Toolchain executables_ tab, enter the SGDK path in the _Compiler's installation directory_. Unfortunately it does not accept variable name so you have to enter it to its own. Then set the executable filename as on the picture:

![https://github.com/Stephane-D/SGDK/wiki/images/cb_03.jpg](https://github.com/Stephane-D/SGDK/wiki/images/cb_03.jpg)

**At this point we already finished the compiler configuration :)**

**Now here's how to do your own project and compile it:**

1. Do a new project

![https://github.com/Stephane-D/SGDK/wiki/images/cb_04.jpg](https://github.com/Stephane-D/SGDK/wiki/images/cb_04.jpg)

2. Choose a empty project type and click on "Go" button

![https://github.com/Stephane-D/SGDK/wiki/images/cb_05.jpg](https://github.com/Stephane-D/SGDK/wiki/images/cb_05.jpg)

3. Click on Next...

![https://github.com/Stephane-D/SGDK/wiki/images/cb_06.jpg](https://github.com/Stephane-D/SGDK/wiki/images/cb_06.jpg)

4. Choose a name and a directory for your project, others box are automatically filled but you can modify them if you want, then click on Next.

![https://github.com/Stephane-D/SGDK/wiki/images/cb_07.jpg](https://github.com/Stephane-D/SGDK/wiki/images/cb_07.jpg)

5. Choose the genesis compiler you just set up (_Sega Genesis Compiler_ here). Uncheck the _Debug_ configuration which is useless here and rename the _Release_ configuration to _default_ as this is the only used here. Change the outputs directory to "out\" then click on finish.

![https://github.com/Stephane-D/SGDK/wiki/images/cb_08.jpg](https://github.com/Stephane-D/SGDK/wiki/images/cb_08.jpg)

6. Open the contextual menu on the project and choose _Properties..._

![https://github.com/Stephane-D/SGDK/wiki/images/cb_09.jpg](https://github.com/Stephane-D/SGDK/wiki/images/cb_09.jpg)

7. Use the provided makefile.gen file in SGDK as the project makefile. Don't forget to check the _This is a custom Makefile_ checkbox. Then click to the _Project's build options_ button.

![https://github.com/Stephane-D/SGDK/wiki/images/cb_10.jpg](https://github.com/Stephane-D/SGDK/wiki/images/cb_10.jpg)

8. Select the _default_ configuration in left column, check if the Selected compiler is the good one (Sega Genesis Compiler here) and go to the last tab _Make_. Then modify the make commands as here:

![https://github.com/Stephane-D/SGDK/wiki/images/cb_11.jpg](https://github.com/Stephane-D/SGDK/wiki/images/cb_11.jpg)

9. Validate your changes and now you can add files to your project, your files should be localized in your project directory as following:
    * Source files (C, S): root directory or _src_ directory
    * Include files (H, INC): root directory or _inc_ directory
    * Resource files (RES): root directory or _res_ directory
10. Compile your project in the _Build_ menu, _Build_ command or press _Ctrl+F9_ keys. If all is correctly setup you should obtain a *_rom.bin_* file in the _out_ directory of your project directory :)