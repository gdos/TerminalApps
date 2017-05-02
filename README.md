![screenshot](https://github.com/fastrgv/TerminalApps/blob/master/sok3.jpg)

# TerminalApps
Old school puzzle games that run in a terminal on any OS.

All source code is under "releases...latest", or this link:

https://github.com/fastrgv/TerminalApps/releases/download/v1.1.1/term2may17.tar.gz


# TerminalApps

## What's new:


**ver 1.1.1 -- 2may17**

* added DirtyDozen [external] solver (bfsl.adb) that handles L-shaped blocks.
* embedded autosolvers initiated by the (=)-key into:
	* tdd (DirtyDozen)
	* trush (TrafficRush)
	* tslid (BlockSliders)
	* tsok (Sokoban)


**ver 1.1.0 -- 5jan17**

* Now supply prebuilt binaries for OS-X and Linux;
* Improved build system.


**ver 1.0.9 -- 20aug16**

* added two sokoban solvers (puller.adb, ibox.adb).
* added tslid solver (bfs.adb).
* added trush solver (bfsr.adb).
* improved pacman gameplay, collision-detection, randomization.


**ver 1.0.8 -- 27jul16**

* added Terminal-DirtyDozen block slider (tdd.adb)
* added restart option to tslid.adb, trush.adb
* added Terminal-Pacman (tpac.adb)


**ver 1.0.7 -- 16jul16**

* added Panama Canal puzzle (tpan.adb)
* added HoleInOne, HoleInOne+4 (thio.adb, thio4.adb)
* added Nine puzzle (t9.adb)


**ver 1.0.6 -- 11jul16**

* fixed logic error in TerminalRush (trush.adb)



**ver 1.0.4 -- 5jul16**

* added tsok game.


**ver 1.0.3 -- 3jul16**

* added a block slider puzzle TerminalBlock (tslid.adb) to support Klotski style games.
* Greater care taken to properly handle key-escape-codes.
* Improved help screens.


**ver 1.0.2 -- 28jun16**

* found and used additional key-mapping associations.  In particular the arrow keys are now accepted since typically (up)=>'A', (rt)=>'C', etc.
* created terminal-rush (trush.adb)...a terminal version of the well known traffic rush puzzle game.

**ver 1.0.1 -- 25jun16**

* generalized two codes to be nearly identical;
* added clarifications within this document;


**ver 1.0.0 -- 24jun16**

* original release.


===============================================================
## Introduction
TerminalApps contains games that run on OS-X and Gnu/Linux, but can also be rebuilt to run on any OS capable of installing the GNAT GPL Ada compiler.

Includes Pacman and 10 puzzle games that use ascii characters only:  trush(rush-hour), tslid(klotski), t7(flat7), taz(flatAZ), tsok(sokoban), tpan(panama), thio(hole-in-one), thio4(hole-in-one+4), t9(nine), tdd(dirty-dozen), tpac(Pacman).

Usable keys for all:

* arrow-keys for movement;
* (q)=quit
* (?)=help toggle


=====================================================================
### terminal-pacman (tpac.adb)
A minimalist version of Pacman with 9 predefined levels.  Playable now, with further improvements expected.

### terminal-7 (t7.adb), terminal-A2Z (taz.adb)

t7 is a flat representation of a 2x2x2 cube with one missing that allows sliding permutations.  Here, the 8-1 elements are labelled 1..7.

taz is a flat representation of a 3x3x3 cube with one missing that allows sliding permutations.  The 27-1 elements are conveniently labelled with the english alphabet.

Both the "taz" and "t7" puzzles work the same:

* note the original order, and blank location;
* mix;
* then restore.

A character in an adjacent row, column, or layer may be moved to the empty space using the keyboard.

Pressing the (home) key on a typical keyboard produces the character 'H'.  So assuming that (home)=>'H', (end)=>'F', (up)=>'A', etc...
the key mapping follows:

* (1)..(5): mix;  higher values are more difficult.

* (up),(i): north
* (dn),(k): south
* (rt),(l): east
* (lt),(j): west
* (home),(\),(u),(.),(-): layer-up
* (end),(/),(o),(+): layer-dn

* (?): help
* (q): quit


### terminal-rush (trush.adb)

Horizontal and vertical strings of letters represent cars and trucks in a crowded parking garage.  The objective is to move them around lengthwise in order to be able to get car "a" to the exit, which is either at the right or top of the garage.  Note that the last digits in each puzzle name represents the minimum number of moves to win.

Now, an autosolver is embedded into this game.  At any time you may press the (=)-key to begin stepping toward a solution.

### terminal-block (tslid.adb), terminal-dirtydozen (tdd.adb)

Blocks of letters can be moved wherever there is space.  The objective is to move the block labelled "a" to an indicated goal position.

Now, an autosolver is embedded into these games.  At any time you may press the (=)-key to begin stepping toward a solution.


#### Gameplay:  
First, one selects a block or vehicle by typing its identifier letter.  Then use the arrow keys to move it.  Here, "?" toggles the help screen.  Note that manual selection is not always necessary as there is an auto-select mechanism for those times when only one selection may move in a given direction.  The "+" and "-" keys [next, previous] are used to cycle through the large number of predefined puzzles.


### terminal-sokoban (tsok.adb)

Move the pusher >< with the arrow keys in order to push all the boxes [] onto the goals :: in which case they look like {}.  Various other functions available on the help screen.  Includes a very large family of puzzle files.

Two [external] sokoban solvers named puller & ibox have been added.  The command line is "solver-name puzzle-file-name max-levels level-number".  Note that the max-levels are embedded into each puzzle file name.

The output file (named similarly to the input file) contains directions from the set {u,d,l,r,U,D,L,R}, where upper case indicates a push.  It is size-limited to 17 or fewer boxes, and 128 or fewer interior puzzle positions.  Compile it with the command "cmp.sh puller" or "cmp.sh ibox".

There are many cases these solvers cannot handle, but they are pretty good at sovling certain types of puzzles, particularly the more dense ones.

But now a time-limited solver is embedded into tsok.  At any time you may press the (=)-key to see if the solver can help you.  If so, you will be prompted to keep pressing that same key to proceed toward a solution.  No prompt means either the present state is unsolvable, or merely that the embedded algorithm failed.


### Terminal-HoleInOne (thio.adb, thio4.adb)
Move the 2x2 'a' block into the center of the four L-shaped corner pieces.

### terminal-panama (tpan.adb)
Move letters to spell "panama canal" !

### terminal-Nine (t9.adb)
Reverse the order of the numbered blocks.


===========================================================================
## Compiler Scripts
There are two scripts, lcmp.sh for Linux, and ocmp.sh for OS-X that are already setup for convenience.  They differ only in where the executables are put.  Now with 11 different precompiled binaries for each OS, there would be too much clutter if they were all put into the same place.  The references below that mention "cmp.sh" refer to the script appropriate to your operating system.

Similarly, there are also two scripts that build everything at once called "lbuildall.sh" and "obuildall.sh".

===============================================================
## Build Instructions:
Manually install GNAT GPL from libre.adacore.com/download/.  If you don't like my key-mappings, edit the code as you like.

Next, edit the script "cmp.sh" so that the path to gnatmake is temporarily prepended to the PATH environment variable.  This script streamlines the build process by allowing auxilliary libraries and files to be neatly hidden in subdirectories.  And make sure it is executable.

Then type "cmp.sh game", where game is in the set {t7, taz, trush, tslid, tsok, tpan, thio, thio4, t9, tdd, tpac} to create a command-line executables for your system.

===============================================================
## Running:
Your terminal must accept the "clear" command, and must be 50 chars wide by 20 lines (57x35 for pacman).  Simply type the executable name to begin.  

For example, on OSX, you would open a terminal, and cd to the install directory and type:

./bin/osx/tsok

to run the Sokoban game.

===============================================================
## Legal Mumbo Jumbo:

TerminalApps is covered by the GNU GPL v3 as indicated in the sources:

 Copyright (C) 2017  <fastrgv@gmail.com>

 This program is free software: you can redistribute it and/or modify
 it under the terms of the GNU General Public License as published by
 the Free Software Foundation, either version 3 of the License, or
 (at your option) any later version.

 This program is distributed in the hope that it will be useful,
 but WITHOUT ANY WARRANTY; without even the implied warranty of
 MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 GNU General Public License for more details.

 You may read the full text of the GNU General Public License
 at <http://www.gnu.org/licenses/>.

----------------------------------------------
## Other Credits and Thanks:
Serhiy Grabarchuk and Peter Grabarchuk for their "Hole in One", "Hole in One plus 4", and "Nine" puzzles.

Mike Billars [michael@gmail.com] for his C-version of Pacman for the console, after which this Ada version was modelled (gnu gpl).

----------------------------------------------
## Best Download Site for all my games:
https://github.com/fastrgv?tab=repositories
