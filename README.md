# mysql-
mysql  backup
主要用来备份数据库文件

xtrabackup备份和恢复MySQL
xtrabackup有两个主要的工具：innobackupex和xtrabackup，xtrabackup只能备份InnoDB和XtraDB数据表，innobackupex封装了xtrabackup，可以备份MyISAM数据表。
MySQL数据库本身提供的工具并不支持真正的增量备份，二进制日志恢复是point-in-time(时间点)的恢复而不是增量备份。Xtrabackup工具支持对InnoDB存储引擎的增量备份，工作原理如下：
1.首先完成一个完全备份，并记录下此时检查点的LSN(LogSequence Number)。
2.在进程增量备份时，比较表空间中每个页的LSN是否大于上次备份时的LSN，如果是，则备份该页，同时记录当前检查点的LSN。
