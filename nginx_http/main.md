# Nginx 静态 HTTP 服务器配置

## HTTP 配置

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
	
	location /dist {
		root /home/fang/learning_note/.vuepress;
	}
	
	location /home {
		alias /home/fang/learning_note/.vuepress/dist/;
		index index.html;
	}
}
```

### root 和 alias 的区别

可以通过字面意思理解，root 就是指出 location 后的路径的父(根)路径，而 alias 是用 alias 后声明的路径替换 location 后声明的路径。

**注意，alisa 后边要加 / **

### 测试

```sh
curl localhost/
curl localhost

# 注意这一条命令的结尾一定要加斜线
curl localhost/home/
```

