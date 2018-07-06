# thinkpad-guides
If you've just installed or updated a Linux distribution on your ThinkPad you may be wondering why some of the function keys don't work.
If so this guide is for you.
Read on to discover how to get those brightness controls working again.

This guide has been produced with a Lenovo ThinkPad X200 laptop from the company Gluglug.
I have it running the Trisquel distribution as its operating system.
This operating system provides the graphical windows using the X11 Windowing System which is why many of the commands we see later start with an `x`.

## Prerequisites
The terminal is where we will spend most of this guide.
You can get to the terminal by pressing `Ctrl-Alt-T`.
From within the terminal you can enter textual commands and have them run by pressing the `Enter` or `Return` key.
An example of a command is `ls` which will print on the screen the files and folders in the folder you are in.

In the rest of this document you may come across a command for a program that you don't have installed on your computer.
If for example say the `xbacklight` command when run says `xbacklight: command not found` then we'll need to get it installed.
Enter the following command to ask to install it `sudo apt-get install xbacklight` the `sudo` means to 'elevate' the running of the rest of the command as the superuser (aka administrator or root user), this means that you get rights and abilities you don't ordinarily have.
Ordinary user accounts don't normally have these extra rights for security reasons.
If your user isn't allowed to gain such rights using `sudo` then you can either get yourself added to the sudo group, login as the `root` account or using the command `su` elevate all commands afterwards in that terminal window, in such cases you will need the root password if such an account exists or help from the IT support person who set it up.
You will probably be asked to enter your password to continue.
It may also ask if you are happy to use disk space to do so, please confirm by entering `y` for yes or `n` for no depending on the question.

### Brightness Controls

#### Bash Command
The commands that will control the brightness from the terminal.

##### Brightness Up
```xbacklight -inc 10```

##### Brightness Down
```xbacklight -dec 10```

#### Find the keycodes that correspond to the keys

1. Run ```xev``` from the terminal.
2. Click the keys in the little "Event Tester" window that pops up.
3. The terminal output will tell you the keycodes and names.
4. Close the little "Event Tester" window to return to the terminal.

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

##### Add the following to the file (including quotes)

```
"xbacklight -inc 10"
  XF86MonBrightnessUp

"xbacklight -dec 10"
  XF86MonBrightnessDown
```

##### Alternatively
In my experience using the following meant that the buttons made the screen brightness flicker at random.
From checking `xev` it seems that it triggers a lot more than neccessary. However your system may differ.
```
"xbacklight -inc 10"
  c:233

"xbacklight -dec 10"
  c:232
```

#### Save
```Ctrl-O``` (output) and Exit ```Ctrl-X```

### Volume adjustment

#### Volume Up
KeyCode 123

```XF86AudioRaiseVolume```

#### Volume Down
KeyCode 122

```XF86AudioLowerVolume```

#### Mute
Could not be discovered by ```xev```.

### Make the settings take effect

#### Reboot the laptop

```shutdown -r now```
