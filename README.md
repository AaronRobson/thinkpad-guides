# thinkpad-guides
ThinkPad laptop how-tos with GNU/Linux.
This guide has been produced with a Thinkpad (Lenovo) X200 laptop from Gluglug running Trisquel.
Various settings of the laptop may not be set up properly when you first install the Operating System or upgrade to a new LTS (Long Term Support) version.

## Assumptions
1. You are running Trisquel or another Debian based distro that uses the X11 Windowing System.
2. You know how to get to the terminal in the GUI ```Ctrl-Alt-T```
3. You know how to install new programs from the terminal e.g. ```sudo apt-get install program_name```

### Brightness Controls

#### Bash Command
The commands that will control the brightness from the terminal.

##### Brightness Up
```xbacklight -inc 10```

##### Brightness Down
```xbacklight -dec 10```

#### Find the keycodes that correspond to the keys

1. Run ```xev``` from the terminal.
2. Click the keys in the little GUI window that pops up.
3. The terminal output will tell you the keycodes and names.

##### Brightness Up
FN-Home

KeyCode: 233

```XF86MonBrightnessUp```

##### Brightness Down
FN-End

KeyCode: 232

```XF86MonBrightnessDown```

#### Connect the keymappings up

http://littlesvr.ca/linux-stuff/articles/xbindkeys/xbindkeys.php

##### Make the user override file for the keybindings
```xbindkeys -d > ~/.xbindkeysrc```

##### Open the keybindings override file
```nano ~/.xbindkeysrc```

##### Add the following to the file

```
"xbacklight -inc 10"
  XF86MonBrightnessUp

"xbacklight -dec 10"
  XF86MonBrightnessDown
```

###### This acts oddly and seems to trigger a lot more than neccessary
```
"xbacklight -inc 10"
  c:233

"xbacklight -dec 10"
  c:232
  ```

####
Save ```Ctrl-O``` (output) and Exit ```Ctrl-X```

### Volume adjustment

## Volume Up
KeyCode 123

``XF86AudioRaiseVolume```

## Volume Down
KeyCode 122

```XF86AudioLowerVolume```

## Mute
Could not be discovered by ```xev```.

#### Make the settings take effect

#### Reboot the laptop

```shutdown -r now```
