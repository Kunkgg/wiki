# sponge

soak up standard input and write to a file.

`sponge` reads standard input and writes it out to the specified file.
Ulinke a shell redirect, `sponge` soaks up all its input before writing the output file.
This allow **constructing pipelines that read from and write to the same file.**

## Install

```sh
sudo pacman -S moreutils
```

## Options

* `-a`, append

## Example

```sh
find . -name '*.cpp' -type f -exec bash -c 'expand -t 4 "$0" | sponge "$0"' {} \;
```
