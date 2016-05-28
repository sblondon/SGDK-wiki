## SGDK : A small, open and free development kit for the Sega Megadrive ##

SGDK 1.2  released !

It features a new Sprite Engine which is still not yet completed (i plan to optimize performance which are already better than the old Sprite Engine but not fast enough yet and also plan to add sorting feature...).
You might find some bugs in it as the code becomes complex and i could not test it intensively, please report them in the GitHub issues tracker :)<
If you experience `undefined reference to _hard_reset` error then just delete your local project copy of `boot/sega.s` file so it will automatically replaced by the new SGDK one.

SGDK is split in several parts:
  * The library itself provided with full code sources, some samples and a Doxygen documentation (in the _doc_ folder).
  * GCC compiler binaries (for Windows system only as you can easily install them on Unix based system).
  * Library tools (resources compiler mainly). Binaries are provided only for Windows system only but sources are included so you can compile them easily.

Download the complete archive in [Download Section](https://github.com/Stephane-D/SGDK/wiki/Download).<br>
Unix/Linux users should give a try to the <a href='https://github.com/kubilus1/gendev/'>Gendev project</a> from Kubilis which allow to quickly setup SGDK on a Unix environment.<br>
And now MACOS users also have access to SGDK with <a href='https://github.com/SONIC3D/gendev-macos'>Gendev MacOS</a>, thanks to Sonic3D for making it :)<br>

After you downloaded the SGDK archive, check the <a href='https://github.com/Stephane-D/SGDK/wiki/Setup-SGDK-basic'>Wiki Section</a> to get installation instructions and basics tutorials.<br>
<br>
You are more than welcome to share your experience and get further assistance on <a href='http://gendev.spritesmind.net/forum'>SpritesMind forum</a> or <a href='http://sega4ever.power-heberg.com/tutoriaux/ProgMD/Outils.html'>Sega4Ever (french only)</a> !<br>
<br>
Wish you a happy coding :)