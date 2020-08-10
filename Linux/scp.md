# scp

Copy file from a remote host to local host SCP example:

```sh
\$ scp username@from_host:file.txt /local/directory/
```

Copy file from local host to a remote host SCP example:

```sh
\$ scp file.txt username@to_host:/remote/directory/
```

Copy directory from a remote host to local host SCP example:

```sh
\$ scp -r username@from_host:/remote/directory/ /local/directory/
```

Copy directory from local host to a remote hos SCP example:

```sh
\$ scp -r /local/directory/ username@to_host:/remote/directory/
```

Copy file from remote host to remote host SCP example:

```sh
\$ scp username@from_host:/remote/directory/file.txt username@to_host:/remote/directory/
```

## My case

copy something from my gcp to local

```sh
scp -v -i ~/.ssh/gcp_gk520_rsa gk_520@gsee.kung.tech:/etc/v2ray/config.json ~/Repos/configs/v2ray/server_v2ray_config_gcp.json
```
