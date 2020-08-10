
# Examples

## match string pattern

We should delete the `LF(\n)` at the end.

```sh
chosen="$(echo "Poweroff
Reboot
Restart VirtualBox Manager" | dmenu -l 5)"

case "$(echo "${chosen}" | tr -d '\n')" in
    Poweroff)
        confirm "Do you want to poweroff?" "sudo shutdown -h now"
        ;;
    Reboot)
        confirm "Do you want to reboot?" "sudo shutdown -r now"
        ;;
    'Restart VirtualBox Manager')
        _restart_virtualbox
        ;;
    *)
        exit 0
        ;;
esac
```

## printf

```sh
divider===============================
divider=$divider$divider

header="\n %-10s %8s %10s %11s\n"
format=" %-10s %08d %10s %11.2f\n"

width=43

printf "$header" "ITEM NAME" "ITEM ID" "COLOR" "PRICE"

printf "%$width.${width}s\n" "$divider"

printf "$format" \
Triangle 13  red 20 \
Oval 204449 "dark blue" 65.656 \
Square 3145 orange .7
```

## read line by line from var

```sh
while IFS= read -r line
do
    dosomething with "${line}"
done < <(printf '%s\n' "$target")
```

## Redirection

Redirect `stdout` and `stderr` in a same file.

```sh
cat file > output 2>&1
cat file &> output
```

## concepts

### `login shell` and `non-login shell`

login shell

:   Require complete procedure of login, username password.
    e.g. login from tty1~tty6

non-login shell

:   Don't require procedure of loing
    e.g. open terminal in window manager after logined

## config files

### bash enviornment

#### system level configure

For all users.

-   `/etc/profile` and `/etc/profile.d/*`
-   `/etc/bashrc`

#### user level configure

For single user

-   login shell
    -   `~/.bash_profile`
    -   `~/.bash_login`
    -   `~/.profile`
-   non-login shell
    -   `~/.bashrc`

```sh
function load_bash_login_shell_env(){
    if [[ -f ~/.bash_profile ]]; then
        load ~/.bash_profile
    elif [[ -f ~/.bash_login ]]; then
        load ~/.bash_login
    elif [[ -f ~/.profile ]]; then
        load ~/.profile
    else
        no-exist env configure file for bash login shell
    fi
}
```
### hooks

-   `/etc/issue` defines the startup prompt page
-   `/etc/issue.net` defines the startup prompt page for telnet
-   `/etc/motd` defines the prompt page which display after login-in
-   `/etc/bash_logout` defines action after logout
