# TerminalApps
Fun puzzle games that run on any terminal on any OS.


# TerminalApps v 1.0.0

## Introduction
TerminalApps contains two F.O.S.S. puzzle games that can be run on any terminal in any OS that has a gnat compiler.  Both puzzles work the same:

* note the original order;  
* mix;  
* then restore.  

A character in the adjacent row, column, or layer may be moved to the empty space using the keyboard.

The key mapping follows:

* 1..5: mix;  higher values are more difficult.

* i: north
* k: south
* j: west
* l: east
* o: layer-dn
* u: layer-up

* h: help
* q: quit


### term7
Conceptually, this is a flat representation of a 2x2x2 cube with one missing that allows sliding permutations.  Here, the cubelets are labelled 1..7.

### term26
Conceptually, this is a flat representation of a 3x3x3 cube with one missing that allows sliding permutations.  Thus, the cubelets are conveniently labelled with the english alphabet.

## Build Instructions:
If you don't like my key-mappings, edit the code as you like. Then type:
* gnatmake term7
* gnatmake term26

to create a command-line executables for your system.

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
