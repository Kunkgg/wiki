# tr

Character is used for the unit of `tr`.

Replace charset1 with charset2, *character by character*

```sh
tr [options] set1 [set2]
```


## Options

* `-d`, remove all characters in set1
* `-s`, remove repetitive characters in set1
* `-c`, --complement the set1

## Character classes

A useful function of `tr` is the ability of using character classes.

character classes:

* `"[:lower:]"`
* `"[:upper:]"`
* `"[:digit:]"`
