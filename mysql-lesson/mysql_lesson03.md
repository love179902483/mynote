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
  *  ###### 查看字符集
  ```
    show variables like "%char%"
    show variables like "%charset%"
  ```
  ![avatar](https://raw.githubusercontent.com/love179902483/mynote/master/mysql-lesson/photos/lesson_003.png)
  
    * ###### 修改my.cnf

    ![avatar](https://raw.githubusercontent.com/love179902483/mynote/master/mysql-lesson/photos/lesson_003_02.png)
    
    ![avatar](https://raw.githubusercontent.com/love179902483/mynote/master/mysql-lesson/photos/lesson_003_03.png)

    * ###### 重启数据库
      如果在修改字符集之前创建的数据库则字符集仍然不生效，需要在创建字符集之后创建的数据库，乱码才消失. 





