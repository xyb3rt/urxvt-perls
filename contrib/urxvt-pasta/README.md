Paste clipboard content using the default urxvt libs. Handles the X11 clipboard too.
The default **selection-to-clipboard** lib will put the selected content into the buffer automatically, no need to bind any key.

# Installation
------------

Simply place the script in **/usr/lib/urxvt/perl/** for
system-wide availability or in **~/.urxvt/ext/** for user-only availability.
You can also put it in a folder of your choice, but then you have to add this
line to your **.Xdefaults/.Xresources**:

```bash
# Don't type ~ or $HOME below
URxvt.perl-lib: /home/user/your/folder/
```

After installing, put the following lines in your **.Xdefaults/.Xresources**:

```bash
# libs to activate, do not omit selection-to-clipboard
URxvt.perl-ext-common           : selection-to-clipboard,pasta

# keyboard shortcut to trigger the lib
URxvt.keysym.Control-Shift-V    : perl:pasta:paste
```

# Requirements

* At least rxvt-unicode version 9.20
