# Spacemacs Cheatsheet
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
