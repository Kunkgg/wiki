
#   regexp exp

## Match Email address

VimScript

    execute "normal! /\\<[a-zA-Z0-9._%+-]\\+@[a-zA-Z0-9.-]\\{-}\\.[a-zA-Z]\\{2,6}\\>\r"

VimSearch

    \<[a-zA-Z0-9._%+-]\+@[a-zA-Z0-9.-]\{-}\.[a-zA-Z]\{2,6}\>

Grep

    grep -E -o "\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,6}\b" file.txt

## Match IP address


Bash

    IPv4_matcher='^((25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.){3}(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)$'
    IPv6_matcher='^([0-9a-fA-F]{1,4}:){7}[0-9a-fA-F]{1,4}$|^::([0-9a-fA-F]{1,4}:){0,6}[0-9a-fA-F]{1,4}$|^[0-9a-fA-F]{1,4}::([0-9a-fA-F]{1,4}:){0,5}[0-9a-fA-F]{1,4}$|^[0-9a-fA-F]{1,4}:[0-9a-fA-F]{1,4}::([0-9a-fA-F]{1,4}:){0,4}[0-9a-fA-F]{1,4}$|^([0-9a-fA-F]{1,4}:){0,2}[0-9a-fA-F]{1,4}::([0-9a-fA-F]{1,4}:){0,3}[0-9a-fA-F]{1,4}$|^([0-9a-fA-F]{1,4}:){0,3}[0-9a-fA-F]{1,4}::([0-9a-fA-F]{1,4}:){0,2}[0-9a-fA-F]{1,4}$|^([0-9a-fA-F]{1,4}:){0,4}[0-9a-fA-F]{1,4}::([0-9a-fA-F]{1,4}:)?[0-9a-fA-F]{1,4}$|^([0-9a-fA-F]{1,4}:){0,5}[0-9a-fA-F]{1,4}::[0-9a-fA-F]{1,4}$|^([0-9a-fA-F]{1,4}:){0,6}[0-9a-fA-F]{1,4}::$'

    function is_IPv4() {
        [[ "$1" =~ ${IPv4_matcher} ]] && echo "Is IPv4."
    }

    function is_IPv6() {
        [[ "$1" =~ ${IPv6_matcher} ]] && echo "Is IPv6."
    }

    function is_IP() {
        [[ -n "$(is_IPv4 "$1")" || -n "$(is_IPv6 "$1")" ]] && echo "Is IP."
    }

## Match the last feild in line, split by space

Bash

    target=$(host "$1" | grep -E -v '\.$' | grep -E -o "[^ ]*?$")
