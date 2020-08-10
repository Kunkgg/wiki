
# ncdu

## Introduce

Ncdu, acronym of NCurses Disk Usage.

Scan disk, generate report of disk usage.

It is developed in C. So it's fast.

## Usage

`ncdu` scan current directory

`sudo ncdu -x /` the option `-x` indicates that only count files and
directories on the same filesystem. It will avoid scanning the mounted devices.

`ncdu -q` the option `-q` indicates that `quiet mode`. By default, ncdu will
update the output screen 10 times a second while scanning the directory. This
might consume more bandwidth if you are analyzing the disk usage of a remote
system. Fortunately, this will be decreased to once every 2 seconds in `quiet
mode`. We can use this feature to save bandwidth over remote connections.

Export report, `ncdu -1xo- / | gzip >export.gz`

View exported report, `zcat export.gz | ncdu -f-`

Export and browse it once scanning is done:

```
ncdu -o- | tee export.file | ncdu -f-
```

To scan a remote system, but browse through the files locally, run:

```
ssh -C username@host ncdu -o- / | ncdu -f-
```

## Reference

[ostechnix -
ncdu](https://www.ostechnix.com/check-disk-space-usage-linux-using-ncdu/)
