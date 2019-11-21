# [return](../README.md)

# docker 

## image

```bash
// 拉取镜像
docker pull [name/id]

// 展示本地镜像
docker image ls

// 删除本地镜像
docker image rm [name/id]
```

## container

```bash
// 运行镜像，用于初次启动，参数为 image name/id 
docker run [name/id]

// 运行停止的 container
docker start [name/id]

// 重启 container
docker restart [name/id]

// 停止 container
docker stop [name/id]

// 删除 container
docker rm [name/id]

// 后台运行
ctrl +p+q
```

## dockerfile

```
FROM node:8.16.1

RUN node:8.16.1

COPY helo.js /src

CMD [“node”, “/src/helo.js”]
```