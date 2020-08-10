
# VimScript

## Why should noremap?

    if use(map):
        Bad!
        It finds key mappings recursively. Cause mess.
        Never use it, as possible as.
    if use(noremap):
        Good!
        Disable the recursive find.

## map-local, options-local

Local map and options may cause mess.

If use map-local(`<buffer>`) with autocmd, I could't chang the map until clear

    if use(autocmd FileType vimrc map <buffer> ... ...):
       The map will work in specify buffer(file), not file type.
       If I will change the map setting in vimrc,
       it not work in files which have been mapped same shortcut in buffer.
       To fix this mess, I have to unmap.

## Operator-Pending mappings

Operator-Pending mappings are used for selecting the operating objects text.
There are many default Operator-Pending mappings. Such as `ib`, `ab`, `i(`,
`a(`, `i{`, `a{`, `iB`, `aB`, and so on.

    onnoremap <keys> <script>

Note: the script should end at `visual-mode`.

## Loose data type

VimScript is a dynamic language. It includes two basic data types, `Number`
and `String`.

While execute operators with different data types, VimScipt will cast data type
automaticly.

*   Strings which start with number, cast the string to the number at beginning.
*   Strings which start with non-number, cast the string to the number 0.

For examples:

```
echom 10 + "test"
# result is: 10

echom "2ahah" + "3yoyo"
# result is: 5

echom "number" + "Ten100"
# result is: 0
```

## single quote and double qoute

literal-string

:   To avoid backslashes in the regexp pattern to be douled,
    use a single-quote string. These two commands are equivalent:

    ```
    if a =~ "\\s"
    if a =~ '\s'
    ```

## Variable scoping

## function

**Vimscript functions must start with a capital letter if they are unscoped!**

## function arguments

Vimscipt function that takes arguments always need to prefix those arguments
with `a:`. It tell Vim that they are in the argument scope.

Varags

:   take variable-length argument lists like Javascript and Python.

    *   `a:0` is the length of argument list
    *   `a:1` is the first element of argument list
    *   `a:2` is the second element of argument list
    *   `a:000` is the argument list

```
function Varg2(foo, ...)
  echom a:foo
  echom a:0
  echom a:1
  echo a:000
endfunction

call Varg2("a", "b", "c")

# result:
# a
# 2
# b
# ['b', 'c']

```

## Comparsions case sensitive

`expr-==` and `expr-!=` are whether comparsions case-sensitive is decided
by user's setting.

`ignorecase` or `noignorecase`.

It's terrible!

`expr-==#` is recommanded, it is always case-sensitive.

## `echo` and `echom`

echo

:   echo some message.

echom

:   echo message to Vim message history. The distinct with `echo` is.

    1.  record message in Vim message history.
    2.  doesn't parse the spical characters. like `\n`, `\r`, `\t` and so on.

## `normal` and `normal!`

`normal!` don't parse command recursively. This is the recommended way.

## `grep` and `grep!`

`grep` will navigate to the frist search result.

`grep!` let cursor stay in current position.

## `silent` and `silent!`

## Regexp very-magic

Vim regexp has four styles regexp. Always use the very-magic style can avoid
unnecessary messes.

    /\v<[a-zA-Z0-9_\.%+-]{-1,}\@[a-zA-Z\.-]{-1,}\.\a{2,6}>

## Operator function

## `gn` and `gN`

select the current regexp search result.

*   `gn` cursor at the end
*   `gN` cursor at the beginning

## list in vimscript

    testlist = ['a', 'b', 'c', 'd']
    if (in vimscripte):
        testlist[0:2] = ['a', 'b', 'c']
    if (in python):
        testlist[0:2] = ['a', 'b']

## `path` and `runtimepath`

`runtimepath` is used for looking for files to load while vim start-up.

`path` is used for search files to edit.

## Very useful help

*   magic
*   runtimepath
*   group-name
*   usr\_28 folding

## See also

*   [vimscript function cheatsheets](https://devhints.io/vimscript-functions)
