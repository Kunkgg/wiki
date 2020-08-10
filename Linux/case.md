
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
