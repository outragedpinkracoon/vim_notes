# Vim Notes

## Day 1

### Navigation
h - left  
l - right  
k - up  
j - down

$ - go to end of line  
0 - go to beginning of line  
Shift + i - go to the beginning and shift to editing mode

### Insertion
i - insert before  
a - insert after

### Deletion
dw - delete to end of word  
d$ - delete to the end of the line  
dd - delete the entire line  
2dd - delete 2 lines

### Command Format
The format for commands is:

[number] [command] object

command: the command to execute  
number: how many times to execute the command  
object: what the command will operate on  

Objects might be:  
w - from the cursor to the end of the word, including the space  
e - from the cursor to the end of the word, not including the space  
$ - from the cursor to the end of the line  

### Undo
u - undo the last command  
ctrl + r - redo

### Copy
- Position cursor at the beginning of the text you want to copy  
- Press 'v' to select characters, V for whole lines, ctrl-v or ctrl-q for blocks  
- Press 'y' to (yank) copy  
- Move to desired paste location, press P to paste before or 'p' to paste after

##  Day 2

### Puts
p - pastes the contents of the buffer  
If it’s a char, it’s pastes after the next char, if it’s a line, it’s after the next line and so on.

### Replace
r + character - replaces the character that the cursor is on

### Searching
While in command mode (prefixed with colon to differentiate)

:%s/foo/bar replaces the FIRST instance of foo with bar  
:%s/foo/bar/g replaces ALL instances of foo with bar  
:%s/foo/bar/gc replaces ALL instances of foo with bar but asks for confirmation each time

### Highlighting
I found this one out by accident...

/* - highlight all occurences of the word under the cursor. Will then traverse forward through matches on subsequent presses, use # to traverse backwards.  
:noh - typing this in command mode will remove all the highlights

### Change word
cw - deletes a word or to the end of a word based on the current cursor position then places you in insert mode.  
We can use this in the same manner as delete e.g. c$ will delete to the end of the line from the current cursor.

### Navigation
G - move to the end of the buffer  
gg - move to the start of the buffer  
:{line_number} - go to a given line e.g. :102 will go to line 102

### Search
/{term}{enter} - search forwards for a term  
?{term} - search backwards for a term  
n - traverse forwards through matches  
N - traverse backwards through matches

### Matching brackets
% - takes you to the corresponding matching bracket

### Duplicate a line
yyp - copies a line then pastes it below the original

## Day 3

### File fuzzy search
SPC p f will open the fuzzy file search

### Window management
SPC w v - split vertically  
SPC w s - split horizontally

SPC w l - move to window on the right  
SPC w h - move to window on the left  
SPC w d - close window

### Navigation
w - move forward one word, having cursor at the start of the word  
e - move forward one word, having cursor at the end of the word  
b - move backwards one word

### Select all
ggVG

gg - move to the top of the buffer  
V - select the line  
G - move to end of buffer

### Tree view
SPC f t - open tree view  
The tree view is clickable, and can be focused and unfocused using the window commands mentioned previously.  
It is traversed using hjkl or the arrow keys as normal.  
Hitting enter will expand a folder.

Pressing | on an item in the tree view opens it up in a new vertical frame

### Open Recent Files
SPC b b

### Saving Files
SPC f s - save changes to file  
(same as :w in command mode)  
SPC f S - save all open files  
(same as :wqa in command mode)

### Swap two lines
ddp - swap current line with the next

### Toggle line numbers
SPC t n

## Day 4

### Moving around the screen
U - move to the top of the screen  
L - move to the bottom of the screen  
M - move to the middle of the screen

### Go to last change
'. (looks weird right?)

### Move lines
[e - move line up  
]e - move line down

### Adding space
[SPC - add space above  
]SPC - add space below

### Deleting characters
x - delete character under the cursor  
X - delete character before the cursor

### Deleting words
daw : delete the word under the cursor  
caw : delete the word under the cursor and put you in insert mode

### Execute an external command
:!{external command} e.g. :!ls

### Create a file
:w {name of file} - writes active file to the current directory  
(though i just learned you could also :!touch)

:{start line number},{end line number} w {filename}  
- writes to active file just the content between the specified lines

### Insert the contents of a file
:r {filename} - places the contents of a file under the current cursor location

### The open command
o - open a line below the cursor and enable insert mode  
O - open a line above the cursor and enable insert mode

### Replacing more than one character
R - allows you to type over existing text starting from the cursor posititon.  
Press ESC when finished.

### Faster insert at the end of the line
A - moves to the end of the line and enables insert mode (NICE!)

## Day 5

Add a layer:  
dotspacemacs-configuration-layers - add your layer here in the .spacemacs file

### Modifying Spacemacs Configuration
SPC f e d - edit the config  
SPC f e R - reload spacemacs to pickup the change (remember to save!)

### Window Management
SPC w S - split horizontal and focus  
SPC w V - split vertical and focus

### Moving around the screen
ctrl u - move halfway up the screen  
ctrl d - move halfway down the screen

### When Melpa is down
You can use a mirror https://github.com/melpa/melpa/blob/master/README.md#mirrors

#### How to add a mirror url
go to your emacs.d directory and open the init.el file  
Add this to the file (I added it to the bottom):  
```(add-to-list
  'package-archives
   ;; '("melpa" . "http://stable.melpa.org/packages/") ; reset back to this when Melpa is up
  '("melpa" . "http://www.mirrorservice.org/sites/stable.melpa.org/packages/")
t)```

### Install a layer
Find the dotspacemacs-configuration-layer section of the .spacemacs config  
Paste in the name of the layer you want to install.   
You will see a whole bunch of commented out packages.

### Copy to the clipboard
We need to install the osx layer first, then we can do "*y to yank to the * register and copy to the system clipboard.  
You can use :reg to see the contents of registers, it's kinda weird and cool.   
I was expecting to see my copied text in there but it's not showing, that's a bit strange!  
It does copy it though and allow me to paste into my Mac applications.

### Ruby
Spacemacs helpfully installed the Ruby layer for me when I opened a Ruby file, neat.  
It auto completes the end keyword for me and highlights matching do / ends, so nice.

### RSpec
With the ruby layer we can run RSpec from inside Spacemacs.  
By default, ruby-test-mode is set to ruby-test, we need to alter this to be rspec in the config file:  
In dotspacemacs-configuration-layer, change ruby to (ruby :variables ruby-test-runner 'rspec)  
The brackets are important, it won't work if you forget them.

SPC m t a - run all specs  
SPC m t b - run the current spec file  
SPC m t r - rerun last spec  
SPC m t t - run spec at pointer  

### Swap Characters
xp - swap the character under the cursor with the next  
Xp - swap the current character with the previous

### Tree view
R - mark directory as the root directory  
K - go up to parent  
SPC p t - open tree view with root directory view  
c - create a node (look for the prompt that appears in the command strip at the bottom)  
d - delete a node  
r - rename a node  
gr - refresh tree  
