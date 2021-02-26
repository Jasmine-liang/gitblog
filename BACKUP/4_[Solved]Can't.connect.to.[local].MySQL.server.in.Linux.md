# [[Solved]Can't connect to [local] MySQL server in Linux](https://github.com/Jasmine-liang/gitblog/issues/4)

## Check the MYSQL Reference Manual
[MySQL :: MySQL 5.6 Reference Manual :: B.3.2.2 Can't connect to [local] MySQL server](https://dev.mysql.com/doc/refman/5.6/en/can-not-connect-to-server.html)
I know there are two ways of connecting the **mysqld** server in Unix, So I quckly found that the` /tmp/mysql.sock` was missing.   
## Solution
[資料庫中mysql.sock不存在問題，Can 't connect to local MySQL server through socket '/tmp/mysql.sock '(2) " - IT閱讀](https://www.itread01.com/content/1541103967.html)
Then use `systemctl start mysqld.service` to start the server.    
Use `systemctl status mysqld.service` to check the status of the server.

---

![mysql](https://user-images.githubusercontent.com/63624438/109262911-4cb1f000-783d-11eb-83ca-33d678d8d909.png)
