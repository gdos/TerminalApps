# TerminalApps
Fun puzzle games that run on any terminal on any OS.

All source code is under "releases" named "termapps30jun16.tar"



# TerminalApps v 1.0.2

## What's new:

**ver 1.0.3 -- 30jun16**

* added a block slider puzzle TerminalBlock (bslid.adb) to support Klotski style games.


**ver 1.0.2 -- 28jun16**

* found and used additional key-mapping associations.  In particular the arrow keys are now accepted since typically (up)=>'A', (rt)=>'C', etc.
* created terminal-rush (rush.adb)...a terminal version of the well known traffic rush puzzle game.

**ver 1.0.1 -- 25jun16**

* generalized two codes to be nearly identical;
* added clarifications within this document;


**ver 1.0.0 -- 24jun16**

* original release.


===============================================================
## Introduction
TerminalApps contains F.O.S.S. puzzle games that can be run on any terminal in any OS that has a gnat compiler.  

There are now 4 apps:  seven, a2z, rush, bslid.

===============================================================
### seven, a2z

seven is a flat representation of a 2x2x2 cube with one missing that allows sliding permutations.  Here, the 8-1 elements are labelled 1..7.

a2z is a flat representation of a 3x3x3 cube with one missing that allows sliding permutations.  The 27-1 elements are conveniently labelled with the english alphabet.

Both the "a2z" and "seven" puzzles work the same:

* note the original order, and blank location;
* mix;
* then restore.

A character in an adjacent row, column, or layer may be moved to the empty space using the keyboard.

Typically, the (home) key produces the character 'H'.  So assuming that (home)=>'H', (end)=>'F', (up)=>'A', etc...
the key mapping follows:

* 1..5: mix;  higher values are more difficult.

* (up),i: north
* (dn),k: south
* (rt),l: east
* (lt),j: west
* (home),\,u: layer-up
* (end),/,o: layer-dn

* ?: help
* q: quit




### terminal-rush
Horizontal and vertical strings of letters represent cars and trucks in a crowded parking garage.  The objective is to move them around lengthwise in order to be able to get car "a" to the exit, which is either at the right or top of the garage.  Note that the last digits in each puzzle name represents the minimum number of moves to win.

### terminal-block
Rectangular blocks of letters can be moved wherever there is space.  The objective is to move the block labelled "a" to an indicated goal position.


#### Gameplay:  
First, one selects a block or vehicle by typing its identifier letter.  Then use the arrow keys to move it.  Here, "?" toggles the help screen.  Note that manual selection is not always necessary as there is an auto-select mechanism for those times when only one selection may move in a given direction.  The "+" and "-" keys [next, previous] are used to cycle through the large number of predefined puzzles.




===============================================================
## Build Instructions:
Manually install GNAT GPL from libre.adacore.com/download/.  If you don't like my key-mappings, edit the code as you like.

Next, edit the script "cmp.sh" so that the path to gnatmake is temporarily prepended to the PATH environment variable.  This script streamlines the build process by allowing auxilliary libraries and files to be neatly hidden in subdirectories.  And make sure it is executable.

Then type:

* cmp.sh seven
* cmp.sh a2z
* cmp.sh rush
* cmp.sh bslid

to create a command-line executables for your system.

===============================================================
## Running:
Your terminal must accept the "clear" command, and must be at least 48 chars by 14 lines.  Simply type "seven", "a2z", "rush", or "bslid" to begin.


===============================================================
## Legal Mumbo Jumbo:

TerminalApps is covered by the GNU GPL v3 as indicated in the sources:

 Copyright (C) 2016  <fastrgv@gmail.com>

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


