# Nginx 静态 HTTP 服务器配置

### 配置 `/etc/nginx/nginx.conf`

```nginx
http {
    ...
    include /etc/nginx/conf.d/*.conf;
    # 可以直接在本文本里添加配置，也可以更改引入文本的，在外部配置
    include /etc/nginx/sites-enabled/your_conf;
}
```

### 配置 `/etc/nginx/sites-enabled/your_conf`

```nginx
server {
	location / {
		root /home/fang/learning_note/.vuepress/dist;
	}
}
```



