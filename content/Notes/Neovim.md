---
date: 2023-09-30
---
Directional keys:
h j k l - left, down, up, right

x - delete character under the cursor
i - insert text right before the cursor

a - append text right after the cursor
A - append text right at the end of the line

dw - delete a word
d$ - delete to the end of the line

Many commands that change text are made from an operator and a motion.

It has the following format:

d motion

d - is the delete operator
motion - is what the operator will operate on (listed below)

Examples of motions:
w - until the start of the next word, EXCLUDING its first character
e - to the end of the current word, INCLUDING the last character
$ - to the end of the line, INCLUDING the last character

We can also add count for a motion

2w - move the cursor 2 words forward
3e - move the cursor to the end of the third word forward
0 - move to the start of the line

d2w - delete the next two words

dd - delete the whole line
2dd - delete two lines

u - undo the last commands
U - to fix a whole line

p - put previously deleted text after the cursor

rx - replace the character at the cursor with x

ce - change until end of a word
c$ - change until end of the line

Control-g - show your location in a file and the file status
G - move to a line in the file, if given a line number, otherwise jump to end of the file
gg - move to the start of the file

/<search term> - searches for the given search term
n - go to the next result
N - go to the next result in the opposite direction

? - search for phrase in the backward direction (instead of /)

Control-o - go back to where you came from. Repeat to go back further.
Control-i - go forward

% - find matching ), ], }

:s/<old>/<new> - substitute <new> for <old>
:s/<old>/<new>/g - same as above but apply the substitution globally in the line
:#,#s/<old>/<new>/g - same as above but apply between two lines (#,# is a range)
:%s/<old>/<new>/g - apply it for the whole file
:%s/<old>/<new>/gc - apply it for the whole file, with a prompt whether to substitute or not

:!<command> - execute some command

v - go into visual mode to select text, and afterwards do ":"
:r <Filename> - retrieve contents of <Filename>
:r !<Command> - read output of a command

o - open a line below the cursor
O - open a line above the cursor

R - replace more than one character

y - yank (copy) text
p - put it

While searching,
:set ic - ignore case
:set hls is - hlsearch and incsearch option
:set noic - disable ignoring case
:set invic - inver the value of a setting (prepend a setting with "inv")
:nohlsearch - remove highlighting of matches

:help - get the help window

Control-w - jump to one window




