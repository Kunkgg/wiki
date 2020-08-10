
# nginx

## Troubleshooting

### Warn in log

Log message:

2020/03/23 10:11:06 [warn] 591#591: could not build optimal types\_hash,
you should increase either types\_hash\_max\_size: 1024 or types\_hash\_bucket\_size: 64;
ignoring types\_hash\_bucket\_size

Solution:

add `types_hash_max_size 4096;` in `/etc/nginx/nginx.config/`

```
http {
log_format main '$remote_addr - $remote_user [$time_local] "$request" '
'$status $body_bytes_sent "$http_referer" '
'"$http_user_agent" "$http_x_forwarded_for"';

access_log /var/log/nginx/access.log main;

sendfile on;
tcp_nopush on;
tcp_nodelay on;
keepalive_timeout 65;

types_hash_max_size 4096; # Add this line
```
