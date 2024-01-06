### Setup Eclipse

1. Define "GDK" environment variable to your installation path in unix path format (example D:/apps/sgdk).
2. Download Eclipse CDT at http://www.eclipse.org/cdt/downloads.php and install it wherever you want.
3. Launch Eclipse and set your workspace folder (will be your root folder for your futures projects).
4. Go to the workbench and select menu _Window > Preferences_ to setup Eclipse
5. In _General > Workspace_
   * check _**Save automatically before build**_
   * uncheck _**Build automatically**_
6. In _C/C++ > New CDT Project Wizard > Makefile Project_ go to the _Builder Settings_ tab
   * uncheck _**Use default build command**_
   * set _**Build command**_ value to `${GDK}/bin/make`
   * go to the _Behavior_ tab
   * check _**Use custom build arguments**_
   * set _**Build Arguments value**_ to `-f ${GDK}/makefile.gen`
![](https://github.com/Stephane-D/SGDK/wiki/images/eclipse03.png)
7. In _C/C++ > New CDT Project Wizard > Makefile Project_ go to the _Behavior_ tab
   * check _**Build (incremental build)**_
   * replace field value `all` by `${ConfigName}` so it will use the current active configuration to build the project
   * check _**Clean**_
   * replace field value `clean` by `clean${ConfigName}` so it will use custom clean depending the current active configuration
![](https://github.com/Stephane-D/SGDK/wiki/images/eclipse02.png)

### Setup Project

1. You can now create a new project (_File > New > C Project > Makefile project > Empty Project > --Other toolchain--_).
![](https://github.com/Stephane-D/SGDK/wiki/images/eclipse04.png)
2. Right-click on the project and select _Build configurations > Manage..._
   * Rename the `Default` configuration to `Release`
   * Add a new configuration named `Debug`
   * So now you can change the active configuration depending the build you need :)
![](https://github.com/Stephane-D/SGDK/wiki/images/eclipse07.png)
3. Right-click on on the project and select _Properties_ to setup the project itself.
4. In _C/C++ General > Paths and Symbols_, add a new directory in _Includes_ tab
   * Directory: `${GDK}/inc`
   * Check `Add to all configurations`
   * Check `Add to all languages`
   * Validate by clicking OK
![](https://github.com/Stephane-D/SGDK/wiki/images/eclipse05.png)
5. Click _Apply_ and rebuild the index if it asks for it and you're ready to compile your project :)

### Common error
* If you have an error on build like *`main() not found`*, be sure to click _*Apply*_ on project properties's _C/C++ General > Paths and Symbols_.
* Be sure to uncheck the _Project > Build automatically_ option.