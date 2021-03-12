**Windows OS only** (refer to README file for others OS)

1. Install Java on your system as the resource compiler tool need it. You need Java 8 at least, you can find it for 64 bit Windows [here](http://icy.bioimageanalysis.org/upload/jre-8u281-windows-x64.exe).
2. Download the SGDK archive from the [Download page](https://github.com/Stephane-D/SGDK/wiki/Download) and unzip it where it suits to you, for instance _D:\sgdk_
3. Define **_GDK_** environment variable with your installation path **in unix path format** (_D:/sgdk_).
4. Define **_GDK_WIN_** which still point to your installation path but **in windows path format** (_D:\sgdk_).
5. Add the _bin_ directory of SGDK (_D:\sgdk\bin_) to your PATH variable. Be careful, if you have another GCC installation you can have some conflicts when internal cc1 command will be called...
6. Now verify everything is properly setting up by trying to compile the library:
<pre>%GDK_WIN%\bin\make -f %GDK_WIN%\makelib.gen</pre>

You should see compilation logs then at the end you should obtain the following file
<pre>%GDK%/lib/libmd.a</pre>

If everything went right you can continue to the [SGDK Usage](SGDK-Usage) page :)