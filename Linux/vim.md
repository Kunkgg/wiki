# Vim

## Interest things

*   c\_mode `:jumps`
*   c\_mode `:changes`
*   c\_mode `:marks`
*   c\_mode `:e!`, drop all changes hasn\'t saved
*   c\_mode `:e $VIMRUNTIME`
*   c\_mode `:scriptnames`
*   c\_mode `:verbos imap <tab>`
*   c\_mode `q:`

## Navigation

### Jumps

The following commands are \" jump \" commands: \" \' \", \" G \",
\" \/ \", \" \? \", \" n \", \" N \", \" \% \", \" \( \", \" \) \",
\" \[\[ \", \" \]\] \", \" { \", \" } \", \" :s \", \" :tag \", \" L \",
\" M \", \" H \" and the commands that start editing a new file.

   c\_mode `:jumps`, print jump list
*   `CTRL-o`, go older jump position
*   `CTRL-i`, go newer jump position

### Repeat inline search

Repeat `f`, `F`, `t`, `T`:

*   `;` forward
*   `,` backward

### Go through the change list

*   c\_mode `:changes`, print change list
*   n\_mode `g;`, go older position in change list
*   n\_mode `g,`, go newer position in change list

### Marks

*   c\_mode `:marks`, print mark list
*   n\_mode \`\` , go to last jump from position
*   n\_mode \`\[ , go to the start of last yank
*   n\_mode \`\] , go to the end of last yank
*   n\_mode \`\< , go to the start of last visual-mode selected
*   n\_mode \`\> , go to the end of last visual-mode selected

### Various motions

*   n\_mode `%`, find next item in this line after or
    under the cursor and jump to its match.
*   n\_mode `]m`, go to the start of next method

## Indent

### General settings

    set shiftwidth=4     " number of *actual* spaces per TAB
    set shiftwidth=4     " number of *actual* spaces per TAB
    set tabstop=4        " number of *visual* spaces per TAB
    set softtabstop=4    " number of spaces in tab when *editing*
    set expandtab        " tabs are spaces

### Indent for filetype

    autocmd Filetype markdown setlocal expandtab \
    tabstop=2 shiftwidth=2 softtabstop=2

### Listchars

    listchars+=tab:→\ ,eol:↲

Display listchars by `:set list`

### Auto-indent

Select contents in visual mode, then press `=`

## Buffer

### Concept

Summary

:   A buffer is the in-memory text of a file.
:   A window is a viewport on a buffer.
:   A tab page is a collection of windows.

A window is a viewport onto a buffer.
You can use multiple windows on one buffer,
or several windows on different buffers.

A buffer is a file loaded into memory for editing.
The original file remains unchanged until you
write the buffer to the file.

A buffer can be in one of three states:

:   active
:   hidden
:   inactive

### Basic usages

*   c\_mode `:ls` or `:buffers`, List buffers.
*   c\_mode `:hide`, Hide Current buffer.
*   c\_mode `:bp`, Go to previous buffer.
*   c\_mode `:bn`, Go to next buffer.
*   c\_mode `:bN`, Go to the _Nth_ buffer.
*   c\_mode `:sb{n,p,N}`, Switch buffer with split window.

## Split window

### Basic Usages

*   c\_mode `:sp`, split windows from up to down, split line is horizontal.
*   c\_mode `:vsp`, split windows from left to right, split line is vertical.
*   n\_mode `CTRL-w`, enter windows commands mode.
    *   n\_mode `"CTRL-w s"`, equal to c\_mode `:sp`.
    *   n\_mode `"CTRL-w v"`, equal to c\_mode `:vsp`.
    *   n\_mode `"CTRL-w h"`, turn to the left window.
    *   n\_mode `"CTRL-w j"`, turn to the down window.
    *   n\_mode `"CTRL-w k"`, turn to the up window.
    *   n\_mode `"CTRL-w l"`, turn to the right window.
    *   n\_mode `"CTRL-w w"`, turn to next window, loop.
    *   n\_mode `"CTRL-w p"`, turn to previous focused window.
    *   n\_mode `"CTRL-w q"`, close window.
    *   n\_mode `"CTRL-w x"`, switch windows in horizontal.
    *   n\_mode `"CTRL-w r"`, switch windows in vertical.
    *   n\_mode `"CTRL-w +"`, scale bigger windows in vertical.
    *   n\_mode `"CTRL-w -"`, scale smaller windows in vertical.
    *   n\_mode `"CTRL-w >"`, scale bigger windows in horizontal.
    *   n\_mode `"CTRL-w <"`, scale smaller windows in horizontal.
    *   n\_mode `"CTRL-w _"`, max windows in vertical.
    *   n\_mode `"CTRL-w |"`, max windows in horizontal.
    *   n\_mode `"CTRL-w ="`, every window resize as same.
    *   n\_mode `"CTRL-w o"`, only display current window.
*   c\_mode `:ba`, display all buffers in split windows,
    opposited to only display current window.
*   c\_mode `:resize` and `:vertical resize`, resize windows.

## Tab

### Basic Usages

*   c\_mode `:tabe`, edit something in a new tab.
*   c\_mode `:tabnew`, create a new empty tab.
*   c\_mode `:tabc`, close tab.
*   c\_mode `:tabs`, list all tabs.
*   c\_mode `:gt`, turn to next tab.
*   c\_mode `:ngt`, turn the nth tab.
*   c\_mode `:gT`, turn to previous tab.
*   c\_mode `:tabmn`, move to the nth tab.
*   c\_mode `:tabo`, only reserve current tab and close others.
*   c\_mode `:drop`, open a new file in current tab.

## Fold

### Setting save and load fold state

    function! MakeViewCheck()
        if has('quickfix') && &buftype =~ 'nofile'
            " Buffer is marked as not a file
            return 0
        endif
        if empty(glob(expand('%:p')))
            " File does not exist on disk
            return 0
        endif
        if len($TEMP) && expand('%:p:h') == $TEMP
            " We're in a temp dir
            return 0
        endif
        if len($TMP) && expand('%:p:h') == $TMP
            " Also in temp dir
            return 0
        endif
        if index(g:skipview_files, expand('%')) >= 0
            " File is in skip list
            return 0
        endif
        return 1
    endfunction
    augroup vimrcAutoView
        autocmd!
        " Autosave & Load Views.
        autocmd BufWritePost,BufLeave,WinLeave ?* if MakeViewCheck() | mkview | endif
        autocmd BufWinEnter ?* if MakeViewCheck() | silent loadview | endif
    augroup end

### Basic Usages

*   c\_mode `:set foldmethod={manual, indent, marker, expr, syntax, diff}`
*   c\_mode `:linenumer1,linenumer2 fold` create fold base linenumbers
*   c\_mode `zf`, define fold
*   c\_mode `fold`
*   c\_mode `foldclose`
*   c\_mode `zd`, delete fold
*   c\_mode `zo`, open fold
*   c\_mode `zc`, close fold
*   c\_mode `zO`, open fold recursive
*   c\_mode `zC`, close fold recursive
*   c\_mode `zr`, open one level fold
*   c\_mode `zm`, close one level fold
*   c\_mode `zR`, open all fold recursive
*   c\_mode `zM`, close all fold recursive
*   c\_mode `zj`, cursor jump to the next fold
*   c\_mode `zk`, cursor jump to the previous fold
*   c\_mode `[z`, cursor jump to the start of open fold
*   c\_mode `]z`, cursor jump to the end of open fold

## Box visual mode

*   n\_mode `"CTRL-v"`, enter the box visual mode.
*   `I` insert at the left of selected lines
*   `A` insert at the right of selected lines
*   `r` replace selected

## Numbers

### Basic Usages

*   n\_mode `CTRL-a` number increment by 1
*   n\_mode `CTRL-x` number decrement by 1
*   n\_mode `NCTRL-a` number increment by `N`
*   n\_mode `NCTRL-x` number decrement by `N`

### Using macro

*   To add 5 to frist number each line
*   Steps:
    1.  press `qa`, start to recode actions in register `a`.
    2.  press `05ctrl-aj`, to add 5 to first number in current line,
        and move cursor to next line.
    3.  press `q`, stop recoding.
    4.  use the macro in register `a`.

<!-- -->

```
This is a test line, the number is 2009.
The number is 2019. This is a test line, the number is 2007.
Here is 13. This is a test line, the number is 2007.
This is a test line, the number is 2010.
The number is 2020. This is a test line, the number is 2007.
Here is 13. This is a test line, the number is 2007.
```

### Edit macro

The method of print macro content in specific register
is same as paste from |registers|.

*   n\_mode `"ap` , `a` should be any other register's name.

The register contents are allowed to be edited.

*   c\_mode `:let @a='05ctrl-aj'`, to edit macro in register `a`.
*   c\_mode `:let @b='05ctrl-xj'`, to edit macro in register `b`.

### Name array automatic

To generate element's name of array like:

    array_name[0] = 0;          array_name[0] = 0;
    array_name[0] = 0;          array_name[1] = 0;
    array_name[0] = 0;          array_name[2] = 0;
    array_name[0] = 0;          array_name[3] = 0;
    array_name[0] = 0;          array_name[4] = 0;
    array_name[0] = 0;   ---->  array_name[5] = 0;
    array_name[0] = 0;          array_name[6] = 0;
    array_name[0] = 0;          array_name[7] = 0;
    array_name[0] = 0;          array_name[8] = 0;
    array_name[0] = 0;          array_name[9] = 0;
    array_name[0] = 0;          array_name[10] = 0;

Steps:

1.  Select array index numbers which need be increased, by `block-visual mode`.
2.  press `g`.
3.  press `CTRL-a` or `CTRL-x`.

### Put `range`

*   c\_mode `:put =range(1000,1003)`
*   c\_mode `:208put =range(1000,1003)`
*   c\_mode `:0put =range(1000,1003)`
*   c\_mode `:$put =range(1000,1003)`

### Generate a list of IP address

*   mode `:for i in range(195,200) | put = '192.168.8.'.i | endfor`

### print each line number at beginning by `Substitute` and `printf`

*   c\_mode `:%s/^/\=printf('%-4d', line('.'))`
*   c\_mode `:%s/^/\=printf('%4d ', line('.'))`
*   c\_mode `:%s/^/\=printf('%04d ', line('.'))`

```
Test line 1        223 Test line 1        230 223 Test line 1        0230  230 223 Test line 1
Test line 2        224 Test line 2        231 224 Test line 2        0231  231 224 Test line 2
Test line 3  ----> 225 Test line 3  ----> 232 225 Test line 3  ----> 0232  232 225 Test line 3
Test line 4        226 Test line 4        233 226 Test line 4        0233  233 226 Test line 4
Test line 5        227 Test line 5        234 227 Test line 5        0234  234 227 Test line 5
```

## VimGrep

### Basic Usages

*   c\_mode `:vimgrep /word/g %`, grep in current file.
*   c\_mode `:vimgrep /word/g **/*`, grep in current directory and sub directories.
*   c\_mode `:cope` or `cw`, open matching list
*   c\_mode `:cprev`, jump to previous matching
*   c\_mode `:cnext`, jump to next matching
*   c\_mode `:cfirst`, jump to first matching
*   c\_mode `:clast`, jump to last matching

## Spelling

*   c\_mode `:set invspell`, enable spell checker
*   c\_mode `]s`, go to next misspelled word
*   c\_mode `[s`, go to previous misspelled word
*   c\_mode `z=`, get action suggestion
*   c\_mode `zg`, add a word to your dictionary
*   c\_mode `zug`, remove a word to your dictionary

## VimDiff

### Open files with VimDiff mode

    vimdiff file1 file2
    vim -d file1 file2

### Basic Usages

*   c\_mode `:set noscrollbind`
*   c\_mode `:diffget`
*   c\_mode `:diffput`
*   n\_mode `]c`, jump to next change
*   n\_mode `[c`, jump to previous change

## conceal

## Debug

### Start-up

```sh
nvim --start-up startup.txt

c\_mode `:scriptnames`
```

### Debug mode

```sh
nvim -D some.vim
```

## Remote Editing Files via SCP

```sh
nvim scp://root@router.lan//etc/hosts
```


## F.Q.A

### What is the difference between

`set clipboard=unnamed` and `set clipboard=unamedplus` \?

On Mac OS X and Windows, the `*` and `+` registers both
point to the system clipboard so unnamed and unnamedplus
have the same effect: the unnamed register is synchronized
with the system clipboard.

On Linux, you have essentially two clipboards: one is pretty
much the same as in the other OSes (Ctrl-C and Ctrl-V in
other programs, mapped to register `+` in Vim),
the other is the \" selection \" clipboard (mapped to
register `*` in Vim).

Using only unnamedplus on Linux, Windows and Mac OS X allows you to:

*   Ctrl-C in other programs and put in Vim with p on all three platforms
*   yank in Vim with y and Ctrl-V in other programs on all three platforms.

If you also want to use Linux\'s \" selection \" clipboard,
you will also need unnamed.

Here is a cross-platform value:

    set clipboard^=unnamed,unnamedplus

Reference:

    :h 'clipboard'
    (and follow the tags)
