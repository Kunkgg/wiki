
# mount

## Tips

### Mount disk drive with specific permission

For filesystem with permission, like `ext4`:

```sh
sudo chown -R user:group <mountpoint>
```

For filesystem without permission, like `FAT`, `ntfs`. Specify ower by `mount`:

```sh
sudo mount -o gid=users,fmask=113,dmask=002 /dev/sdb1 /mnt/Archives
```
