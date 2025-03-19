**Windows OS only** (refer to README file for others OS)

1. Install Java on your system as the resource compiler tool needs it. You need at least Java 8, which you can find for 64-bit Windows [here](https://www.java.com/en/download/).
2. Download the SGDK archive from the [Download page](https://github.com/Stephane-D/SGDK/wiki/Download) and unzip it where it suits to you, for instance `D:\sgdk` (we will refer to it later as `<SGDK_PATH>`)
3. You're done ! Now verify everything is properly setting up by trying to compile the library:
```console
<SGDK_PATH>\bin\make -f <SGDK_PATH>\makelib.gen```
(don't forget to replace `<SGDK_PATH>` with your own SGDK installation path)

You should see compilation logs then at the end you should obtain the following file
`<SGDK_PATH>\lib\libmd.a`.

If everything went right, you can continue to the [SGDK Usage](SGDK-Usage) page. :)