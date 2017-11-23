### 安装mysql
**centos 安装 mysql：**  
>1. 下载与操作系统匹配的发布包
>2. rpm -Uvh mysql57-community-release-el7-11.noarch.rpm
>3. yum install mysql-community-server

**启动：**   
`service mysqld start`

**停止：**   
`service mysqld stop`

**查看状态：**   
`service mysqld status`

**查看 mysql 临时密码：**   
`grep 'temporary password' /var/log/mysqld.log`

**登录 mysql:**   
`mysql -uroot -p`

**修改 mysql 当前用户密码：**   
`ALTER USER 'root'@'localhost' IDENTIFIED BY '新密码';`

**授权外网访问（此处以 root 用户为例）：  **  
>1. 登录数据库
>2. use mysql;
>3. update user set host='%' where user='root';
>4. flush privileges;

---

### 常见问题

#### mysql error 1366
**描述：**  
**Incorrect string value: '\xE5\xB8 for column 'name' at row 1**

**解决办法:**  
> 查看表字段的编码：  
> show full columns from 表名;  
>
> 对有问题的字段使用如下命令：  
> ALTER TABLE databaseName.tableName  
> CHANGE COLUMN columnName columnName VARCHAR(45) CHARACTER SET 'utf8' NOT NULL;
>
> 检查是否修改完毕：    
> show full columns from 表名;


### 修改 mysql 默认字符集

**查看mysql当前状态:**  
> mysql> status  

**显示信息如下:**  
> mysql  Ver 14.14 Distrib 5.7.19, for Linux (x86_64) using  EditLine wrapper  
>
> Connection id:		9  
> Current database:  
> Current user:		root@localhost  
> SSL:			Not in use  
> Current pager:		stdout  
> Using outfile:		''  
> Using delimiter:	;  
> Server version:		5.7.19 MySQL Community Server (GPL)  
> Protocol version:	10  
> Connection:		Localhost via UNIX socket  
> Server characterset:	latin1  
> Db     characterset:	latin1  
> Client characterset:	utf8  
> Conn.  characterset:	utf8  
> UNIX socket:		/var/lib/mysql/mysql.sock  
> Uptime:			7 hours 55 min 12 sec  

**修改配置文件:**  
>1. 打开 vi /etc/my.cnf  
>2. 添加 character-set-server=utf8，如：  
datadir=/var/lib/mysql  
socket=/var/lib/mysql/mysql.sock  
character-set-server=utf8  
