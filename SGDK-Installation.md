**Windows OS only** (refer to README file for others OS)

1. Download the SGDK archive from the [Download page](https://github.com/Stephane-D/SGDK/wiki/Download) and unzip it where it suits to you (for instance D:/sgdk).
2. Define _GDK_ environment variable with your installation path **in unix path format** (example D:/sgdk).
3. Define _GDK_WIN_ which still point to your installation path but **in windows path format** (example D:\sgdk).
4. Add the _bin_ directory of SGDK (%GDK_WIN%\bin) to your PATH variable. Be careful, if you have another GCC installation you can have some conflicts when internal cc1 command will be called...
5. Now verify everything is properly setting up by trying to compile the library typing this command:
<pre>%GDK_WIN%\bin\make -f %GDK_WIN%\makelib.gen</pre>

You should see compilation logs then at the end you should obtain the following file
<pre>%GDK%/lib/libmd.a</pre>

If everything went right you can continue to the [SGDK Usage](https://github.com/Stephane-D/SGDK/wiki/SGDK-Usage) page :)