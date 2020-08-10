# xmodmap

## Concepts

keycode

:   the numeric representation received by the kernal when a key or a mouse
button is pressed.

keysym

:   the value assigned to the keycode.
    For example, pressing `a` generates the `keycode 38`,
    which is mapped to the `keysym 0x61`,
    which matches `a` in [ASCII table].
    The keysyms are managed by [Xorg] in a table of keycodes defining the
    keycode-keysym relations,
    which is called the **keymap table**.
    This can be shown by running `xmodmap`.

## Install

*   [xorg-xmodmap]
*   [xkeycaps] GUI

## Keymap table

```sh
xmodmap -pke
...
keycode  35 = bracketright braceright bracketright braceright
keycode  36 = Return NoSymbol Return
keycode  37 = Control_L NoSymbol Control_L
keycode  38 = a A a A
keycode  39 = s S s S
keycode  40 = d D d D
keycode  41 = f F f F
...
```

## Reference

[Arch Linux Wiki: xmodmap](https://wiki.archlinux.org/index.php/Xmodmap)
[Fix terminal](http://www.leonerd.org.uk/hacks/fixterms/)

[ASCII table]: https://en.wikipedia.org/wiki/ASCII
[Xorg]: https://wiki.archlinux.org/index.php/Xorg
[xorg-xmodmap]: https://www.archlinux.org/packages/?name=xorg-xmodmap
[xkeycaps]: https://www.archlinux.org/packages/?name=xkeycaps
