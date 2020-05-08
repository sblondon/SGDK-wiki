## Hello World ##

Whenever you use [Code::Block](Setup-SGDK-with-CodeBlocks), [Eclipse](Setup-SGDK-with-Eclipse), [QtCreator](Setup-SGDK-with-QtCreator) or [any other source code editor](SGDK-Usage), you need your `main` function.

```
int main(u16 hard)
{
    return 0;
}
```

As any C program this function is your starting point and is automatically called on start up.<br>
Note that with SGDK (and this is specific to SGDK), your `main` function receive a single parameter named `hard` which allow to know if you are on a hard reset (hard = 1 mean that we just turned the system ON) or on a soft reset (hard = 0 mean that reset button was pressed).

Before calling ```main``` method, SGDK initializes several things for you:
  * clear RAM and initialize variables
  * setup the VDP with a default configuration (64x32 plane size, enable Vint, setup table addresses... see [VDP registers doc](http://info.sonicretro.org/SCHG:VDP_Documentation/General/Registers))
  * clear video RAM
  * load 4 default palettes: grey, red, green and blue
  * load a default font for your text print need
  * init input handling
  * reset sound system

So, for basic stuff and testing, everything is ready to use :)

Now if you want to use VDP, input, sprite or whatever function from SGDK, you first need to include the `genesis.h` header. It will let you access to the whole SGDK functions !

Let's see that by replicating the infamous _**Hello World**_ example :)

Printing on screen is a VDP task so you need to call `VDP_drawText(<your_text>, <x>, <y>)`.<br>
> Don't forget to use the doxygen documentation (in SGDK _doc_ folder) when you are looking for help on a specific function. SGDK organizes its functions per unit, for instance SYS_xx methods are declared in sys.h unit, JOY_xx in joy.h unit, helping you to find them more easily... 
Ok so if you correctly read the `VDP_drawText(<your_text>, <x>, <y>)` documentation you know that _x_ and _y_ parameters are in tile unit with 1 tile = 8 pixels.

```
#include <genesis.h>

int main(u16 hard)
{
    VDP_drawText("Hello World!", 10, 13);

    return 0;
}
```

This code is correct but not really Genesis friendly: do you think we can return (and stop) a program ?
Video games repeatedly update the TV screen, and it's up to you to handle things before or while a refresh.

So a more Genny Hello World is more like this:
```
#include <genesis.h>

int main(u16 hard)
{
    VDP_drawText("Hello Genny World!", 10, 13);

    while(TRUE)
    {
        // read input
        // move sprite
        // update score
        // draw current screen (logo, start screen, settings, game, gameover, credits...)
    }

    return 0;
}
```

This code is correct, even if `return 0;` will never be reached.
The code inside the while loop will execute in full speed...great! but do you think the Genesis will handle so much ?
The TV screen is updated 50 (PAL) or 60 (NTSC) times per second...you have to be sync with this.
A useful way is to wait for screen update, or vertical synchronization.

SGDK is here to help you with the `VDP_waitVSync` function !

So, this time, you could write your first Genesis fully compliant demo:
```
#include <genesis.h>

int main(u16 hard)
{
    VDP_drawText("Hello Genny World!", 10, 13);

    while(TRUE)
    {
        // read input
        // move sprite
        // update score
        // draw current screen (logo, start screen, settings, game, gameover, credits...)

        // wait for screen refresh
        VDP_waitVSync();
    }

    return 0;
}
```

Congratulations ! You're now ready to make a little more :)

Download: [Sample Hello World project](files/tut1_HelloWorld.zip)