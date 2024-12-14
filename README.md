## Now apply template to container
```sh
bastille create phpmyadmin 14.1-RELEASE 10.0.0.254

bastille bootstrap https://github.com/bastille-templates/phpmyadmin
bastille template phpmyadmin bastille-templates/phpmyadmin
```

## Test Run
```sh
root@localhost~# mysql

# show user list
root@localhost [(none)]> select user,host,password from mysql.user; 
+-------------+-----------+----------+
| User        | Host      | Password |
+-------------+-----------+----------+
| mariadb.sys | localhost |          |
| root        | localhost | invalid  |
| mysql       | localhost | invalid  |
| PUBLIC      |           |          |
+-------------+-----------+----------+
4 rows in set (0.001 sec)

# show database list
root@localhost [(none)]> show databases; 
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
4 rows in set (0.000 sec)

# create test database
root@localhost [(none)]> create database test_database; 
Query OK, 1 row affected (0.000 sec)

# create test table on test database
root@localhost [(none)]> create table test_database.test_table (id int, name varchar(50), address varchar(50), primary key (id)); 
Query OK, 0 rows affected (0.108 sec)

# insert data to test table
root@localhost [(none)]> insert into test_database.test_table(id, name, address) values("001", "FreeBSD", "Hiroshima"); 
Query OK, 1 row affected (0.036 sec)

# show test table
root@localhost [(none)]> select * from test_database.test_table; 
+----+---------+-----------+
| id | name    | address   |
+----+---------+-----------+
|  1 | FreeBSD | Hiroshima |
+----+---------+-----------+
1 row in set (0.000 sec)

# delete test database
root@localhost [(none)]> drop database test_database; 
Query OK, 1 row affected (0.111 sec)

root@localhost [(none)]> exit
Bye
```

## License
This project is licensed under the BSD-3-Clause license.