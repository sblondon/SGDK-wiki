**Windows OS only** (refer to README file for others OS)

1. Install Java on your system as the resource compiler tool needs it. You need at least Java 8, which you can find for 64-bit Windows [here](http://icy.bioimageanalysis.org/upload/jre-8u281-windows-x64.exe).
2. Download the SGDK archive from the [Download page](https://github.com/Stephane-D/SGDK/wiki/Download) and unzip it where it suits to you, for instance `D:\sgdk`. (We will refer to it later as `SGDK_PATH`.)
3. You're done ! Now verify everything is properly setting up by trying to compile the library:
<pre>{SGDK_PATH}\bin\make -f {SGDK_PATH}\makelib.gen</pre>, replacing `{SGDK_PATH}` with your unzip location.

You should see compilation logs then at the end you should obtain the following file
<pre>{SGDK_PATH}\lib\libmd.a</pre>.

If everything went right, you can continue to the [SGDK Usage](SGDK-Usage) page. :)