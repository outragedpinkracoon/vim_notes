# Vim / Spacemacs Cheatsheet

## Navigation
h - left  
l - right  
k - up   
j - down  

$ - go to end of line  
0 - go to beginning of line  
Shift + i - go to the beginning and shift to editing mode  

G - move to the end of the buffer  
gg - move to the start of the buffer  

:{line_number} - go to a given line e.g. :102 will go to line 102  

w - move forward one word, having cursor at the start of the word  
e - move forward one word, having cursor at the end of the word  
b - move backwards one word

U - move to the top of the screen  
L - move to the bottom of the screen  
M - move to the middle of the screen  

## Insertion
i - insert before  
a - insert after  
A - moves to the end of the line and enables insert mode (NICE!)

## The open command
o - open a line below the cursor and enable insert mode  
O - open a line above the cursor and enable insert mode  

## Deletion
dw - delete to end of word  
d$ - delete to the end of the line  
dd - delete the entire line  
2dd - delete 2 lines  

x - delete character under the cursor  
X - delete character before the cursor  

daw - delete the word under the cursor  
caw - delete the word under the cursor and put you in insert mode

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

## Select all
ggVG

gg - move to the top of the buffer  
V - select current line  
G - move to end of buffer  

## Puts
p - pastes the contents of the buffer.  
If it’s a char, it’s pastes after the next char, if it’s a line, it’s after the next line and so on.  

## Replace
r + character - replaces the character that the cursor is on  
R - allows you to type over existing text starting from the cursor posititon.  
Press ESC when finished.

## Duplicate a line
yyp - copies a line then pastes it below the original  
ddp - swap current line with the next

## Move lines
[e - move line up
]e - move line down

## Go to last change
'. (looks weird right?)

## Searching
While in command mode (prefixed with colon to differentiate)

:%s/foo/bar replaces the FIRST instance of foo with bar  
:%s/foo/bar/g replaces ALL instances of foo with bar  
:%s/foo/bar/gc replaces ALL instances of foo with bar but asks for confirmation each time

## Highlighting
/* - highlight all occurences of the word under the cursor. Will then traverse forward through matches on subsequent presses, use # to traverse backwards.  
:noh - typing this in command mode will remove all the highlights

## Change word
cw - deletes a word or to the end of a word based on the current cursor position then places you in insert mode.  
We can use this in the same manner as delete e.g. c$ will delete to the end of the line from the current cursor.

## Insert the contents of a file
:r {filename} - places the contents of a file under the current cursor location

## Search
/{term}{enter} - search forwards for a term  
?{term} - search backwards for a term  
n - traverse forwards through matches  
N - traverse backwards through matches

## Matching brackets
% - takes you to the corresponding matching bracket

## Files Management
SPC p f will open the fuzzy file search  
SPC b b - open recent files  
SPC f s - save changes to file  
(same as :w in command mode)  
SPC f S - save all open files  
(same as :wqa in command mode)

## Window management
SPC w v - split vertically  
SPC w s - split horizontally  

SPC w l - move to window on the right  
SPC w h - move to window on the left

## Toggle Line Numbers
SPC t n

## Tree view
SPC f t - open tree view  
The tree view is clickable, and can be focused and unfocused using the window commands mentioned previously.  
It is traversed using hjkl or the arrow keys as normal. Hitting enter will expand a folder.

Pressing | on an item in the tree view opens it up in a new vertical frame
