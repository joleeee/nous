# <img src="logo.png" height="22" /> NOUS - The ultimate keyboard 

- [ NOUS - The ultimate keyboard](#-nous---the-ultimate-keyboard)
- [Preview](#preview)
- [Linux and OpenBSD](#linux-and-openbsd)
  - [Installation](#installation)
  - [Arch package](#arch-package)
  - [How to use with fcitx](#how-to-use-with-fcitx)
  - [Switching keys in tty](#switching-keys-in-tty)
- [MacOS](#macos)
  - [Installation](#installation-1)
  - [Other tips](#other-tips)

Nordic + United States. Made with scandinavian keyboards in mind. Uses both Shift and AltGr to shift keys.
# Preview
![preview](preview.png)

Slightly outdated

# Linux and OpenBSD
## Installation
```sh
# cp nous /usr/share/X11/xkb/symbols
$ setxkbmap nous
```
For a permanent setup:
```sh
# linux:   /etc/X11/xorg.conf.d/00-keyboard.conf
# openbsd: /usr/X11R6/share/X11/xorg.conf.d/00-keyboard.conf
Section "InputClass"
    Identifier "system-keyboard"
    MatchIsKeyboard "on"
    Option "XkbLayout" "nous"
    Option "XkbModel" "pc102"
    # optional
    Option "XkbOptions" "altwin:swap_lalt_lwin"
EndSection
```

## Arch package
You can build it yourself by running `makepkg -i` in that repo. `nous` is for the layout file, `switchlayout` is for the tty layout as described below.

## How to use with fcitx
Sort of unrelated but in case you also have trouble. I added a new input method. I searched for "nous" and selected "Keyboard - English (US)". I think it's conincidental it shows up. Move it to the top of the list, then Addons -> (Advanced) -> X Keyboard Integration -> (Configure) -> (Untick) Allow to Override System XKB Settings. Then restart and AltGr combos should now work, even with Japanese or whatever you may use! This also prevents fcitx from screwing up my capslock, escape and tab rebinds.

## Switching keys in tty
The `switch.map` can be used to switch tab with escape and control with capslock. It does *not* implement the rest of nous. It was edited from `/usr/share/keymaps/xkb/us.map.gz` on an alpine system. `kbd` is a requirement. Apparently keycodes can vary by system. If it doesn't work make your own by using `showkey` to find the codes. Install: `gzip -k switch.map && cp switch.map.gz /usr/share/keymaps/xkb/ && loadkeys switch`. Load automatically on login:
```sh
# .profile
loadkeys switch
```


# MacOS
The MacOS layout currently does not exactly correspond to the linux layout wrt. to all special symbols. It does however map `æøå` to `option`, in the same way `altgr`/`right alt` is used on linux.


## Installation
1.  move `nous.bundle` into Documents.
2.  use Ukulele's `File > Install > Show Organizer` to install
3. sign out and log back in
4. select `nous` from the top bar

![MacOS toolbar](macos-toolbar.png)

## Other tips
![MacOS layout](macos.png)

I'd also recommend [Karabiner-Elements](https://karabiner-elements.pqrs.org/) for swapping the right cmd and option for easier layer switching.

![Karabin remap](karabin.png)

