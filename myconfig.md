# Custom config

## Font
dotspacemacs-default-font '("Fira Code"...)

## Copy paste bug
user-config
(fset 'evil-visual-update-x-selection 'ignore)

## Mouse wheel
(unless window-system
    (global-set-key (kbd "<mouse-4>") 'scroll-down-line)
    (global-set-key (kbd "<mouse-5>") 'scroll-up-line))
