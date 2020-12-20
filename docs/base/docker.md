## docker 安装 mongo
---

#### 下载官方镜像

`docker pull mongo:4`

#### 启动 mongo 容器

`docker run --name mongo -v /root/mongo/data:/data/db -p 27017:27017 -d 镜像ID --auth`

* --name 容器名称
* -v 数据文件挂载到宿主机的路径,/data/db 是 mongo 默认数据文件地址
* -p mongo端口映射到宿主机的指定端口
* -d 后台运行容器
* --auth 连接mongodb需要授权

#### 进入 mongo client

`docker exec -it mongo(容器名称) mongo(启动 mongo shell 的命令) admin(进入 admin 集合)`

#### 添加超级管理员用户

`db.createUser({ user: "useradmin", pwd: "adminpassword", roles: [{ role: "userAdminAnyDatabase", db: "admin" }] })`

#### 查看 mongo 日志

`docker logs mongo(容器名)`