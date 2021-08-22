# NOUS - The ultimate keyboard
Nor(wegian|dic) + United States. Made with scandinavian keyboards in mind. Uses both Shift and AltGr to switch keys.

# Installation
```sh
# cp nous /usr/share/X11/xkb/symbols
$ setxkbmap nous
```
For a permanent setup:
```sh
#/etc/X11/xorg.conf.d/00-keyboard.conf
Section "InputClass"
        Identifier "system-keyboard"
        MatchIsKeyboard "on"
        Option "XkbLayout" "nous"
        Option "XkbModel" "pc102"
	Option "XkbOptions" "altwin:swap_lalt_lwin"
EndSection
```

# How to use with fcitx
Sort of unrelated but in case you also have trouble. I added a new input method. I searched for "nous" and selected "Keyboard - English (US)". I think it's conincidental it shows up. Move it to the top of the list, then Addons -> (Advanced) -> X Keyboard Integration -> (Configure) -> (Untick) Allow to Override System XKB Settings. Then restart and AltGr combos should now work, even with Japanese or whatever you may use! This also prevents fcitx from screwing up my capslock, escape and tab rebinds.

# Preview
![preview](preview.png)
As you can see it also has some mathematical symbols, too.\
NOTE: AltGr+5 gives ‰ (per mille / promille), it is shortened to ... in the image.

# TODO
* Shift+AltGr+FX → 1/2 etc
* More mathematical symbols like R and Q
* Utilize the key between Shift and Z (but for what?)
* Swap ESC and CapsLock
* Utilize key between FN and Ctrl for something other than "right clicking"
