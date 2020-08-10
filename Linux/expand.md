# expand

converts tabs to spaces

## Usages

* Default, converts each tab to 8 spaces.
* `-t N` converts each tab to N spaces.
* `-i` convert the tabs at the start of lines only.

## Example

```sh
expand -t -i tab_file | sponge tab_file

find . -name '*.py' -type f -exec bash -c 'expand -t 4 "$0" | sponge "$0"' {} \;
```

