### mysql lesson03

* ##### mysql 的安装位置
  先讲配置文件拷贝
  ```
    mysql 5.5
    cp /usr/share/mysql/my-huge.cnf  /etc/my.cnf

    mysql 5.5+
    cp /usr/share/mysql/my-default.cnf  /etc/my.cnf
  ```
* #### 修改mysql默认字符集以及存储路径
  ```
    show variables like "%char%"
    show variables like "%charset%"
  ```

  
