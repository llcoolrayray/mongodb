## 备份及恢复
---
#### 热备份与恢复 mongodump 和 mongorestore  

备份： mongodump -h localhost --port 27017 -u=mtpadmin -p=admin --authenticationDatabase=admin -d mtp -o c:\data\dump

```
- -h：host 地址
- --port: 端口号
- -u： 用户名
- -p： 密码
- -d：要备份的数据库名
- -o：备份文件输出路径
- --authenticationDatabase： 用户鉴权的数据库名（鉴权的数据库和用户名确定唯一用户）
```

> Authentication Database  
> 给一个 mongo 数据库添加用户时，该数据库就是这个用户的授权数据库（authenticationDatabase）
> 通过分配其他数据库的 role,一个用户不仅在他的授权数据库中有权限，在其他的数据库也可以有权限。用户名和他的授权数据库是唯一的

恢复： mongorestore -h localhost:27017 -umtpadmin -padmin --authenticationDatabase admin -d mtp --drop c:\data\dump\mtp

`--drop：会在恢复数据前删除所有数据`

