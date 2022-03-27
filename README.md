# What is this?

This is a collection of reasonably well thought out notes on xkb geometry (in no particular format).
I'm calling it documentation because it's probably the best there is on the topic.

Xkb geometry is very powerful, but I haven't found any good documentation anywhere (I've searched hard, but please let me know if I didn't search hard enough).
I want to change that.

This is for anyone else who has decided to ignore [this](https://wiki.archlinux.org/title/X_keyboard_extension#xkb_geometry), but has otherwise followed that page or something similar.

# List of geometry files, to use as templates/examples

- https://gitlab.freedesktop.org/xkeyboard-config/xkeyboard-config (look in the geometry folder). Probably already in /usr/share/X11/xkb/ on your computer.
The default is the 105 key version in geometry/pc, but the other files have more complicated layouts.

- [My Dell Latitude E6420 layout](examples/geometry.xkb)

Random repos I found after a bit of searching:

- https://github.com/pfaion/x1carbon-xkb-geometry

- https://github.com/ZeptByteS/xkb_geometry_microsoft_4000

Please let me know if you find more.
I think it would be good to have a collection of keyboard geometry configuration files.


# Useful resources

- https://www.x.org/releases/X11R7.7/doc/kbproto/xkbproto.html#Keyboard_Geometry Great description of xkb geometry, but doesn't translate it into configuration files.

- https://web.archive.org/web/20190205191552/http://pascal.tsu.ru/en/xkb/ Best documentation on xkb configuration I've found. It also happens to be an archived english translation of documentation hosted on a Russian university(?)'s website. I hope that illustrates the state of xkb configuration documentation. Nothing on geometry.

- https://wiki.archlinux.org/title/X_keyboard_extension Good documentation on normal keyboard configuration. Nothing on geometry.

Other sources:

- Random places and testing

- https://gitlab.freedesktop.org/xorg/app/xkbcomp

- https://gitlab.freedesktop.org/xorg/app/xkbprint

- Experience from creating https://github.com/Albert-S-Briscoe/xkbprint-kle
