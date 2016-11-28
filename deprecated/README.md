Deprecated perl extensions for the rxvt-unicode terminal emulator.

See the file README.md in the parent directory for installation instructions,
in case you still want to use them.


url-select
----------
Use keyboard shortcuts to select URLs.

**DEPRECATED**

Since version 9.21 the *matcher* extension shipped with rxvt-unicode fully
replaces this extension. The `url-select:select_next` action is provided by the
`matcher:select` action. However, the *matcher* extension does not provide
vi-like key bindings; it only uses the arrow and home/end keys.

This should be used as a replacement for the default matcher extension, it also
makes URLs clickable with the middle mouse button.

After installing, put the following lines in your .Xdefaults/.Xresources:

    URxvt.perl-ext-common: ...,url-select
    URxvt.keysym.M-u: perl:url-select:select_next

Use Meta-u to activate URL selection mode, then use the following keys:

    j/k:      Select next downward/upward URL (also with arrow keys)
    g/G:      Select first/last URL (also with home/end key)
    o/Return: Open selected URL in browser, Return: deactivate afterwards
    y:        Copy (yank) selected URL and deactivate selection mode
    q/Escape: Deactivate URL selection mode

Options:

    URxvt.url-select.autocopy:  if set to true, selected URLs are automatically
                                copied to the PRIMARY buffer
    URxvt.url-select.button:    mouse button to click-open URLs (default: 2)
    URxvt.url-select.launcher:  browser/command to open selected URL with
    URxvt.url-select.underline: if set to true, all URLs get underlined

For compatibility reasons, url-select will also use any patterns defined for
the matcher extension by reading all `URxvt.matcher.pattern.[0-9]` resources.


clipboard
---------

**DEPRECATED**

Since version 9.20 rxvt-unicode natively supports copying to and pasting from
the CLIPBOARD buffer with the `Ctrl-Meta-c` and `Ctrl-Meta-v` key bindings. The
`clipboard.autocopy` setting is provided by the `selection_to_clipboard`
extension shipped with rxvt-unicode.

Use keyboard shortcuts to copy the selection to the clipboard and to paste the
clipboard contents (optionally escaping all special characters).

After installing, put the following lines in your .Xdefaults/.Xresources:

    URxvt.perl-ext-common: ...,clipboard
    URxvt.keysym.M-c:   perl:clipboard:copy
    URxvt.keysym.M-v:   perl:clipboard:paste
    URxvt.keysym.M-C-v: perl:clipboard:paste_escaped

Options:

    URxvt.clipboard.autocopy: if set to true, the clipboard is automatically
                              updated whenever the PRIMARY selection changes

You can also overwrite the system commands to use for copying/pasting.
The default ones are:

    URxvt.clipboard.copycmd:  xsel -ib
    URxvt.clipboard.pastecmd: xsel -ob

If you prefer xclip, then put these lines in your .Xdefaults/.Xresources:

    URxvt.clipboard.copycmd:  xclip -i -selection clipboard
    URxvt.clipboard.pastecmd: xclip -o -selection clipboard

On Mac OS X, put these lines in your .Xdefaults/.Xresources:

    URxvt.clipboard.copycmd:  pbcopy
    URxvt.clipboard.pastecmd: pbpaste

The use of the functions should be self-explanatory!
