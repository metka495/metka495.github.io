---
title: Mysql 隔离级别
date: 2020-04-01
categories:
- mysql
tags: 
- mysql
---

# Read Uncommitted #

x=1
> T时间线：----------------------------------------------------------------------------> commit
> 
> 事务A：x=1, set x=2,  set x=3 , rollback  x=1
> 
> 事务B：x=1, read x=2, reda x=3 read x=3(*出现脏数据*)

事务B可以读到事务A未提交的数据 这样事务A要是发生异常回滚数据 事务B读到的数据就是脏数据

# Read committed #

x=1
> T时间线：----------------------------------------------------------------------------> commit
> 
> 事务A：x=1, set x=2,  set x=3  commit
> 
> 事务B：x=1, read x=1, reda x=1 read x=3 (*不可重复读*)

事务B 再一个事务里读到的两次数据不一样 出现了不可重复读的问题

# Read repeatable #

x=1
> T时间线：----------------------------------------------------------------------------> commit
> 
> 事务A：x=1, set x=2,  set x=3  commit
> 
> 事务B：x=1, read x=1, reda x=1 read x=1  updatex=x+1  read x=4 

可重复读
一个事务里select 操作的是一个快照
update delete insert 读到的数据才是最新版的  所以 x=x+1 之后是4 而不是2
当事务还没结束后 插入数据会让事务B产生幻读

# Serialization #

x=1
> T时间线：----------------------------------------------------------------------------> commit
> 
> 事务A：x=1, set x=2,  set x=3  commit
> 
> 事务B：x=1, read x=1 阻塞...

串行化级别 行表都会被锁住，只能一个事务一个事务的顺序执行

