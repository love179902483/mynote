### mysql lesson04 （mysql配置文件）

* ##### log-bin 
  用于主从复制,二进制日志
* ##### log-error
  错误日志

* ##### log
  查询日志：默认关闭，记录查询的sql语句，如果开启会减低mysql的整体性能，因为记录日志会消耗宿主机资源

* ##### 数据文件
  * 查看所有现有数据库
    ```
        ls -1F | grep  ^d
    ```
    ![avatar](https://raw.githubusercontent.com/love179902483/mynote/master/mysql-lesson/photos/lesson_004_01.png)

    默认路径： /var/lib/mysql/

  * 数据文件
    |文件类型|作用|
    |---|---|
    |frm文件|存放表结构|
    |myd文件|存放表数据|
    |myi文件|存放表索引|
