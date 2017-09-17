# Vim Notes

## Navigation
h - left
l - right
k - up 
j - down

$ - go to end of line
0 - go to beginning of line
Shift + i - go to the beginning and shift to editing mode

## Insertion
i - insert before 
a - insert after

## Deletion
dw - delete to end of word
d$ - delete to the end of the line
dd - delete the entire line

## Command Format

The format for commands is:

[number] [command] object

command: the command to execute
number: how many times to execute the command
object: what the command will operate on

Objects might be:
w - from the cursor to the end of the word, including the space
e - from the cursor to the end of the word, not including the space
$ - from the cursor to the end of the line

## Undo
u - undo the last command
ctrl + r - redo

## Copy
- Position cursor at the beginning of the text you want to copy
- Press 'v' to select characters, V for whole lines, ctrl-v or ctrl-q for blocks
- Press 'y' to (yank) copy
- Move to desired paste location, press P to paste before or 'p' to paste after
