# MongoDB

## 1.数据库

**数据库(Database)**

- 数据库是按照数据结构来组织、存储和管理数据的仓库。
- 我们的程序都是在内存中运行的, 一旦程序运行结束或者计算机断电,程序运行中的数据都会丢失。
- 所以我们就需要将一些程序运行的数据持久化到硬盘之中,以确保数据的安全性。而数据库就是数据持久化的最佳选择。
- 说白了,数据库就是存储数据的仓库。



**数据库主要分成两种:**

1.**关系型数据库（RDBMS）**

- MySQL、 Oracle、 DB2、 SQL Server
- 关系数据库中全都是表

2.**非关系型数据库(NoSQL Not Only SQL)**

- MongoDB、 Redis
- 键值对数据库
- 文档数据库MongoDB



### 1.**NoSQL** **介绍** 

NoSQL(NoSQL = Not Only SQL )，意即“不仅仅是 SQL”，它指的是非关系型的数据库，是以 key-value 

形式存储，和传统的关系型数据库不一样，不一定遵循传统数据库的一些基本要求，比如说遵循 SQL 标准、 

ACID 属性、表结构等等。NoSQL 最早被提出是在 20 世纪 80 年代，在当时更多是强调的是与关 

系数据库区别对待，最近这些年被提及的更多是强调协助解决大数据等相关问题。NoSQL 在大 

数据时代有自己的意义。



### 2.**NoSQL** **应用情况介绍** 

国内的互联网蓬勃发展，不仅涌现出 BAT（百度，阿里巴巴，腾讯）之类的巨头，也带动了整个互联 

网行业的发展，大量的创业型公司如春笋般的涌出，在国家层面也提出了“互联网+”和“万众创业”的口 

号。更多传统的行业也开始拥抱互联网。但是无论是做所谓的生态平台还是传统业务的转型，涉及到的业 

务是多种多样的。这个时候企业架构师对于应用系统的核心——数据库管理 不仅有传统的 SQL 选项也有了 

NoSQL 这种适合特定场景需求的选项。 



### 3.**NoSQL** **数据库在以下的这几种情况下比较适用：** 

1、数据模型比较简单； 

2、需要灵活性更强的 IT 系统； 

3、对数据库性能要求较高；

4、不需要高度的数据一致性； 

5、对于给定 key，比较容易映射复杂值的环境。



### 4.**NoSql** **和传统数据库简单对比。** 

非结构型数据库。**没有行、列的概念。用** **JSON** **来存储数据。** 

**集合就相当于“表”，文档就相当于“行”。**

![image-20211009211700994](https://i.loli.net/2021/10/09/45xrleQkyIapHKJ.png)



### 5.**MongoDb** 介绍 

MongoDB 是一个介于关系数据库和非关系数据库之间的产品，是非关系数据库当中功能最丰富，最像 

关系数据库的 NoSql 数据库。他支持的数据结构非常松散，是类似 json 的 bson 格式，因此可以存储比较复 

杂的数据类型。Mongodb 最大的特点是他支持的查询语言非常强大，其语法有点类似于面向对象的查询语 

言，几乎可以实现类似关系数据库单表查询的绝大部分功能，而且还支持对数据建立索引。它的特点是**高** 

**性能**、**易部署**、**易使用**，**存储数据非常方便**。 



- **MongoDB是为快速开发互联网Web应用而设计的数据库系统。**
- **MongoDB的设计目标是极简、灵活、作为Web应用栈的一部分。**
- **MongoDB的数据模型是面向文档的,所谓文档是一种类似于JSON的结构 ,简单理解MongoDB这个数据库中存的是各种各样的JSON。( BSON )**



### 6.配置环境变量

**安装完成配置环境变量** **C:\Program Files\MongoDB\Server\4.2\bin** **加入到系统的** 

**path** **环境变量中**



## 2.命令行操作

#### **1.与mongodb建立连接**

```
mongo
```

#### **2.查看所有数据库列表**

```
show dbs
```

![image-20211009212446295](https://i.loli.net/2021/10/09/ywAqUdxS6tVm3PN.png)



#### **3.使用数据库、创建数据库**

```
use itying
```

如果真的想把这个数据库创建成功，那么必须插入一个数据。 

数据库中不能直接插入数据，只能往集合(collections)中插入数据。下面命令表示给 itying 数 

据库的 user 表中插入数据。 

```
db.user.insert({“name”:”xiaoming”});
```



#### 4.显示当前的数据集合（**mysql** **中叫表）**

```
show collections
```



#### 5.删除集合，删除指定的集合 删除表

删除集合 **db.COLLECTION_NAME.drop()** 

```
db.user.drop()
```



#### 6.删除数据库，删除当前所在的数据库 

```
db.dropDatabase();
```



#### 7.**插入（增加）数据** 

**插入数据，随着数据的插入，数据库创建成功了，集合也创建成功了。**

```
db.表名.insert({"name":"zhangsan"，"age":20});
```



#### **8.**查询所有记录

```
db.user.find(); 
```



#### 9.查询去掉后的当前聚集集合中的某列的重复数据

```
db.user.distinct("name");
```

**会过滤掉 name 中的相同数据**



#### 10.**查询** **age = 22** **的记录**

```
db.user.find({"age": 22});
```



#### 11.查询 **age > 22** **的记录**

```
db.user.find({age: {$gt: 22}});
```



#### 12.**查询** **age < 22** **的记录**

```
db.user.find({age: {$lt: 22}});
```



#### 13.**查询** **age >= 25** **的记录**

```
db.user.find({age: {$gte: 25}});
```



#### 14.**查询** **age <= 25** **的记录**

```
db.user.find({age: {$lte: 25}});
```



#### 15.**查询** **age >= 23** **并且** **age <= 26** 

**注意书写格式**

```
db.user.find({age: {$gte: 23, $lte: 26}});
```



#### 16.**查询** **name** **中包含** **mongo** **的数据** 

**模糊查询用于搜索**

**正则表达式**

```
db.user.find({name: /mongo/});
```



#### 17.**查询** **name** **中以** **mongo** **开头的**

```
db.user.find({name: /^mongo/});
```



#### 18.**查询指定列** **name**、**age** **数据**

**如果给定0或false表示不显示该列，显示其他所有列**

```
db.user.find({}, {name: 1, age: 1});
```



#### 19.**查询指定列** **name**、**age**数据, age > 25

```
db.user.find({age: {$gt: 25}}, {name: 1, age: 1});
```



#### 20.**按照年龄排序** 

**1** **升序** 

```
db.user.find().sort({age: 1});
```

**-1** **降序**

```
db.user.find().sort({age: -1});
```



#### 21.**查询** **name = zhangsan, age = 22** **的数据**

```
db.user.find({name: 'zhangsan', age: 22});
```



#### 22.**查询前** **5** **条数据** 

```
db.user.find().limit(5);
```



#### 23.**查询** **10** **条以后的数据**

```
db.user.find().skip(10);
```



#### 24.**查询在** **5-10** **之间的数据**

```
db.user.find().limit(10).skip(5);
```



#### 25.**or** **与 查询**

```
db.user.find({$or: [{age: 22}, {age: 25}]});
```



#### 26.findOne 查询第一条数据

```
db.user.findOne();
```



#### 27.**查询某个结果集的记录条数** 

**统计数量**

```
db.user.find({age: {$gte: 25}}).count();
```

如果要返回限制之后的记录数量，要使用 count(true)或者 count(非 0) 

```
db.users.find().skip(10).limit(5).count(true);
```



### 3.**修改数据** 

修改里面还有查询条件。你要该谁，要告诉 mongo。 

查找名字叫做小明的，把年龄更改为 16 岁：

```
db.student.update({"name":"小明"},{$set:{"age":16}});
```

查找数学成绩是 70，把年龄更改为 33 岁：

```
db.student.update({"score.shuxue":70},{$set:{"age":33}});
```

**更改所有匹配项目：**

```
db.student.update({"sex":"男"},{$set:{"age":33}},{multi: true});
```

**完整替换，不出现$set 关键字了：** **注意**

```
db.student.update({"name":"小明"},{"name":"大明","age":16});
```



### 4.**删除数据** 

**删除所有匹配项**

```
db.collectionsNames.remove( { "borough": "Manhattan" } ) 
db.users.remove({age: 132});
```

**仅删除一项**

```
db.restaurants.remove( { "borough": "Queens" }, { justOne: true } )
```



| 修饰符 | 含义     |
| ------ | -------- |
| $lt    | 小于     |
| $gt    | 大于     |
| $lte   | 小于等于 |
| $gte   | 大于等于 |
| $or    | 或者     |
| $set   | 更新数据 |





## 2.索引

### 1.相关操作及概念



**索引**是对数据库表中一列或多列的值进行排序的一种结构，可以让我们查询数据库变得 

更快。MongoDB 的索引几乎与传统的关系型数据库一模一样，这其中也包括一些基本的查 

询优化技巧。 



#### 1.**创建索引的命令：**

```
db.user.createIndex({"userame":1})
```



#### 2.**获取当前集合的索引：**

```
db.user.getIndexes()
```



#### 3.**删除索引**

```
db.user.dropIndex({"username":1})
```



**用于关联查找**

在 MongoDB 中，我们同样可以创建**复合索引**，如： 

数字 1 表示 username 键的索引按升序存储，-1 表示 age 键的索引按照降序方式存储。

```
db.user.createIndex({"username":1, "age":-1})
```

​		该索引被创建后，基于 username 和 age 的查询将会用到该索引，或者是基于 username 

的查询也会用到该索引，**但是只是基于** **age** **的查询将不会用到该复合索引。因此可以说，** 

**如果想用到复合索引，必须在查询条件中包含复合索引中的前** **N** **个索引列**。然而如果查询 

条件中的键值顺序和复合索引中的创建顺序不一致的话，MongoDB 可以智能的帮助我们调 

整该顺序，以便使复合索引可以为查询所用。如： 

```
db.user.find({"age": 30, "username": "stephen"})
```



​		对于上面示例中的查询条件，MongoDB 在检索之前将会动态的调整查询条件文档的顺 

序，以使该查询可以用到刚刚创建的复合索引。 

对于上面创建的索引，MongoDB 都会根据索引的 keyname 和索引方向为新创建的索引 

自动分配一个索引名，**下面的命令可以在创建索引时为其指定索引名**，如：

```
db.user.createIndex({"username":1},{"name":"userindex"})
```



**随着集合的增长，需要针对查询中大量的排序做索引。如果没有对索引的键调用** **sort**， 

**MongoDB** **需要将所有数据提取到内存并排序。因此在做无索引排序时，如果数据量过大以** 

**致无法在内存中进行排序，此时** **MongoDB** **将会报错。**



### 2.**唯一索引**

在缺省情况下创建的索引均不是唯一索引。下面的示例将创建唯一索引，如：

```
db.user.createIndex({"userid":1},{"unique":true})
```

如果再次插入 userid 重复的文档时，MongoDB 将报错，以提示插入重复键，如： 

```
db.user.insert({"userid":5}) 
db.user.insert({"userid":5})
```

错误信息：**E11000 duplicate key error index: user.user.$userid_1 dup key: { : 5.0 }**

​		如果插入的文档中不包含 userid 键，那么该文档中该键的值为 null，如果多次插入类似 

的文档，MongoDB 将会报出同样的错误，如： 

```
db.user.insert({"userid1":5}) 
db.user.insert({"userid1":5})
```

错误信息：**E11000 duplicate key error index: user.user.$userid_1 dup key: { : null }**



​		如果在创建唯一索引时已经存在了重复项，我们可以通过下面的命令帮助我们在创建唯 

一索引时消除重复文档，仅保留发现的第一个文档，如： 



1.先删除刚刚创建的唯一索引。

```
db.user.dropIndex({"userid":1})
```

2.插入测试数据，以保证集合中有重复键存在。

```
db.user.remove() 
db.user.insert({"userid":5}) 
db.user.insert({"userid":5})
```

3.重新创建唯一索引

```
db.user.createIndex({"userid":1},{"unique":true })
```

 

**我们同样可以创建复合唯一索引，即保证复合键值唯一即可。如：**

```
db.user.createIndex({"userid":1,"age":1},{"unique":true})
```



### 3.**索引的一些参数**

| Parameter  | Type    | Description                                                  |
| ---------- | ------- | ------------------------------------------------------------ |
| background | Boolean | 建索引过程会阻塞其它数据库操作, background可指定以后台方式创建素引,即增加"background"可选参数。"background" 默认值为false. |
| unique     | Boolean | 建立的索引是否唯一。指定为true创建唯一索引。 默认值为false.  |
| name       | string  | 索引的名称。如果未指定, MongoDB的通过连接索引的字段名和排序顺序生成一个索引名称。 |
| dropDups   | Boolean | 在建立唯一索引时是否删除重复记录指定true创建唯一索引。 默认值为false. |



​		如果在为已有数据的文档创建索引时，可以执行下面的命令，以使 MongoDB 在后台创 

建索引，这样的创建时就不会阻塞其他操作。但是相比而言，以阻塞方式创建索引，会使整 

个创建过程效率更高，但是在创建时 MongoDB 将无法接收其他的操作。

```
db.user.createIndex({"username":1},{"background":true})
```



### 4.**使用** **explain**

​		**explain** 是非常有用的工具，会帮助你获得查询方面诸多有用的信息。只要对游标调用 

该方法，就可以得到查询细节。explain 会返回一个文档，而不是游标本身。如： 

```
db.user.find({"username":"张三"}).explain()
```

![image-20211012091250346](https://i.loli.net/2021/10/12/qunXy1UPMboK5af.png)

explain 会返回查询使用的索引情况，耗时和扫描文档数的统计信息。



**explain executionStats** **查询具体的执行时间**

```
db.tablename.find().explain( "executionStats" ) 
```

关注输出的如下数值：explain.executionStats.executionTimeMillis



## 3.**Mongodb** **账户权限配置**（重点）

### **1.第一步创建超级管理用户**

```js
use admin 

db.createUser({ 
	user:'admin', 
	pwd:'123456', 
	roles:[{role:'root',db:'admin'}] 
}) 
```



### 2.**第二步修改** **Mongodb** **数据库配置文件**

**路径**：C:\Program Files\MongoDB\Server\4.0\bin\mongod.cfg



**配置：**

```js
security:
  authorization: enabled
```



### 3.**第三步重启** **mongodb** **服务**

![image-20211012173617308](https://i.loli.net/2021/10/12/2rfehVNkY8izFI7.png)

![image-20211012173645420](https://i.loli.net/2021/10/12/1guY6abciNhW3xU.png)



### 4.**第四步用超级管理员账户连接数据库**

```js
//本地连接
mongo admin -u 用户名 -p 密码 
//远程连接
mongo 192.168.1.200:27017/test -u user -p password
```



### 5.**第五步给** **eggcms** **数据库创建一个用户** 

**只能访问** **eggcms** **不能访问其他数据库**

```js
use eggcms 

db.createUser(
	{ 
	user: "eggadmin", 
	pwd: "123456", 
	roles: [ { role: "dbOwner", db: "eggcms" } ] 
	}
)
```



## 4.**Mongodb** **账户权限配置中常用的命令**

```js
1、show users; #查看当前库下的用户
```

```js
2、db.dropUser("eggadmin") #删除用户
```

```js
3、db.updateUser( "admin",{pwd:"password"}); #修改用户密码
```

```js
4、db.auth("admin","password"); #密码认证
```



## 5.**Mongodb** **数据库角色**

1. **数据库用户角色：read、readWrite;** 
2. **数据库管理角色：dbAdmin、dbOwner、userAdmin；** 
3. **集群管理角色：clusterAdmin、clusterManager、clusterMonitor、hostManager；** 
4. **备份恢复角色：backup、restore；** 
5. **所有数据库角色：readAnyDatabase、readWriteAnyDatabase、userAdminAnyDatabase、dbAdminAnyDatabase** 
6. **超级用户角色：root**

重点记住**root ，dbOwner**

参考：https://www.cnblogs.com/zzw1787044/p/5773178.html 



## 6.**连接数据库的时候需要配置账户密码** 

```js
const url = 'mongodb://admin:123456@localhost:27017/';
```





## 7.**MongoDB** **的高级查询** **aggregate** **聚合管道**（重点）

### 1.**MongoDB** **聚合管道（Aggregation Pipeline**）

**使用聚合管道可以对集合中的文档进行变换和组合。** 

**实际项目：**表关联查询、数据的统计。 

MongoDB 中使用 

```js
db.COLLECTION_NAME.aggregate([{<stage>},...])
```

来构建和使用聚合管道。先看下官网给的实例，感受一下聚合管道的用法。

![image-20211014155146412](https://i.loli.net/2021/10/14/bON2H5muEZSAq4s.png)



| 管道操作符 | Description                                |
| ---------- | ------------------------------------------ |
| $project   | 增加、删除、重命名字段                     |
| $match     | 条件匹配。只满足条件的文档才能进入下一阶段 |
| $limit     | 限制结果的数量                             |
| $skip      | 跳过文档的数量                             |
| $sort      | 条件排序。                                 |
| $group     | 条件组合结果 统计                          |
| $lookup    | 用以引入其它集合的数                       |



**管道表达式：**

管道操作符作为“键”,所对应的“值”叫做管道表达式。 

例如{$match:{status:"A"}}，$match 称为管道操作符，而 status:"A"称为管道表达式， 

是管道操作符的操作数(Operand)。 

每个管道表达式是一个文档结构，它是由字段名、字段值、和一些表达式操作符组成的。

| **常用表达式操作符** | **Description**        |
| -------------------- | ---------------------- |
| $addToSet            | 将文档指定字段的值去重 |
| $max                 | 文档指定字段的最大值   |
| $min                 | 文档指定字段的最小值   |
| $sum                 | 文档指定字段求和       |
| $avg                 | 文档指定字段求平均     |
| $gt                  | 大于给定值             |
| $lt                  | 小于给定值             |
| $eq                  | 等于给定值             |



### 2.示例

#### 1.**$project** 

修改文档的结构，可以用来重命名、增加或删除文档中的字段。

要求查找 order 只返回文档中 trade_no 和 all_price 字段

```js
db.order.aggregate([ 
    { 
        $project:{ trade_no:1, all_price:1 } 
    } 
])
```

![image-20211014162716281](https://i.loli.net/2021/10/14/piSPnbLvJgat8Ml.png)



#### 2.**$match**

用于过滤文档。用法类似于 find() 方法中的参数。

```js
db.order.aggregate([ 
    { $project:{ trade_no:1, all_price:1 } }, 
    { $match:{"all_price":{$gte:90}} } 
])
```

![image-20211014164446478](https://i.loli.net/2021/10/14/WLtJ1wn5iEKzZPV.png)



#### 3.**$group**

将集合中的文档进行分组，可用于统计结果。 

统计每个订单的订单数量，按照订单号分组

```js
db.order_item.aggregate( [ 
    { 
        $group: {_id: "$order_id", total: {$sum: "$num"}} //"$字段名"
    } 
])
```

![image-20211014165456397](https://i.loli.net/2021/10/14/7iX8JrRyWM9APkd.png)



#### 4.**$sort**

将集合中的文档进行排序。

```js
db.order.aggregate([ 
    { $project:{ trade_no:1, all_price:1 } }, 
    { $match:{"all_price":{$gte:90}} }, 
    { $sort:{"all_price":-1} } 
])
```

![image-20211014165808833](https://i.loli.net/2021/10/14/gfdmpwXVeotjil5.png)



#### 5.**$limit**

```js
db.order.aggregate([ 
    { $project:{ trade_no:1, all_price:1 } }, 
    { $match:{"all_price":{$gte:90}} }, 
    { $sort:{"all_price":-1} }, 
    { $limit:1 } 
])
```

![image-20211014165835499](https://i.loli.net/2021/10/14/mLcnfvz6ghD2MxV.png)



#### 6.**$skip**

```js
db.order.aggregate([ 
    { $project:{ trade_no:1, all_price:1 } }, 
    { $match:{"all_price":{$gte:90}} }, 
    { $sort:{"all_price":-1} },
    { $skip:1 } 
])
```

![image-20211014165922874](https://i.loli.net/2021/10/14/5GBvJ6PlCcteyrU.png)



#### 7.**$lookup** **表关联** (重点)

```js
db.order.aggregate([ 
    { $lookup: { 
        from: "order_item", //关联那个表
        localField: "order_id", //父表关联字段
        foreignField: "order_id", //字表关联字段
        as:"items" //关联后的数据放哪
    	} 
    } 
])
```



**表关联查询**

```js
db.order.aggregate([ 
    { 
        $lookup: { 
            from: "order_item", 
            localField: "order_id", 
            foreignField: "order_id", 
            as: "items" } 
    }, 
    { $project:{ trade_no:1, all_price:1,items:1 } }, 
    { $match:{"all_price":{$gte:90}} }, 
    { $sort:{"all_price":-1} }, 
])
```



# Node操作MongoDB

## [mongoose](https://mongoosejs.com/)（官方文档）

- 之前我们都是通过shel来完成对数据库的各种操作的 ,在开发中大部分时候我们都需要通过程序来完成对数据库的操作。
- 而Mongoose就是一 个让我们可以通过Node来操作MongoDB的模块。
- Mongoose是一 个对象文档模型( ODM)库，它对Node原生的MongoDB模块进行了进-步的优化封装，并提供了更多的功能。
- 在大多数情况下,它被用来把结构化的模式应用到一个MongoDB集合,并提供了验证和类型转换等好处



**mongoose的好处**

1. 可以为文档创建一个模式结构( Schema )
2. 可以对模型中的对象/文档进行验证
3. 数据可以通过类型转换转换为对象模型
4. 可以使用中间件来应用业务逻辑挂钩
5. 比Node原生的MongoDB驱动更容易



**mongoose中为我们提供了几个新的对象**

**Schema(模式对象)**

​	Schema对象定义约束了数据库中的文档结构

**Model**

​	Model对象作为集合中的所有文档的表示，相当于MongoDB数据库中的集合collection

**Document**

​	Document表示集合中的具体文档,相当于集合中的一个具体的文档



## 1.连接

**[Connections](http://mongoosejs.net/docs/connections.html#connections)**

你可以使用 `mongoose.connect()` 方法连接 MongoDB 。

```javascript
mongoose.connect('mongodb://localhost/myapp');
```

这是连接到本地 `myapp` 数据库默认接口(27017)的最小配置。 本地连接失败可以尝试连接 127.0.0.1 。 local hostname 被修改有时候会引起问题。

你也可以在 `uri` 中指定多个参数：

**在使用密码登录前，这个数据库得有用户**

```javascript
mongoose.connect('mongodb://username:password@host:port/database?options...');
```

`connect()` 函数接受回调函数，或返回一个 [promise](http://mongoosejs.net/docs/promises.html)。

```javascript
mongoose.connect(uri, options, function(error) {
  // Check error in initial connection. There is no 2nd param to the callback.
});

// Or using promises
mongoose.connect(uri, options).then(
  () => { /** ready to use. The `mongoose.connect()` promise resolves to undefined. */ },
  err => { /** handle initial connection error */ }
);
```



**[多个连接](http://mongoosejs.net/docs/connections.html)**详细看官网



## 2.Models

[Models](http://mongoosejs.net/docs/api.html#model-js) 是从 `Schema` 编译来的构造函数。 它们的实例就代表着可以从数据库保存和读取的 [documents](http://mongoosejs.net/docs/documents.html)。 从数据库创建和读取 document 的所有操作都是通过 model 进行的。

**编译你的第一个 model**

```javascript
var schema = new mongoose.Schema({ name: 'string', size: 'string' });
var Tank = mongoose.model('Tank', schema);
```

第一个参数是跟 model 对应的集合（ collection ）名字的 *单数* 形式。 **Mongoose 会自动找到名称是 model 名字 复数形式的 collection** 。 对于上例，Tank 这个 model 就对应数据库中 **tanks** 这个 collection。`.model()` 这个函数是对 `schema` 做了拷贝（生成了 model）。 你要确保在调用 `.model()` 之前把所有需要的东西都加进 `schema` 里了！



**构造 documents**

[Documents](http://mongoosejs.net/docs/documents.html) 是 model 的实例。 创建它们并保存到数据库非常简单：

```javascript
var Tank = mongoose.model('Tank', yourSchema);

var small = new Tank({ size: 'small' });
small.save(function (err) {
  if (err) return handleError(err);
  // saved!
})

// or

Tank.create({ size: 'small' }, function (err, small) {
  if (err) return handleError(err);
  // saved!
})
```



## 3.Queries 查询

[Model](http://mongoosejs.net/docs/models.html) 的多个静态辅助方法都可以查询文档。

[Model](http://mongoosejs.net/docs/api.html#model_Model) 的方法中包含查询条件参数的（ [find](http://mongoosejs.net/docs/api.html#model_Model.find) [findById](http://mongoosejs.net/docs/api.html#model_Model.findById) [count](http://mongoosejs.net/docs/api.html#model_Model.count) [update](http://mongoosejs.net/docs/api.html#model_Model.update) ）都可以按以下两种方式执行：

- 传入 `callback` 参数，操作会被立即执行，查询结果被传给回调函数（ callback ）。
- 不传 `callback` 参数，[Query](http://mongoosejs.net/docs/api.html#query-js) 的一个实例（一个 query 对象）被返回，这个 query 提供了构建查询器的特殊接口。

[Query](http://mongoosejs.net/docs/api.html#query-js) 实例有一个 `.then()` 函数，用法类似 promise。

如果执行查询时传入 `callback` 参数，就需要用 JSON 文档的格式指定查询条件。JSON 文档的语法跟 [MongoDB shell](http://docs.mongodb.org/manual/tutorial/query-documents/) 一致。

```javascript
var Person = mongoose.model('Person', yourSchema);

// 查询每个 last name 是 'Ghost' 的 person， select `name` 和 `occupation` 字段
Person.findOne({ 'name.last': 'Ghost' }, 'name occupation', function (err, person) {
  if (err) return handleError(err);
  // Prints "Space Ghost is a talk show host".
  console.log('%s %s is a %s.', person.name.first, person.name.last,
    person.occupation);
});
```

上例中查询被立即执行，查询结果被传给回调函数。Mongoose 中所有的回调函数都使用 `callback(error, result)` 这种模式。如果查询时发生错误，`error` 参数即是错误文档， `result` 参数会是 null。如果查询成功，`error` 参数是 null，`result` 即是查询的结果。

Mongoose 中每一处查询，被传入的回调函数都遵循 `callback(error, result)` 这种模式。查询结果的格式取决于做什么操作： [findOne()](http://mongoosejs.net/docs/api.html#model_Model.findOne) 是单个文档（有可能是 null ），[find()](http://mongoosejs.net/docs/api.html#model_Model.find) 是文档列表， [count()](http://mongoosejs.net/docs/api.html#model_Model.count) 是文档数量，[update()](http://mongoosejs.net/docs/api.html#model_Model.update) 是被修改的文档数量。 [Models API](http://mongoosejs.net/docs/api.html#model-js) 文档中有详细描述被传给回调函数的值。

下面来看不传入 `callback` 这个参数会怎样：

```javascript
// 查询每个 last name 是 'Ghost' 的 person
var query = Person.findOne({ 'name.last': 'Ghost' });

// select `name` 和 `occupation` 字段
query.select('name occupation');

// 然后执行查询
query.exec(function (err, person) {
  if (err) return handleError(err);
  // Prints "Space Ghost is a talk show host."
  console.log('%s %s is a %s.', person.name.first, person.name.last,
    person.occupation);
});
```

以上代码中，`query` 是个 [Query](http://mongoosejs.net/docs/api.html#query-js) 类型的变量。 `Query` 能够用链式语法构建查询器，无需指定 JSON 对象。 下面2个示例等效。

```javascript
// With a JSON doc
Person.
  find({
    occupation: /host/,
    'name.last': 'Ghost',
    age: { $gt: 17, $lt: 66 },
    likes: { $in: ['vaporizing', 'talking'] }
  }).
  limit(10).
  sort({ occupation: -1 }).
  select({ name: 1, occupation: 1 }).
  exec(callback);

// Using query builder
Person.
  find({ occupation: /host/ }).
  where('name.last').equals('Ghost').
  where('age').gt(17).lt(66).
  where('likes').in(['vaporizing', 'talking']).
  limit(10).
  sort('-occupation').
  select('name occupation').
  exec(callback);
```

[Query API](http://mongoosejs.net/docs/api.html#query-js) 文档中有查询函数的完整列表。



## 4.[验证](http://mongoosejs.net/docs/validation.html#验证)



如果你要使用验证，请注意一下几点：

- 验证定义于 [SchemaType](http://mongoosejs.net/docs/schematypes.html)
- 验证是一个[中间件](http://mongoosejs.net/docs/middleware.html)。它默认作为 pre('save')` 钩子注册在 schema 上
- 你可以使用 `doc.validate(callback)` 或 `doc.validateSync()` 手动验证
- 验证器不对未定义的值进行验证，唯一例外是 [`required` 验证器](http://mongoosejs.net/docs/api.html#schematype_SchemaType-required)
- 验证是异步递归的。当你调用 [Model#save](http://mongoosejs.net/docs/api.html#model_Model-save)，子文档验证也会执行，出错的话 [Model#save](http://mongoosejs.net/docs/api.html#model_Model-save) 回调会接收错误
- 验证是可定制的



```javascript
    var schema = new Schema({
      name: {
        type: String,
        required: true
      }
    });
    var Cat = db.model('Cat', schema);

    // This cat has no name :(
    var cat = new Cat();
    cat.save(function(error) {
      assert.equal(error.errors['name'].message,
        'Path `name` is required.');

      error = cat.validateSync();
      assert.equal(error.errors['name'].message,
        'Path `name` is required.');
    });
  
```

**[内建 Validators](http://mongoosejs.net/docs/validation.html#内建-validators)**



Mongoose 有一些内建验证器。

- 所有 [SchemaTypes](http://mongoosejs.net/docs/schematypes.html) 都有内建 [required](http://mongoosejs.net/docs/api.html#schematype_SchemaType-required) 验证器。required 验证器使用 [`checkRequired()` 函数](http://mongoosejs.net/docs/api.html#schematype_SchemaType-checkRequired) 判定这个值是否满足 required 验证器
- [Numbers](http://mongoosejs.net/docs/api.html#schema-number-js) 有 [min](http://mongoosejs.net/docs/api.html#schema_number_SchemaNumber-min) 和 [max](http://mongoosejs.net/docs/api.html#schema_number_SchemaNumber-max) 验证器.
- [Strings](http://mongoosejs.net/docs/api.html#schema-string-js) 有 [enum](http://mongoosejs.net/docs/api.html#schema_string_SchemaString-enum)、 [match](http://mongoosejs.net/docs/api.html#schema_string_SchemaString-match)、 [maxlength](http://mongoosejs.net/docs/api.html#schema_string_SchemaString-maxlength) 和 [minlength](http://mongoosejs.net/docs/api.html#schema_string_SchemaString-minlength) 验证器

上面的链接提供了使用和错误处理相关的详细信息



```javascript
    var breakfastSchema = new Schema({
      eggs: {
        type: Number,
        min: [6, 'Too few eggs'],
        max: 12
      },
      bacon: {
        type: Number,
        required: [true, 'Why no bacon?']
      },
      drink: {
        type: String,
        enum: ['Coffee', 'Tea'],
        required: function() {
          return this.bacon > 3;
        }
      }
    });
    var Breakfast = db.model('Breakfast', breakfastSchema);

    var badBreakfast = new Breakfast({
      eggs: 2,
      bacon: 0,
      drink: 'Milk'
    });
    var error = badBreakfast.validateSync();
    assert.equal(error.errors['eggs'].message,
      'Too few eggs');
    assert.ok(!error.errors['bacon']);
    assert.equal(error.errors['drink'].message,
      '`Milk` is not a valid enum value for path `drink`.');

    badBreakfast.bacon = 5;
    badBreakfast.drink = null;

    error = badBreakfast.validateSync();
    assert.equal(error.errors['drink'].message, 'Path `drink` is required.');

    badBreakfast.bacon = null;
    error = badBreakfast.validateSync();
    assert.equal(error.errors['bacon'].message, 'Why no bacon?');
  
```

[`unique` 不是验证器](http://mongoosejs.net/docs/validation.html#unique-不是验证器)



初学者常见的 `unique` 选项 *不是*验证器。这是构建 [MongoDB unique indexes](https://docs.mongodb.com/manual/core/index-unique/) 的辅助函数。 详见 [FAQ](http://mongoosejs.net/docs/faq.html)。



```js
    var uniqueUsernameSchema = new Schema({
      username: {
        type: String,
        unique: true
      }
    });
    var U1 = db.model('U1', uniqueUsernameSchema);
    var U2 = db.model('U2', uniqueUsernameSchema);

    var dup = [{ username: 'Val' }, { username: 'Val' }];
    U1.create(dup, function(error) {
      // Race condition! This may save successfully, depending on whether
      // MongoDB built the index before writing the 2 docs.
    });

    // Need to wait for the index to finish building before saving,
    // otherwise unique constraints may be violated.
    U2.once('index', function(error) {
      assert.ifError(error);
      U2.create(dup, function(error) {
        // Will error, but will *not* be a mongoose validation error, it will be
        // a duplicate key error.
        assert.ok(error);
        assert.ok(!error.errors);
        assert.ok(error.message.indexOf('duplicate key error') !== -1);
      });
    });

    // There's also a promise-based equivalent to the event emitter API.
    // The `init()` function is idempotent and returns a promise that
    // will resolve once indexes are done building;
    U2.init().then(function() {
      U2.create(dup, function(error) {
        // Will error, but will *not* be a mongoose validation error, it will be
        // a duplicate key error.
        assert.ok(error);
        assert.ok(!error.errors);
        assert.ok(error.message.indexOf('duplicate key error') !== -1);
      });
    });
  
```

[自定义验证器](http://mongoosejs.net/docs/validation.html#自定义验证器)



如果内建检验器不够用了，你可以定义满足自己需要的检验器

自定义检验器通过传入一个检验函数来定义，更多细节请看 [`SchemaType#validate()` API 文档](http://mongoosejs.net/docs/api.html#schematype_SchemaType-validate)。



```js
    var userSchema = new Schema({
      phone: {
        type: String,
        validate: {
          validator: function(v) {
            return /\d{3}-\d{3}-\d{4}/.test(v);
          },
          message: '{VALUE} is not a valid phone number!'
        },
        required: [true, 'User phone number required']
      }
    });

    var User = db.model('user', userSchema);
    var user = new User();
    var error;

    user.phone = '555.0123';
    error = user.validateSync();
    assert.equal(error.errors['phone'].message,
      '555.0123 is not a valid phone number!');

    user.phone = '';
    error = user.validateSync();
    assert.equal(error.errors['phone'].message,
      'User phone number required');

    user.phone = '201-555-0123';
    // Validation succeeds! Phone number is defined
    // and fits `DDD-DDD-DDDD`
    error = user.validateSync();
    assert.equal(error, null);
  
```

### [引用其他文档](http://mongoosejs.net/docs/queries.html#refs)

MongoDB 中没有表连接，但引用其他集合的文档有时也会需要。[Population](http://mongoosejs.net/docs/populate.html) 即为此而生。 [这里](http://mongoosejs.net/docs/api.html#query_Query-populate) 有关于从其他集合引用文档的更多内容。

## 5.集合关联

- 通常不同集合的数据之间是有关系的，例如文章信息和用户信息存储在不同集合中，但文章是某个用户发表的，要查询文章的所有信息包括发表用户，就需要用到集合关联。

- 使用id对集合进行关联

- 使用populate方法进行关联集合查询

MongoDB在3.2以上的版本有类似于 join 的 $lookup 聚合操作符，其实 Mongoose 有一个更强大的替代方法，叫做populate ( )，它允许你在其他集合中引用文档，实现更简洁优雅的查询操作。

业务需求如下：查询文章信息，并显示文章的分类以及文章的作者信息，下面用 populate 来实现这个查询需求。

**1.定义文章分类的schema生成模型导出，文件名 aritcleCate.js**

```js
// 引入自定义的数据库连接文件
var mongoose=require('./db.js');
var ArticleCateSchema = new mongoose.Schema({
    title  : { 
        type: String, 
        unique: true 
    },
    descripton:String,
    addtime:{
        type:Date       
    }
});

module.exports=mongoose.model('ArticleCate',ArticleCateSchema,'articlecate');
```



​	**2.定义用户的schema生成模型导出，文件名 user.js**

```js
// 引入自定义的数据库连接文件
var mongoose = require('./db.js');

var UserSchema = new mongoose.Schema({
    username: {
        type: String,
        unique: true
    },
    password: String,
    name: String,
    age: Number,
    sex: String,
    tel: Number,
    status: {
        type: Number,
        default: 1
    }
});
module.exports = mongoose.model('User', UserSchema, 'user');
```

**3.定义文章的 schema 生成模型导出，文件名 article.js**

**通过给 schema 中的关联字段添加 ref 与指定的模型建立关联**

```js
// 引入自定义的数据库连接文件
var mongoose = require('./db.js');
var Schema = mongoose.Schema;

var ArticleSchema = new Schema({
    title: {
        type: String, unique: true
    },
    // 分类ID
    cid: {
        type: Schema.Types.ObjectId,
        // 引用文章分类的模型  
        ref: "ArticleCate"
    },
    // 用户ID
    author_id: {
        type: Schema.Types.ObjectId,
        // 引用 user 的模型
        ref: "User"
    },
    author_name: {
        type: String
    },
    descripton: String,
    content: String
});


module.exports = mongoose.model('Article', ArticleSchema, 'article');
```




**4.执行查询操作**

```js
// 注意使用 populate 需要引入用到的 model
var ArticleCateModel=require('./model/articleCate.js');
var ArticleModel=require('./model/article.js');
var UserModel=require('./model/user.js');

// 文章表、分类表关联
ArticleModel.find({}).populate('cid').exec(function(err,docs){
    console.log(docs);
})

// 文章表、分类表、用户表关联
ArticleModel.find({}).populate('cid').populate('author_id').exec(function(err,docs){
    console.log(docs);
})

```

5.不同实现方式

- $lookup
- populate

[查看此文章](https://blog.csdn.net/weixin_44829437/article/details/108068137?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522163435161816780262573591%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=163435161816780262573591&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-2-108068137.first_rank_v2_pc_rank_v29&utm_term=mongoose%E5%85%B3%E8%81%94%E6%9F%A5%E8%AF%A2&spm=1018.2226.3001.4187)

# 超哥讲述mongoose用法

### 安装：

```
npm i -s mongoose
```

### 连接数据库：

```js
// 1.引入mongoose
const mongooes = require("mongoose");
// 2.连接mongodb数据库
mongooes.connect("mongodb://localhost/users", {
    useNewUrlParser: true,
    useUnifiedTopology: true,
});

// 3.监听mongodb数据库的连接状态
// 绑定数据库连接成功事件
mongooes.connection.once("open", function () {
    console.log("连接成功");
});
// 绑定数据库连接失败事件
mongooes.connection.once("close", function () {
    console.log("数据库连接已经断开");
});

// 4.断开数据库连接(一般不用)
mongooes.disconnect();
```

### 创建模式对象和模型对象：

```js
const Schema=mongooes.schema;
//创建模式对象
const stuSchema=new Schema({
    name:String,
    age:Number,
    gender:{
        type:String,
        default:'female'
    },
    address:String
})
//创建模型对象
const StuModel=stuSchema.model("student",stuSchema); //第一个参数表示创建的集合的名称，第二个参数表示利用的模式对象
```

### 利用模型对象进行增删查改操作：

#### 添加操作：

```js
UserModel.create({ user_id: 100, name: "liu1" }, function (err) {
  if (!err) {
    console.log("插入成功");
  } else {
    console.log(err);
  }
});

let data = [
  { user_id: 101, name: "liu2", age: 22 },
  { user_id: 102, name: "liu3" },
];
UserModel.create(data, function (err) {
  console.log(arguments[1]); //第二个值表示的是所添加的文档对象,是一个数组
});
```

#### 查询操作：

```js
/* 
    查询:
    model.find(conditions,[projection],[options],callback)
    conditions:查询的条件 
    projection:投影  { name: 1, gender: 1, _id: 0 } 或 'name gender -_id'
    options:查询选项  { skip: xx, limit: xx }   
 
    model.findOne(...)
    model.findById(...)

    model.countDocuments(conditions,callback) 查询文档的数量
 */

UserModel.find({}, function (err, data) {
  console.log(data);
});
UserModel.find(
  { name: /liu/i },
  "name gender -_id",
  { skip: 2, limit: 1 },
  function (err, data) {
    console.log(data); //返回的是一个文档对象数组
  }
);

UserModel.findById("5f9fbfba14319e492c0f5bc4", function (err, data) {
  console.log(data);
  console.log(data instanceof UserModel); //true 返回的文档对象属于模型对象（即集合）的实例对象
});

UserModel.countDocuments({}, function (err, data) {
  console.log(data);
});
```

#### 修改操作：

```js
/* 修改：
    model.update(conditions,[doc],[options],callback)
        doc:修改后的文档对象
    model.updateMany(...)
    model.uodateOne(...)
*/
UserModel.updateOne({ name: "liu1" }, { $set: { age: 22 } }, function (
  err,
  data
) {
  if (!err) {
    console.log("修改成功");
  }
});

UserModel.find({ name: "liu1" }, function (err, data) {
  console.log(data);
});
```

#### 删除操作：

```js
/* 
删除：
model.remove(conditions,callback)
model.deleteOne(...)
model.deleteMany(...)
*/
UserModel.remove(
  {
    name: "liu2",
  },
  function (err, data) {
    console.log("删除成功");
  }
);
UserModel.find({}, function (err, data) {
  console.log(data);
});
```
[更多详细](https://blog.csdn.net/weixin_45828332/article/details/114120710?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522163533779916780274116111%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=163533779916780274116111&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-114120710.first_rank_v2_pc_rank_v29&utm_term=mongoose&spm=1018.2226.3001.4187)
