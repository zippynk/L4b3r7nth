L4b3r7nth Specifications v0.3

(c) Copyright 2014-2015 Nathan Krantz-Fire. Some rights reserved.
This work is licensed under the Creative Commons Attribution-ShareAlike 4.0 International License. To view a copy of this license, visit http://creativecommons.org/licenses/by-sa/4.0/.

L4b3r7nth is an esoteric programming language focused around spreadsheets.

https://github.com/zippynk/l4b3r7nth

Syntax:
BEGIN |METHOD_NAME| DIRECTION INCREMENT
COMMAND |arguments|go|here| DIRECTION INCREMENT And the rest is ignored and can be anything.
MULTI-WORD-COMMAND |arguments|go|<VALUE |arguments|go|here|>|here| DIRECTION INCREMENT And the rest is ignored and can be anything.
END

This goes in a spreadsheet.

The method “START” is executed at the beginning of the program. The method “END” is executed when the program is about to terminate

Global methods:

BEGIN |method|
FINISH ||
OUT |text|
IN |text|resulting_variable|
SETCELL |x_position|y|y_position|value|
FLAGCELL |x_position|y_position|cell_type|
MOVECURSOR |x_position|y_position|
DELETE-UNUSED-CELLS ||
NULL ||
RUN |method|number_of_times|
IFRUN |condition|method|number_of_times|
PLUGIN-[Plugin name goes here]-[Command name goes here] |arguments|go|here|
PARENTMODULE-[Command name goes here] |arguments|go|here|
GOTO |x_position|y_position| Comments go right afterward since this is a moving command and therefore does not move right afterward.

Global values:

<CELL ||>
<HOUR ||>
<MINUTE ||>
<SECOND ||>
<DAY ||>
<WEEK ||>
<MONTH ||>
<YEAR ||>
<PROGRAM-CLOCK ||>
<NULL ||>
<ADD |first_number|second_number|>
<SUBTRACT |first_number|second_number|>
<MULTIPLY |first_number|second_number|>
<DIVIDE |first_number|second_number|>
<MODULO |first_number|second_number|>
<EXPONENT |first_number|second_number|>
<JOIN |first_string|second_string|>
<CONVERT |thing|data_type|>
<PLUGIN-[Plugin name goes here]-[Reporter name goes here]> |arguments|go|here|>
<PARENTMODULE-[Value identifier goes here] |arguments|go|here|>

Cell types:
"data": Data, usually a variable. Cannot be executed. Reset to blank on program start. Default cell type for previously blank cells with data added.
"code": Computer program code. Can be executed. Default cell type for data in the spreadsheet at launch.
"blank": Contains nothing. Setting a cell to this will erase it. Cannot do anything. Default cell type for cells.
"curses-editable": Shown to the user as a TUI, can be edited by the user with the keyboard. Any key non-navigation key pressed overrides the current cell, which can be controlled with the "MOVECURSOR |x|y|" command. This cell can only have one character in it - more will produce an error and end the program. While there are curses cells, no IN or OUT commands can be given - if any are, it will produce an error and end the program.
"curses-noneditable": Shown to the user as a TUI, static to the user. The user's cursor can be controlled with the "MOVECURSOR |x|y|" command. This cell can only have one character in it - more will produce an error and end the program. While there are curses cells, no IN or OUT commands can be given - if any are, it will produce an error and end the program. 

Removed Modules:
CREATE, SET, and DELETE. Use data cells.
END |module|. Changed to "FINISH ||" and no module is specified - it just ends the current one.
