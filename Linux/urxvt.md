
# urxvt

### Output URxvt Resources

```sh
urxvt --help 2>&1| sed -n '/:  /s/^ */! URxvt*/gp'
```

### URxvt Resources with descriptions

```sh
man -Pcat urxvt | sed -n '/th: b/,/^B/p'|sed '$d'|sed '/^ \{7\}[a-z]/s/^ */^/g' | sed -e :a -e 'N;s/\n/@@/g;ta;P;D' | sed 's,\^\([^@]\+\)@*[\t ]*\([^\^]\+\),! \2\n! URxvt*\1\n\n,g' | sed 's,@@\(  \+\),\n\1,g' | sed 's,@*$,,g' | sed '/^[^!]/d' | tr -d "'\`"
```
