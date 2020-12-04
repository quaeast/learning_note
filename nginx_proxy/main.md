# Nginx proxy

配置 `/etc/nginx/nginx.conf` 或者 `/usr/local/etc/nginx`

将 `http://localhost:8080/` 映射为`http`

```nginx
http {
    # ...
    server {
    # ...
    location /api/ {
        proxy_pass http://localhost:8080/;
    }
}
```

