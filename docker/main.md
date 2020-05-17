### [return](../README.md)

# docker 

## image

```bash
# 拉取镜像
docker pull [name/id]

# 展示本地镜像
docker image ls

# 删除本地镜像
docker image rm [name/id]

# 将运行的 container 提交成 image
docker commit [hash] [name]

# 编译 Dockerfile
docker build [dir] -t [name]

# 改名
docker tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]

# push
docker push name:tag

```

## container

```bash
# 运行镜像，用于初次启动，参数为 image name/id 
docker run [name/id]

-d 后台
-p [本机 post]:[docker post]
-P 打开任意端口

# 运行停止的 container
docker start [name/id]

# 重启 container
docker restart [name/id]

# 停止 container
docker stop [name/id]

# 删除 container
docker rm [name/id]

# 后台运行
ctrl + pq

# ls
docker container ls
```

## dockerfile

```
FROM hub.c.163.com/nce2/nodejs:0.12.2  # Create app directory

RUN mkdir -p /home/Service

WORKDIR /home/Service    # Bundle app source

COPY . /home/Service

RUN npm install

EXPOSE 8888

CMD npm start 
```

## Demo: run a hello node app

### index.js

```js
'use strict';
var express = require('express');
var PORT = 8888;
var app = express();
app.get('/', function (req, res) {
    res.send('Helloworld\n');
});
app.listen(PORT);
console.log('Running on http://localhost:' + PORT);
```

### package.json

```json
{
  "name": "docker_test",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node index.js"
  },
  "author": "fangzidong",
  "license": "ISC",
  "dependencies": {
    "express": "^4.17.1"
  }
}
```

### Dockerfile

```
FROM node:10
RUN mkdir -p /home/Service
WORKDIR /home/Service
COPY ./index.js /home/Service
COPY ./package.json /home/Service
RUN npm install
EXPOSE 8888
CMD npm start
```

### commands

```bash
docker build . -t mynodeapp
```

```bash
docker run -p 8880:8888 mynodeapp
```

### [return](../README.md)