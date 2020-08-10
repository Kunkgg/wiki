# virtualbox

## Install

### Core package

Core package *virtualbox*, need to choice dkms.

*   for linux kernel choose *virtualbox-host-modules-arch*
*   for other kernels (linux-lts, linux-hardened, linux-zen)
    choose *virtualbox-host-dkms*

### Extension pack

Install *virtualbox-ext-oracle*^AUR^.

### Guest additions disc

It is also recommended to install the *virtualbox-guest-iso*
package on the host running VirtualBox.

This package will act as a disc image that can be used to install
the guest additions onto guest systems other than Arch Linux.

The `.iso` file will be located at:
`/usr/lib/virtualbox/additions/VBoxGuestAdditions.iso`,
and may have to be mounted manually inside the virtual machine.
Once mounted, you can run the guest additions installer inside the guest.

## General settings

### Accessing host USB devices in guest

To use the USB ports of your host machine in your virtual machines,
add users that will be authorized to use this feature to the
`vboxusers` user group.

### Fullscreen mode shows blank screen with i3-wm or awesome-wm

For each vms disable:

    setting --> user interface --> minibar: Full-screen/Seamless

## Reference

[Arch Linux Wiki - virtualbox](https://wiki.archlinux.org/index.php/VirtualBox)
