dwm - dynamic window manager
============================
dwm is an extremely fast, small, and dynamic window manager for X. This is a maintained implementation of dwm with sensible, sane defaults and pre-installed patches for drop-in usage.


Requirements
------------
In order to build dwm you need the Xlib header files.

Installation
------------
Edit config.mk to match your local setup (dwm is installed into
the /usr/local namespace by default).

Afterwards enter the following command to build and install dwm (if
necessary as root):

    make clean install


Running dwm
-----------
Add the following line to your .xinitrc to start dwm using startx:

    exec dwm

In order to connect dwm to a specific display, make sure that
the DISPLAY environment variable is set correctly, e.g.:

    DISPLAY=foo.bar:1 exec dwm

(This will start dwm on display :1 of the host foo.bar.)

In order to display status info in the bar, you can do something
like this in your .xinitrc:

    while xsetroot -name "`date` `uptime | sed 's/.*,//'`"
    do
    	sleep 1
    done &
    exec dwm


Configuration
-------------
The configuration of dwm is done by modifying the custom config.h
and (re)compiling the source code. If config.h is not found, one will
be generated from config.def.h.

A default config.h is provided with sensible default bindings and settings:

| Keybind | Action |
| -------------- | --------------- |
| `SUPER+(1-9)` | Switch tag |
| `SUPER+R` | dmenu |
| `SUPER+R_Shift` | st |
| `SUPER+C` | Close active window |
| `SUPER+B` | Toggle status bar |
| `SUPER+J` | Focus prev |
| `SUPER+K` | Focus next |
| `SUPER+H` | Decrement master stack size |
| `SUPER+L` | Increment master stack size |
| `SUPER+RETURN` | Zoom (move focused window to master stack) |
| `SUPER+L_SHIFT+Q` | Exit dwm |


### Misc. Changes

`incmaster` binds commented out to prevent accidental increasing or decreasing of master windows.

`resizehints` has been disabled so that dwm will have full control over application window resizing (`st` notably resizes its own window to fit the TTY's cols and rows; disabling this settings prevents the gaps from appearing).

`borderpx` has been increased to 2px (cosmetic only).

### Patches

A list of pre-applied patches can be found in the `patches/` directory.
