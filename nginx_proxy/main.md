# Nginx proxy

配置 `/etc/nginx/nginx.conf` 或者 `/usr/local/etc/nginx/nginx.conf`

将 `http://localhost:8080/` 映射为`http://0.0.0.0:[port_you_set]/api`

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

[官方文档](https://docs.nginx.com/nginx/admin-guide/security-controls/securing-http-traffic-upstream/)

