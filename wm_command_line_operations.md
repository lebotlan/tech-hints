# Operations on windows (move, toggle fullscreen, resize, ...) from the command-line.

This was tested on GNOME Flashback + Metacity. Probably works on other window-managers.

## Install wmctrl

## Usage
'wmctrl -l    # list windows'

Toggle fullscreen
'wmctrl -r "xpdf" -b "toggle,fullscreen"'

* Note : xpdf should be toggled using ALT+F, for it also removes windows decorations, buttons, etc.
* ALT+F => -decoration ++ toggle fullscreen

## Move window

* The first number is gravity. Keep 0.
* (gr,x,y,w,h)
* -1 means unchanged
* When in fullscreen mode, you may move from one monitor to another quite easily. When I tested, the coordinates seems to be rounded to the closest monitor (very handy).
'wmctrl -r xpdf -e "0,800,0,-1,-1"'



