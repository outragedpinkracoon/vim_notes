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

ctrl u - move halfway up the screen  
ctrl d - move halfway down the screen

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

## Copy to the clipboard
We need to install the osx layer (see installing layers) first, then we can do "*y to yank to the * register and copy to the system clipboard.

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

## Indent
>> - indent once
<< - unindent once

## Commenting
With evil-commentary layer
gcc - comment or uncomment a line, prefix with number to repeat

## Change Case
Select a region in visual block mode
u - lowercase
U - uppercase

## Swap Characters
With the ruby-on-rails layer
:A

## Swap between source and spec file
xp - swap the character under the cursor with the next  
Xp - swap the current character with the previous


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

cW - change word up to the next space
ct[character] - change up to (not including) the next instance of the specified character

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
SPC w V - split vertical and focus

SPC w s - split horizontally  
SPC w S - split horizontal and focus  

SPC w l - move to window on the right  
SPC w h - move to window on the left

## Toggle Line Numbers
SPC t n

## Tree view
SPC f t - open tree view at the current file level  
SPC p t - open tree view with root directory view

The tree view is clickable, and can be focused and unfocused using normal window commands.  
It is traversed using hjkl or the arrow keys as normal. Hitting enter will expand a folder.


R - mark directory as the root directory  
K - go up to parent  
| - opens up selected node in a new vertical frame

c - create a node (look for the prompt that appears in the command strip at the bottom)  
d - delete a node  
r - rename a node  

## Modifying Spacemacs Configuration
SPC f e d - edit the config  
SPC f e R - reload spacemacs to pickup the change (remember to save!)

## When Melpa package repository is down
You can use a mirror https://github.com/melpa/melpa/blob/master/README.md#mirrors

### How to add a mirror url
go to your emacs.d directory and open the init.el file  
Add this to the file (I added it to the bottom):  

```(add-to-list
  'package-archives
   ;; '("melpa" . "http://stable.melpa.org/packages/") ; reset back to this when Melpa is up
  '("melpa" . "http://www.mirrorservice.org/sites/stable.melpa.org/packages/")
t)
```

## Install a layer
Find the dotspacemacs-configuration-layer section of the .spacemacs config  
Paste in the name of the layer you want to install.   
You will see a whole bunch of commented out packages.

## Ruby
Spacemacs helpfully installed the Ruby layer for me when I opened a Ruby file, neat.  
Otherwise add the ruby layer to your .spacemacs file.

### RSpec
With the ruby layer we can run RSpec from inside Spacemacs.  
By default, ruby-test-mode seems to be set to ruby-test, rather than rspec.  
We can use a .dir-locals.el file to specify different test runners per project,  
but let's keep it simple for now and just add it to .spacemacs.

The previous 'ruby' layer in the dotspacemacs-configuration-layers section becomes:

```
(ruby :variables
           ruby-test-runner 'rspec
           ruby-enable-enh-ruby-mode t)
```

NOTE: We need to install the gem 'spring-commands-rspec' to get this to work inside of Spacemacs.  
If you don't have it, you will see info about the usage of Spring rather than your test output.

SPC m t a - run all specs  
SPC m t b - run the current spec file  
SPC m t r - rerun last spec  
SPC m t l - run last failed spec  
SPC m t t - run spec at pointer  

[Docs here](https://github.com/syl20bnr/spacemacs/tree/master/layers/%2Blang/ruby#rspec-mode)

### Rubocop
SPC m r r f - run on the current file  
SPC m r r p - run on the entire project

To show Rubocop errors on the screen, uncomment the syntax-checking layer in .spacemacs.
