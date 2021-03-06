![screenshot](https://github.com/fastrgv/TerminalApps/blob/master/sok3.jpg)

# TerminalApps
Old school ascii character puzzle games that run in a terminal on Windows, OSX, & Linux.

Executables & source code is under this link:

https://github.com/fastrgv/TerminalApps/releases/download/v1.2.0/te29dec18.7z






# TerminalApps

## What's new:


**ver 1.2.0 -- 29dec18**

* Now request only high-priority rather than realtime-priority;
* Now deliver 7z archives for better compression and simplicity of extraction on all 3 platforms.



**ver 1.1.8 -- 30nov18**

* Made big improvement in Windows keyboard response by setting realtime mode programmatically;


**ver 1.1.7 -- 25nov18**

* Using improve autosolver in tsok;
* Improved autosolvers for trush, tslid, tdd.
* Corrected error in autoselect logic;



===============================================================
## Introduction
TerminalApps contains ascii-character games that run in a commandline terminal on msWindows, OS-X and Gnu/Linux. 

Now with runtime-priority control of console terminal, if needed.

They can also be rebuilt after installing the GNAT GPL Ada compiler.

Includes RPNcalc, Pacman and 10 puzzle games that use ascii characters only:  trush(rush-hour), tslid(klotski), t7(flat7), taz(flatAZ), tsok(sokoban), tpan(panama), thio(hole-in-one), thio4(hole-in-one+4), t9(nine), tdd(dirty-dozen), tpac(Pacman).

Keyboard setup is important.  You should have a short key-delay and fast repeat setting.  

Usable keys for all:

* arrow-keys for movement;
* (q)=quit
* (?)=help toggle


Windows games are all located in .\bin\win\;
Mac games are in ./bin/osx/;
Linux games are in ./bin/gnu/;

For example, to play rush-hour on a Mac you would type:
bin/osx/trush
or else cd to ./bin/osx/ then type
trush


=====================================================================
### terminal-pacman (tpac.adb)
A primitive version of Pacman with 9 predefined levels.

For this game, keyboard setup is critical to playability.  One must have a short key-delay and fast repeat setting.  The arrow keys, or wasd-keys, or ijkl-keys control movement.  The (x),(q) keys quit;  (p) pauses game.

Executable can now be given 2 optional command line parameters:
	* Game Speed 0..9;  0=slow, 5=default=medium, 9=fast;
	* Ghost Speed 0..9;  0=stopped, 2=default=easy, 9=fast

So on windows, the command:
"bin\win\tpac 5 2" 
gives default settings, same as giving no parameters:
"bin\win\tpac" 


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

* (up),(i),(w): north
* (dn),(k),(s): south
* (rt),(l),(d): east
* (lt),(j),(a): west
* (home),(\),(u),(.),(-): layer-up
* (end),(/),(o),(+): layer-dn

* (?): help
* (q): quit


### terminal-rush (trush.adb)

Horizontal and vertical strings of letters represent cars and trucks in a crowded parking garage.  The objective is to move them around lengthwise in order to be able to get car "a" to the exit, which is either at the right or top of the garage.  Note that the last digits in each puzzle name represents the minimum number of moves to win.

A stand alone autosolver, bfsr, is provided, but now, an autosolver is embedded into this game.  At any time you may press the (=)-key to begin stepping toward a solution.

### terminal-block (tslid.adb), terminal-dirtydozen (tdd.adb)

Blocks of letters can be moved wherever there is space.  The objective is to move the block labelled "a" to an indicated goal position.

A stand alone autosolver, bfsl, works for these puzzles, but now, an autosolver is embedded into these games.  At any time you may press the (=)-key to begin stepping toward a solution.


#### Gameplay:  
First, one selects a block or vehicle by typing its identifier letter.  Then use the arrow keys to move it.  Here, "?" toggles the help screen.  Note that manual selection is not always necessary as there is an auto-select mechanism for those times when only one selection may move in a given direction.  The "+" and "-" keys [next, previous] are used to cycle through the large number of predefined puzzles.


### terminal-sokoban (tsok.adb)

Move the pusher >< with the arrow keys in order to push all the boxes [] onto the goals :: in which case they look like {}.  Various other functions available on the help screen.  Includes a very large family of puzzle files.  Note that most any sokoban puzzle can become unsolvable after an unwise sequence of moves.

Two [external] sokoban solvers named puller & ibox have been added.  The command line is "solver-name puzzle-file-name max-levels level-number".  Note that the max-levels are embedded into each puzzle file name.

The output file (named similarly to the input file) contains directions from the set {u,d,l,r,U,D,L,R}, where upper case indicates a push.  It is size-limited to 17 or fewer boxes, and 128 or fewer interior puzzle positions.  Compile it with the command "cmp.sh puller" or "cmp.sh ibox".

There are many cases these solvers cannot handle, but they are pretty good at sovling certain types of puzzles, particularly the more dense ones.

But now a time-limited solver is embedded into tsok.  At any time you may press the (=)-key to see if the solver can help you.  If so, you will be prompted to keep pressing that same key to proceed toward a solution.  No prompt means either the present state is unsolvable, or merely that the embedded algorithm failed.  In this case, you can try to undo moves using the (u)-key until it again becomes solvable.


### Terminal-HoleInOne (thio.adb, thio4.adb)
Move the 2x2 'a' block into the center of the four L-shaped corner pieces.

### terminal-panama (tpan.adb)
Move letters to spell "panama canal" !

### terminal-Nine (t9.adb)
Reverse the order of the numbered blocks.

### RPN (reverse polish notation) command line calculator
A cult classic.  Recalls the HP rpn functionality.  Type "rpn".



===============================================================
## Setup & Running:


Mac users see "osx-setup.txt".
Windows users see "windows-setup.txt".

Unzip the archive.  On Windows, 7z [www.7-zip.org] works well for this.


Ensure your keyboard has a short key-delay and fast repeat.

Minimize the size of your terminal window.  Your terminal must be 50 chars wide by 20 lines (57x35 for pacman).  

Enlarge the Font so that the window fills your monitor.  

Simply type the executable name to begin.  

For example, on OSX, you would open a terminal, and cd to the install directory and type:  ./bin/osx/tsok   to run the Sokoban game.  You could also cd to the executable directory ./bin/osx/ then type:  tsok.

NOTE:  Windows users should probably CD to .\bin\win\ then run the script "hipri.bat" to open a realtime-priority window in which to run apps.  (It seems that some hardware may cause terminal freezes at normal priority.)  If that does not work, and the response is poor, try using the command "start /realtime [game].exe" where [game] is one of {t7,t9,taz,tdd,thio4,thio,tpac,tpan,trush,tslid,tsok}

Similarly for Linux/OSX users, you can CD to ./bin/gnu/ then use the "nice" command to be a bit less nice and give each terminal game the highest real time priority.  For example, to run traffic rush at high priority type:  "nice --adjustment=-20 trush".  See ~/bin/gnu/hipr.sh, ~/bin/osx/hipr.sh





===========================================================================
## Compiler Scripts
There are three scripts, wbuildall.bat for msWindows, lbuildall.sh for Linux, and obuildall.sh for OS-X.  They differ in where the executables are put.  Now with so many different precompiled binaries for each OS, there would be too much clutter if they were all put into the same place.


===============================================================
## Build Instructions:
Remember that prebuilt executables are already included.  If you want to rebuild...

Manually install GNAT GPL from libre.adacore.com/download/.  If you don't like my key-mappings, edit the code as you like.

Next, edit the scripts wcmp.bat or lcmp.sh or ocmp.sh so that the path to gnatmake is correct.  These scripts streamline the build process by allowing auxilliary files to be neatly hidden in subdirectories.  And make sure it is executable.

Then type "[wlo]buildall" to create new command-line executables for your system.



===============================================================
## What is special about this project?
* portability, transparency, and open source freedom;
* uses GNAT GPL;
* for developers, the Ada code is easy to understand;
* essentially no graphics, and no user interface;




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


----------------------------------------------
## Earlier Revision History:

**ver 1.1.6 -- 10aug18**

* Fixed tsok to handle DOS-format resume file.
* Corrected errors in autosolvers for rush & dirty12;


**ver 1.1.5 -- 10dec17**

* improved pacman (tpac);
* all games now runnable from home or bin/./ directory;
* The script hipri.bat for Windows was added to fix terminal-freezes by opening a high priority command window for console games.
* Also added scripts hipr.sh (linux & OSX) to run at high priority using "nice", if necessary.


**ver 1.1.4 -- 5dec17**

* added missing DLLs;
* now using the intrinsic file detection function:  Exists();
* elliminated need for directory links, simplifying Windows install.
* huge performance improvements by not erasing screens between redraws.


**ver 1.1.3 -- 29oct17**

* added RPN calculator;


**ver 1.1.3 -- 26oct17**

* added prebuilt executables for msWindows;
* added working build scripts for msWindows;


**ver 1.1.2 -- 18oct17**

* added keymaps for IJKL, WASD, when possible, eg. pacman;
* improved, corrected pacman code;
* minor correction to compilation scripts;


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

