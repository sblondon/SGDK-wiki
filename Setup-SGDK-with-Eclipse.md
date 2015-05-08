### Setup Eclipse

1. Define "GDK" environment variable to your installation path in unix path format (example D:/apps/sgdk).
2. Download Eclipse CDT at http://www.eclipse.org/cdt/downloads.php and install it wherever you want.
3. Launch Eclipse and set your workspace folder as your root folder of your futures development projects as each new project will be added to this folder by Eclipse.
4. Go to the workbench and select menu _Window > Preferences_ to setup Eclipse
5. In _General > Workspace_, select _**Save automatically before build**_ and unselect _**Build automatically**_
6. In _C/C++ > Build > Build Variables_, add a new variable :
 * Variable name : _GDK_
 * Type : _Directory_
 * Value : _../../sdk_

{{{
 this will define $GDK needed by sdk/makefile.gen
}}}

![](https://github.com/Stephane-D/SGDK/wiki/images/eclipse01.png)

7. In _C/C++ > Build > Environnement_, add a new variable
 * Name : _GDK_
 * Value : _../../sdk_
 
{{{
 this will define a var used on Eclipse IDE
}}}

![](https://github.com/Stephane-D/SGDK/wiki/images/eclipse02.png)


8. In _C/C++ > New CDT Project Wizard > Makefile Project_
 * unselect _**Use default build command**_ in _Builder Settings_ tab
 * set, as _Build command_,  `${GDK}/bin/make -f ${GDK}/makefile.gen`

{{{
 this will define  sgdk/makefile.gen as the default makefile of any project
}}}

![](https://github.com/Stephane-D/SGDK/wiki/images/eclipse03.png)

### Setup Project

You could now create a new project (_File > New > C Project > Makefile project > Empty Project > --Other toolchain--_).

![](https://github.com/Stephane-D/SGDK/wiki/images/eclipse04.png)

Right-click on it and select _Properties_ to setup the project itself.

In _C/C++ General > Paths and Symbols_, add a new directory in _Includes_ tab
 * Directory : `${GDK}/include`
 * Add to all configurations
 * Add to all languages
 
![](https://github.com/Stephane-D/SGDK/wiki/images/eclipse05.png)

Click _Apply_ and rebuild the index

![](https://github.com/Stephane-D/SGDK/wiki/images/eclipse06.png)
{{{
this will make available the headers on <parent folder>/sdk/include to your project
}}}


On _Make Target_ view, create a new target for your project.
 * give it a name
 * unselect _*Same as the target name*_
 * empty _Make target_ field
http://sgdk.googlecode.com/svn/wiki/pictures/eclipse07.png
{{{
 double click on this target to generate a out/rom.bin according your project's file, sdk/makefile.gen and sgdk library
}}}

== Common error ==
If you have an error on build like *`main() not found`*, be sure to click _*Apply*_ on project properties's _C/C++ General > Paths and Symbols_.

Another source of problem : be sure to un-mark _Project>Build automatically_