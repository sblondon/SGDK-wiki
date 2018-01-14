## Download ##

Get the last version: [SGDK 1.34](https://github.com/Stephane-D/SGDK/releases/download/1.34/sgdk134.7z)

**Old versions**
  * [SGDK 1.33](https://github.com/Stephane-D/SGDK/releases/download/v1.33/sgdk133.7z)
  * [SGDK 1.32](https://github.com/Stephane-D/SGDK/releases/download/v1.32/sgdk132.7z)
  * [SGDK 1.31](https://www.dropbox.com/s/1fejuksb5w37eoe/sgdk131.7z?dl=0)
  * [SGDK 1.30](https://www.dropbox.com/s/b3rso72uousjk7l/sgdk130.7z?dl=0)
  * [SGDK 1.22a](https://www.dropbox.com/s/17q2xidtw33q517/sgdk122a.7z?dl=0)
  * [SGDK 1.22](https://www.dropbox.com/s/8ocwkgttf6vbku7/sgdk121.7z?dl=0)
  * [SGDK 1.21](https://www.dropbox.com/s/8ocwkgttf6vbku7/sgdk121.7z?dl=0)
  * [SGDK 1.2](https://www.dropbox.com/s/ee3159mtbyo8mlt/sgdk12.7z?dl=0)
  * [SGDK 1.12](https://www.dropbox.com/s/2cnlpcoiowq6178/sgdk112.7z?dl=0)
  * [SGDK 1.11](https://www.dropbox.com/s/fk51tsowolmjwaf/sgdk111.7z?dl=0)
  * [SGDK 1.10](https://www.dropbox.com/s/ng7ga5reyay51p6/sgdk110.7z?dl=0)
  * [SGDK 1.01](https://www.dropbox.com/s/059zcf44176r9z9/sgdk101.7z?dl=0)
  * [SGDK 1.00](https://www.dropbox.com/s/o056nj6zgxa6k4j/sgdk100.7z?dl=0)
  * [SGDK 0.96d](https://www.dropbox.com/s/a4oqp7i7hizivsd/sgdk096d.7z?dl=0)


---

## Changelog 1.34 (January 2018) ##

**LIBRARY**
  * DMA
   - added DMA queue support for all (or almost all) methods supporting DMA operation
  * SPRITE
   - fixed timing issue when changing FRAME or ANIMATION manually.
   - fixed sprite sorting when multiple depth were modified in a single SPR_update(..).
   - safer sprite allocation / release.
  * MEMORY
    - added MEM_getLargestFreeBlock() to get the largest available block of memory.
  * improved LZ4W compression (better compression rate, faster compression...)
  * minors changes on method updating tilemap through X,Y position (safer)
  * some cleanup

**SAMPLE**
  * reworked benchmark sample to avoid out of memory error (^^)


## Changelog 1.33 (November 2017) ##

**LIBRARY**
  * DMA
    - added HALT_Z80_ON_DMA flag in config.h to enable Z80 halt on DMA (avoid corruptions or sound issues on Tectoy MD).
    - deprecated 'vdp_dma' unit now forward calls to 'dma' unit.
    - added wait DMA checking (DMA fill or DMA copy operation) before doing a DMA operation.
  * SPRITE
    - simplified sprite sorting (always enabled, just need to use SPR_setDepth(..) method if needed)
    - fixed a regression which was causing 1 frame latency in sprite update.

**SAMPLE**
  * minor change to sound sample


## Changelog 1.32 (October 2017) ##

**COMPILER**
  * added VS project for easier compilation with Visual Studio (thanks to lab313)

**LIBRARY**
  * TIMER
    - fixed getSubTick() method (no more possible rollback)
    - minor fix in getFPS() and getFPS_f() methods
  * VDP
    - tweaked default VRAM memory layout
  * BITMAP
    - changed get/setPixelXXX(..) methods so they now work on single pixel (not anymore doubled X pixel resolution)
    - changed drawLine(..) method so it now work on single pixel (not anymore doubled X pixel resolution).
      WARNING: drawLine(..) is not anymore doing clipping, use BMP_clipLine(..) first for that.
    - added get/setPixelXXXFast(..) methods for fast get/set pixel operation (no clipping check)
  * SOUND
    - fixed auto PCM selection when playing sample with driver 2ADPCM and 4PCM.
    - fixed default tempo for PAL system with XGM driver
  * SPRITE
      WARNING: you now require to set the sprite depth to use depth sorting (not anymore using the sprite Y position).
    - replaced SPR_FLAG_AUTO_YSORTING by SPR_FLAG_AUTO_DEPTH_SORTING
    - replaced SPR_setYSorting(..) method by SPR_setDepthSorting(..) / SPR_setZSorting(..)
    - replaced SPR_sortOnYPos() by SPR_sortOnDepth()
    - added void SPR_setDepth(..) / SPR_setZ(..) methods to set sprite depth
    - fixed VDP_updateSprites() with DMA queue operation (prevent sprite table modifications before DMA occurs).
  * STRING
    - added int16ToStr(..) and uint16ToStr(..) methods (faster than intToStr(..) or uintToStr(..) for 16 bit integer, thanks to clbr)
    - optimized intToStr(..) and uintToStr(..) methods (thanks to clbr for that)

**SAMPLE**
  * added XGM Player sample :)
  * Bench
    - added some pixels / line draw tests
  * Donuts
    - updated for new depth sorting refactoring


## Changelog 1.31 (July 2017) ##

**DOCUMENTATION**
  * minor fix and updated to last version

**COMPILER**
  * fixed debug build in 'build_lib' batch

**LIBRARY**
  * JOY:
    - fixed joy state variables declaration to avoid issues when GCC -O3 optimization level is used.
  * SPRITE:
    - added ALWAYS_ON_TOP flag to keep a sprite above others sprites whatever is sorting order.
    - minor fix on sprite sort


## Changelog 1.30 (June 2017) ##

**DOCUMENTATION**
  * Updated to last version

**COMPILER**
  * Updated to GCC 6.3 (thanks a tons to Gligli for that !)
    * many bugs fix and new features compared to old GCC 3.4.6
    * much better assembly code generation :)
    * added LTO (Linker Time Optimization) support
  * Modified makefile to enable LTO and improve optimization level.
  * Rescomp:
    * updated to handle structure changes in the Sprite Engine.

**LIBRARY**
  * DMA:
    * minor optimization to DMA_queue(..) method (thanks to HpMan)
  * Memory:
    * default stack size increased to 0x800 bytes (GCC 6.3 requires more stack memory :p)
  * Sprite Engine:
    * added automatic Y sorting (per sprite)
    * added SPR_sort(..) for generic sorting
    * added SPR_sortOnY(..) for generic sorting
    * by default now sprite visibility is set to always ON (faster than automatic visibility)
    * updated 'Collision' structure (hierarchical structure)
    * some changes to internal structures to provide better performance
  * VDP BG/Tile:
    * fixed a minor bug in VDP_setTileMapDataEx(..) and VDP_setTileMapDataRectEx(..) methods (thanks to Alekmaul for reporting it)
  * Minors fixes...

**SAMPLE**
  * Bench:
    * fixed math tests for GCC 6.3


## Changelog 1.22a (September 2016) ##

**LIBRARY**
  * VDP: reintroduced the 16 plain system tiles.


## Changelog 1.22 (September 2016) ##

**DOCUMENTATION**
  * minors improvements and fixes

**COMPILER**
  * Rescomp: fixed a minor issue in sprite resource
  * XGMTool:
    * added duration information to XD3 tag
    * improved loop
  * added the XGM ROM builder tool.
  * removed GenRes from makefile

**LIBRARY**
  * Sprite Engine:
    * fixed sprite attribut update for non visible sprite
    * fixed sprite list update in certain condition
  * Sound:
    * moved XGM driver method in a specific unit (xgm.c)
    * added `XGM_getElapsed(..)` method to retrieve elapsed XGM music playing time (in number of frame)
    * added `XGM_setLoopNumber(..)` to set the wanted number of loop in XGM music play.
    * added interrupt protection for Z80 access
  * Maths:
    * reverted `fix32Mul()` and `fix32Div()` to previous version to avoid cumulative error
    * added `getApproximatedLog2(..)` method for fast Log2 calculation (approximated)
    * added `getLog2Int(..)` method for integer Log2 calculation
  * Misc:
    * moved QSort methods to tools
    * added generic qsort with custom comparator callback
  * VDP: more flexible VRAM tilemap configuration (window plan don't have to be first map).
  * Bitmap mode: can now set bitmap mode in window plan
  * changed to MIT license
  * refactoring

**SAMPLE**
  * Bench: added sprite donut animation test.


## Changelog 1.21 (May 2016) ##

**LIBRARY**
  * SPRITE: fixed a bug causing corrupted sprite after `SPR_release(..)` operation
  * TOOLS: reintroduced `zlib_unpack(..)` method (accidentally removed from header)

**SAMPLE**
  * Bench
    * fixed a bug causing address error on real hardware during `Sprite test`.
    * added 2 tests in `BG test`


## Changelog 1.2 (May 2016) ##

**COMPILER**
  * Rescomp: updated to version 1.5 (with updated documentation)
    * updated SPRITE resource compilation to the new SGDK Sprite structures.
    * fixed minor issue on IMAGE resource packing.
    * now using constants for sound driver (less confusing, got annoying bug because of that).
    * changed header _define_ name generation to avoid conflict between 2 identical named file.
    * fixed a bug in tilemap optimization for flipped tiles.
    * removed all packers not anymore used in SGDK.
    * minor change to XGM resource to support extra parameter
    * fixed a minor bug in sprite structure definition
  * XGMTool: updated to version 1.64
    * major structure changes for faster conversion/optimization operations
    * improved VGM to XGM conversion.
    * added options to disable some PCM auto processing
    * new options available to handle specific case and improve conversion process
    * added GD3 tag support.
    * better handling of PAL/NTSC timing
    * fixed pal information lost during XGC conversion.
    * more accurate loop position
    * fixed a minor issue in offset calculation.
    * fixed VGM loop information export (when using VGM optimization)
  * WavToRaw
    * fix 64-bit issues, it is still not endian safe.
    * check for read errors.
  * Appack: minor fix for silent parameter.
  * Added new custom LZ4W packer (require Java to be installed).
  * Removed GenRes tool (not anymore used and can confuse with rescomp).
  * added GDB tool (not yet really used yet)
  * Separated _debug_ and _release_ library build for easier profile switch.

**LIBRARY**
  * BITMAP
    * allow to change the plan used for bitmap rendering
    * added buffer preservation option (severe impact on performance)
    * fixed minors issues on reset/initialization process
  * DMA: added new DMA queue system in _dma_ unit, you can consider _vdp\_dma_ unit as deprecated (still provided for backward compatibility).
    * we can now limit the max transfer capabilities in a single frame with `DMA_setMaxTransferSize(..)`
    * can now define the DMA queue size with DMA_init(..) method.
    * added `DMA_setIgnoreOverCapacity(..)` to change DMA strategy when reaching max capacity.
  * GRAPHIC
    * added news methods for allocation and compression stuff (see TOOLS section)
    * added dynamic VRAM allocation (_vram_ unit which replace _tilecache_ unit)
  * PALETTE
    * fixed `RGB24_TO_VDPCOLOR` so it does what it says.
    * better palette fading using rounding.
    * fixed issue using sync fading locking interrupts (can cause XGM music lag).
  * MATHS
    * added `abs(..)` method.
    * fixed `fix32ToRoundedInt()` and `fix32Round()` defines (added parenthesis around)
    * replaced `distance_approx(..)` by `getApproximatedDistance(..)`
    * changed fix32 div/mul calculation strategy for better value preservation
  * MEMORY
    * added `MEM_getAllocated()` to return current dynamically allocated memory.
    * added `MEM_dump()` to dump in Gend KMod console the memory allocation table
  * SOUND
    * renamed `Z80_DRIVER_4PCM_ENV` to `Z80_DRIVER_4PCM`
  * SPRITE: complete rewrite of sprite engine !
    * many changes including the API.
    * should be faster but will be more optimized in future.
  * STRING
    * added isdigit(c), strnlen(..) and the very useful sprintf(..) ma
    * added strncpy(..) method.
    * replaced strreplace(..) by strreplacechar(..)
    * fixed fix32ToStr(..) and fix16ToStr(..) methods
  * SYSTEM
    * tried to more more compatible with default GCC stdint.h definitions
    * added `SYS_setVIntPreCallback(..)` so you can have your method called at VInt before any internal SGDK stuff are proceed.
    * added `SYS_isNTSC()` and `SYS_isPAL()` methods for easy system determination.
    * minor fix on SP register initialization (preserve value set in vector table)
    * added `SYS_hardReset()` to force hard reset.
  * TOOLS:
    * added new `LZ4W` compression (very fast unpacking but average compression level)
    * removed `RLE`, `RLE_MAP` and `UFTC` compression (LZ4W performs better in almost all cases).
    * removed `UnpackEx(..)` method (useless now).
    * added `setRandomSeed(u16 seed)` to initialize randomizer.
  * VDP
    * renamed `WPLAN` / `WINDOW` / `VDP_WINDOW` to `VDP_PLAN_WINDOW`
    * renamed `APLAN` to `VDP_PLAN_A`
    * renamed `BPLAN` to `VDP_PLAN_B`
    * renamed `SLIST` / `VDP_SPRITE_LIST` to `VDP_SPRITE_TABLE`
    * renamed `HSCRL` / `VDP_SCROLL_H` to `VDP_HSCROLL_TABLE`
    * added `planWidth` / `planHeight` to replace VDP_getPlanWidth() / VDP_getPlanHeigth() for faster internal SGDK calculations.
    * added `windowWidth` / `windowHeight` for faster internal SGDK calculations.
    * added `VDP_setWindowHPos(..)` and `VDP_setWindowVPos(..)` methods to set window positions.
    * fixed a bug with `VDP_setBPlanAddress(..)` method.
  * VDP BG/TILE
    * replaced `VDP_PLAN_A` / `VDP_PLAN_B` constants by `PLAN_A` / `PLAN_B` in some methods.
    * some methods now support `PLAN_WINDOW` parameter.
    * added `VDP_clearTextAreaBG(..)`, `VDP_clearTextLineBG(..)`, `VDP_clearTextArea(..)` methods.
    * modified `VDP_drawTextBG(..)` method.
    * others minors changes.
  * VDP SPRITE: major rewrite of _vdp\_sprite_ unit (require project modifications) !
    * replaced `SpriteDef` structure by `VDPSprite` structure (fit better hardware structure).
    * added dynamic allocation of hardware sprite: `VDP_allocateSprites(..)`, `VDP_releaseSprites(..)`, `VDP_getAvailableSprites()`
    * `VDP_updateSprites(..)` can now use DMA queue.
    * many others changes.
  * XGM driver
    * better handling of main BUS contention with DMA
    * added methods to improve BUS contention when using PSG sound in music.
    * fixed PCM play status when PCM is used from XGM music.
    * minor fix in driver code for better music frame sync.
    * better pause/resume support.
    * music sync is now handled on 68000 side for more flexibility (adjustable tempo).
  * Z80
    * modified writeYM macros
* memory usage optimizations.

**SAMPLE**
  * Bench
    * added new sample for general test and benchmarking.
  * Sound
    * minors changes about Z80 load information for XGM driver.
  * Sprite
    * added basic enemies (no collision yet)
    * added basic SFX
    * updated to last SGDK
    * some refactoring

**DOCUMENTATION**
  * several update and fixes here and there (some tags were not correctly recognized in later doxygen version).



## Changelog 1.12 (March 2015) ##

**COMPILER**
  * XGMTool
    * minors changes and fixes.

**LIBRARY**
  * SPRITE
    * added `VDP_resetSpritesDirect()` method.
  * SOUND
    * minor fix to XGM driver (PCM in music was wrong in some case).



## Changelog 1.11 ##

**LIBRARY**
  * CONTROLLER
    * fixed small issue in joystick code (Chilly Willy).
  * SOUND
    * added Z80 CPU load information in XGM driver (experimental).



## Changelog 1.10 ##

**COMPILER**
  * XGMTool
    * removed DAC enabled command (automatically handle by the XGM driver).
    * added DAC enabled state (XGM driver uses it when no PCM are playing).
    * now uses the VGM 1.60 _stream id_ information to allow multi PCM channel for XGM conversion (note that each channel has its own priority as VGM music does not contains PCM priority information).

**LIBRARY**
  * VDP
    * `VDP_fade(..)` method now automatically disables interrupts if needed.
  * SPRITE
    * minor optimization in the Sprite Engine to quickly discard disabled sprites (visibility forced to off).
  * SOUND
    * added automatic DAC enabled control (XGM driver).
    * fixed issue with music pause operation on real hardware (XGM driver).
    * minor tweak to reduce a bit the size of the Z80 drivers.
    * removed _Z80\_DRIVER\_4PCM_ which is useless (use _Z80\_DRIVER\_4PCM\_ENV_ driver instead).
  * CONTROLLER
    * added Sega Phaser support (Chilly Willy).
  * SYSTEM
    * disable library debug info.
  * SAMPLE
    * updated _Joy_ sample to add Phaser test (Chilly Willy).
    * updated _Sound_ sample to remove _Z80\_DRIVER\_4PCM_ test and add an example of the MVS driver PCM SFX.



## Changelog 1.01 ##

**COMPILER**
  * fixed bugs in XGMTool.
  * removed linear interpolation when converting WAV file.
  * others minors changes.



## Changelog 1.00 ##

A big addition for SGDK 1.00, the new XGM sound driver !
You can find more informations about it in the [XGM driver specifications](https://www.dropbox.com/s/bu348hu29ttl6la/xgm.txt?dl=0).

**COMPILER**
  * Rescomp
    * added support to XGM resource in rescomp.
  * added xgmtool to convert VGM into XGM and compile XGM file.
  * removed Genitile tool sources.
  * updated wavtoraw to support sample interpolation.

**LIBRARY**
  * VDP
    * added `VDP_setScanMode(u16 mode)` method to change the interlaced mode.
    * added `VDP_interruptFade()` method to interrupt async palette fading.
  * SPRITE
    * fixed a bug with `SPR_init(..)` method when using same definition, sometime timer could be not reseted and then animation is not working anymore.
    * fixed declaration of `VDP_setSprite(..)` / `VDP_setSpriteDirect(..)` / `VDP_setSpritePosition(..)` methods.
  * SOUND
    * Z80 memory is cleared before loading a custom driver.
    * added Z80\_read(..) and Z80\_write(..) methods for simple Z80 RAM read/write operations.
    * added XGM driver methods:
      * `u8 SND_isPlaying_XGM();`
      * `void SND_startPlay_XGM(const u8 *song);`
      * `void SND_stopPlay_XGM();`
      * `void SND_resumePlay_XGM();`
      * `u8 SND_isPlayingPCM_XGM(const u16 channel_mask);`
      * `void SND_setPCM_XGM(const u8 id, const u8 *sample, const u32 len);`
      * `void SND_setPCMFast_XGM(const u8 id, const u8 *sample, const u32 len);`
      * `void SND_startPlayPCM_XGM(const u8 id, const u8 priority, const u16 channel);`
      * `void SND_stopPlayPCM_XGM(const u16 channel);`
  * MATH
    * minor fix in min/max defines.
  * CONTROLLER
    * fixed declaration of `JOY_readJoypadX/Y(..)` methods (they should return s16 and not u16)
  * SYSTEM
    * sega.s and rom\_head.c files are now copied into the _src/boot_ project folder so they can easily be customized per project.
  * SAMPLE
    * modified sound sample to add XGM driver example.
  * some fixes in the doxygen documentation.
  * others changes and improvements.



## Changelog 0.96d ##

**LIBRARY**
  * removed direct VRam Map data unpacking as it was buggy.



## Changelog 0.96c ##

**COMPILER**
  * Rescomp
    * fixed some issues on compression.
    * now accept string to define which compression to use (AUTO, APLIB, RLE) in resource definition.

**LIBRARY**
  * minors changes to Doxygen documentation.



## Changelog 0.96 ##

**COMPILER**
  * Rescomp
    * improved BMP image support.
    * byte data are now output in word format to avoid the GCC bug (compilation with `-g` flag fails when byte data is encountered).
    * fixed issue on empty sprite animation detection.
    * fixed path separator issue on old windows system.
    * fixed compilation issues on unix system.
  * Makefile
    * Added `release` and `debug` targets to makefile (default target is `release`, `debug` target allow you to use GDB interactive debugger through emulator supporting it).
  * added `appack` tool sources code (compatibility for linux system).
  * some cleanup in `bintos` tool (removed the useless `-sizealign` command done by `sizebnd` tool).

**LIBRARY**
  * VDP
    * fixed palette fading methods where the last frame colors weren't always correct.
    * `VDP_drawImage(..)` and `VDP_drawBitmap(..)` now use dynamic VRAM tile index so they does not erase anymore the previous drawn image. `curTileInd` variable which contains the VRAM tile index where next tile will be uploaded is public.
  * TILE
    * fixed some bugs in the tile cache engine.
    * removed the`MEM_free(..)` call from the VInt callback (tile cache engine). We don't need anymore to disable interrupts at each memory allocation operation for safety ;)
  * SPRITE
    * fixed some bugs in the sprite engine.
    * added `SPR_setAlwaysVisible(..)` and `SPR_setNeverVisible(..)` to force (not) visibility on sprite (sprite engine)
  * BITMAP
    * minor performance improvement on the `BMP_drawPolygon(..)` method.
  * SOUND
    * fixed YM2612 write methods (can have issue on Megadrive 2 system).
  * DMA
    * fixed VRam Copy DMA.
  * MATH
    * fixed 2D projection calculation in `M3D_project_xxx(..)` methods. Now the camera distance is correctly taken in account for the final projection (adding a minor impact on performance).
  * SYSTEM
    * fixed soft reset issues.
  * TIMER
    * fixed a minor issue with `getTime(..)` method.
    * `waitSubTick(..)` is now more accurate when called from V-Interrupt code.
  * SAMPLE
    * minors changes and improvements on the Sonic Sprite sample.
    * minors changes to 3D cube flat sample.
  * DEBUG
    * added some KDebug log methods (`KLog, KLog_Uxx, KLog_Sxx...`)
  * MISC
    * added `strcmp(..)` method.
    * others changes and improvements.