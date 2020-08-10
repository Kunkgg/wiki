
# pacman

## Troubleshooting

### pacman: <filename> exists in filesystem

Error messages:

```sh
error: failed to commit transaction (conflicting files)
python-pip: /usr/lib/python3.8/site-packages/pip/_internal/__pycache__/wheel_builder.cpython-38.pyc exists in filesystem
python-pip: /usr/lib/python3.8/site-packages/pip/_internal/cli/__pycache__/main.cpython-38.pyc exists in filesystem
...

Errors occurred, no packages were upgraded.
```

Solution:

```sh
# Check what package includes the filename.
pacman -Qo <filename>

# If the files don't belong to any package, rename or delete them.
# If you're sure you know what you're doing,
# you can use the --overwrite option, eg:

pacman -S package-name --overwrite /usr/bin/station

# or

pacman -S package-name --overwrite '*'
```
