# 数据库导入导出

##R语言用RMySQL 链接数据库
##数据库名是中文的暂时无法连接
#install.packages('RMySQL')
```javascript
library('RMySQL')
con <- dbConnect(MySQL(),user='step',password='123456',dbname='tmall',host='172.16.57.72',port= 3306)
dbSendQuery(con,"SET NAMES gbk")
table.names=dbListTables(con)
table.names

##用SQL语句查询dbGetQuery()和dbSendQuery()两种方法  
# 方式一 dbGetQuery()

table  <- dbGetQuery(con,"select 日期,访客数,浏览量,成交金额,客单价 from 运营明细表 ")

#方式二dbSendQuery()
query <- dbSendQuery(con,"select 日期,访客数,浏览量,成交金额,客单价 from 运营明细表 ")
table <- fetch(query,-1) ##取所有数据  
```
* 注意table <- fetch(query,-1) 中-1 参数代表取所有数据；

* 推荐使用dbGetQuery()

参考教程：
[R语言使用RMySQL连接及读写Mysql数据库](http://blog.csdn.net/cl1143015961/article/details/46472343)
