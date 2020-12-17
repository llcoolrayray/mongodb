## 数据库权限
---
### 默认数据库

mongodb 有两个默认的数据库  
* admin: 存储 mongodb 的用户、角色等信息
* local: 存储副本集的元数据

### 权限默认配置

mongodb 默认是不开启鉴权的。若需要鉴权则需要切换到 admin 数据库来创建用户。

### mongodb角色

创建用户时通过给用户添加角色来实现赋予权限

mongodb 常见角色：

角色|描述|  
--|:--:|  
read|可以读取指定数据库中任何数据|  
readWrite|可以读写指定数据库中任何数据，包括创建、重命名、删除集合|  
readAnyDatabase|可以读取所有数据库中任何数据(除了数据库config和local之外)|  
readWriteAnyDatabase|可以读写所有数据库中任何数据(除了数据库config和local之外)|  
dbAdmin|可以读取指定数据库以及对数据库进行清理、修改、压缩、获取统计信息、执行检查等操作|  
dbAdminAnyDatabase|可以读取任何数据库以及对数据库进行清理、修改、压缩、获取统计信息、执行检查等操作(除了数据库config和local之外)|  
clusterAdmin|可以对整个集群或数据库系统进行管理操作|  
userAdmin|可以在指定数据库创建和修改用户|  
userAdminAnyDatabase|可以在指定数据库创建和修改用户(除了数据库config和local之外)|  

示例：创建所有数据库管理用户  
`db.createUser({ user: "useradmin", pwd: "adminpassword", roles: [{ role: "userAdminAnyDatabase", db: "admin" }] })`