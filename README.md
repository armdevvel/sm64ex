# sm64ex - for ARM Windows
Fork of [sm64pc/sm64ex](https://github.com/sm64pc/sm64ex) with fixed and patches for ARM Windows (ARMv7/Aarch64)

You will need all dependencies from the normal build, with the addition of LLVM-MinGW. If you're building for ARM Windows, check out [here for MXE + ARM Windows integration](https://github.com/armdevvel/mxe). Builds will be ran as so:

ARMv7/ARM32: `make CROSS=armv7-w64-mingw32- WINDOWS_BUILD=1 RENDER_API=D3D11 AUDIO_API=SDL2 DISCORDRPC=0`
Aarch64/ARM64: `make CROSS=aarch64-w64-mingw32- WINDOWS_BUILD=1 RENDER_API=D3D11 AUDIO_API=SDL2 DISCORDRPC=0`

The rendering API is forced to be D3D11 (atleast, on ARM32/ARMv7) because of missing DLLs or it is software only. On ARMv7, the game runs painfully slow because of only having DirectX11 SW, so a D3D9 port of fast-engine is being worked on, as Windows on ARM has hardware for DX9.

If there are any issues, never hesitate to open an issue!

# Original README

## sm64ex

Fork of [sm64-port/sm64-port](https://github.com/sm64-port/sm64-port) with additional features. 

Feel free to report bugs and contribute, but remember, there must be **no upload of any copyrighted asset**. 
Run `./extract_assets.py --clean && make clean` or `make distclean` to remove ROM-originated content.

Please contribute **first** to the [nightly branch](https://github.com/sm64pc/sm64ex/tree/nightly/). New functionality will be merged to master once they're considered to be well-tested.

*Read this in other languages: [Español](README_es_ES.md), [Português](README_pt_BR.md) or [简体中文](README_zh_CN.md).*

## New features

 * Options menu with various settings, including button remapping.
 * Optional external data loading (so far only textures and assembled soundbanks), providing support for custom texture packs.
 * Optional analog camera and mouse look (using [Puppycam](https://github.com/FazanaJ/puppycam)).
 * Optional OpenGL1.3-based renderer for older machines, as well as the original GL2.1, D3D11 and D3D12 renderers from Emill's [n64-fast3d-engine](https://github.com/Emill/n64-fast3d-engine/).
 * Option to disable drawing distances.
 * Optional model and texture fixes (e.g. the smoke texture).
 * Skip introductory Peach & Lakitu cutscenes with the `--skip-intro` CLI option
 * Cheats menu in Options (activate with `--cheats` or by pressing L thrice in the pause menu).
 * Support for both little-endian and big-endian save files (meaning you can use save files from both sm64-port and most emulators), as well as an optional text-based save format.

Recent changes in Nightly have moved the save and configuration file path to `%HOMEPATH%\AppData\Roaming\sm64pc` on Windows and `$HOME/.local/share/sm64pc` on Linux. This behaviour can be changed with the `--savepath` CLI option.
For example `--savepath .` will read saves from the current directory (which not always matches the exe directory, but most of the time it does);
   `--savepath '!'` will read saves from the executable directory.

## Building
For building instructions, please refer to the [wiki](https://github.com/sm64pc/sm64ex/wiki).

**Make sure you have MXE first before attempting to compile for Windows on Linux and WSL. Follow the guide on the wiki.**
