# thinkpad-guides
ThinkPad laptop how-tos with GNU/Linux.
This guide has been produced with a Thinkpad (Lenovo) X200 laptop from Gluglug running Trisquel.

## Brightness Controls

### Bash Command
The commands that will control the brightness from the terminal.

#### Brightness Up

```xbacklight -inc 10```

#### Brightness Down
```xbacklight -dec 10```

### Find the keycodes that correspond to the keys

#### Brightness Up
FN-Home

KeyCode: 233

```XF86MonBrightness```

#### Brightness Down
FN-End

KeyCode: 232

```XF86MonBrightnessDown```

### Connect the keymappings up

http://littlesvr.ca/linux-stuff/articles/xbindkeys/xbindkeys.php

#### Make the user override file for the keybindings
```xbindkeys -d > ~/.xbindkeysrc```

#### Open the keybindings override file
```nano ~/.xbindkeysrc```

#### Add the following to the file

```
"xbacklight -dec 10"
  XF86MonBrightnessDown

"xbacklight -inc 10"
  XF86MonBrightnessUp
```

##### This acts oddly and seems to trigger a lot more than neccessary
```
"xbacklight -dec 10"
  c:232

"xbacklight -inc 10"
  c:233
  ```

### Make the settings take effect

#### Reboot the laptop

```shutdown -r now```
