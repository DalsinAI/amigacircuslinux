Circus Linux! 1.0.3 for AmigaOS 3.x
===================================

Circus Linux! (Bill Kendrick, New Breed Software), the balloon-popping
game after Circus Atari: bounce the clowns off the teeter-totter up into
three rows of balloons, keep them from hitting the floor, one or two
players, with barriers, bouncy balloons and clear-all modes. For
AmigaOS 3.x on a 68040 or 68060 with an FPU and an RTG screen, on
OpenGPU's SDL 1.2 (sdl12-compat).

Base: circuslinux_1.0.3.orig.tar.gz from Debian (sha256
bf9550ebd598a9e7d93a20d80ff466475122f8b023314bb1e07c31e8c608ce8a), with
Debian's patches (1.0.3-35) as the second commit. Branch
team2/circuslinux-amiga.

Status: plays in the lab (Instance-45 on GFOpenUp 0.8.19, 6 November
2026): the title screen with its balloons, One Player (the teeter-totter
moved with the mouse, a clown launched, balloons popped, a clown lost,
the score), Escape to the final score, the title again, and Exit back to
the Shell, the settings and high scores written to circuslinux.dat. The
music and sounds load without an error; the lab is muted, so they were
not heard there.


What you need
-------------

- A 68040 or 68060 with an FPU, AmigaOS 3.x, an RTG card (or the
  AmigaChrome lab).
- GFOpenUp 0.8.18 or later (LIBS:OpenGPU/SDL2.module). Everything else is
  in the program.


How to play
-----------

Open the CircusLinux icon, or run CircusLinux from a Shell. It opens a
640x480 window (CircusLinux --fullscreen for the full screen, --low for
less drawing on a slow machine, --disable-sound). Click on the title
screen to choose a game, its options and the volumes; Escape there
quits. In the game the mouse moves the teeter-totter and the button
flips it, Space pauses, Escape ends the game. ReadMe-upstream in the
drawer is upstream's README. The pictures, sounds and music are in the
drawer's data/; the high scores and settings are circuslinux.dat in the
drawer.


Building
--------

    make -f amiga/Makefile.amigaos -j2 dist

with GFOpenAmigaGCC 16.2.0-open4, the OpenNDK headers, the OpenGPU kit and
the Team's static libpng and zlib (see the Makefile's head). The drawer is
dist/CircusLinux (and dist/CircusLinux.info).


What was changed
----------------

- circuslinux.c: on AmigaOS the settings and high scores are
  PROGDIR:circuslinux.dat (Debian's shared score file is not used).
- amiga/Makefile.amigaos builds circuslinux.c with configure's joystick
  support, the data at PROGDIR:data/.
- No SDL_image or SDL_mixer 1.2 for OpenGPU's SDL 1.2: the Team's
  amiga/sdl_image_lite.c (PNG on libpng) and amiga/sdl_mixer_lite.c (WAV,
  with libmikmod 3.3.16 for the music: amiga/libmikmod, its player,
  ProTracker loader and no-sound driver, at most 16 voices), from the
  Critical Mass port.
- amiga/stack.c: 256 KB of stack.


Licences
--------

Circus Linux!, its pictures, sounds and music: GPL 2 or later
(COPYING.txt; AUTHORS.txt in the source names who made them). libmikmod:
LGPL 2 or later (COPYING-libmikmod.txt). The Amiga files (amiga/): the
AmiCradle Team, GPL 2 or later, except the mixer, which comes from the
Team's Wizznic port and is GPL 3 or later, so the program as built here
is GPL 3 or later; the icon is upstream's data/images/icon.png.
