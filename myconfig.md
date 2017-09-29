# Custom config
## .spacemacs

### Font
dotspacemacs-default-font '("Fira Code"...)

### Copy paste bug
user-config
(fset 'evil-visual-update-x-selection 'ignore)

### Mouse wheel
(unless window-system
    (global-set-key (kbd "<mouse-4>") 'scroll-down-line)
    (global-set-key (kbd "<mouse-5>") 'scroll-up-line))

## .emacs.d/init.el
(add-to-list
  'package-archives
   ;; '("melpa" . "http://stable.melpa.org/packages/") ; reset back to this when Melpa is up
  '("melpa" . "http://www.mirrorservice.org/sites/stable.melpa.org/packages/")
t)
