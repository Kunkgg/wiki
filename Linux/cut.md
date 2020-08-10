# cut

## By character range

```sh
cut -c -5,8-12,14- filename
```

## By delimiter and field number

```sh
cut -f -2,5,6- -d';' filename
```

## Invert selection (complement)

```sh
cut --complement -f 5 -d':' filename
```

## Specify output-delimiter

```sh
cut -f 2,5 -d' ' --output-delimiter='*' filename
```

