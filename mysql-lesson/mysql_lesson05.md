### mysql lesson05 （mysql性能下降原因）

1. ##### 执行时间长、等待时间长
     1. 查询语句写的不规范
     2. 索引失效
        * 单值索引 : `create index idx_user_name on user(name)`
        * 复合索引 : `create index idx_user_NameEmail on user(name,email)`
     3. 关联查询太多join（设计缺陷或不得已的需求）
     4. 服务器调优以及个参数设置（缓冲、线程数等） 