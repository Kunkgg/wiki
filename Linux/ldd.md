
# ldd -- print shared object dependencies

## Basic Usage

```sh
ldd /bin/ls

	linux-vdso.so.1 (0x00007ffd327bc000)
	libcap.so.2 => /usr/lib/libcap.so.2 (0x00007fab0381f000)
	libc.so.6 => /usr/lib/libc.so.6 (0x00007fab03658000)
	/lib64/ld-linux-x86-64.so.2 =>\
    /usr/lib64/ld-linux-x86-64.so.2 (0x00007fab03873000)
```

## Note

You should never employ ldd on an untrusted executable,
since this may result in the excution of arbitrary code.

A safer alternative when dealing with untrusted
executables is:

```sh
objdump -p /path/to/program | grep NEEDED
```
