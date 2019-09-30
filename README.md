# VT100-Labview-Emulator
Creates a Table to emulate a VT100 terminal.

The VI takes reads a string from a VISA Read vi. First, it searches for the Escape Code pertaining to the Cursor Position. 
Then it extracts the data and position (row,col) into a 2D array. Using the position information, a table (2d array) is 
built to replicate the VT100 screen. Steps where taken to reduce the size of this table to more accurately represent
the VT100 screen.
The device currently using this VI sends 4096 bytes of data every second.  It only sends 3 types of Escape Codes:
the "Clear Screen" command (which I ignore), the "Cursor Position" command (used to build the table), and the 
"Reserve Video" command, (used to highlight section headers).

The two Escape Code commands used to build the tables are:
The Cursor position code - Esc\[Line;ColumnH
The Reverse Video code   -  Esc\[7m <highlight string> Esc\[m
