## 一. MySQL主从剧本结构

```
[root@localhost MySQL-Binary-Master-slave-Playbook]# tree
.
├── ansible.cfg
├── hosts
├── roles
│   ├── master
│   │   ├── files
│   │   │   └── mysql-5.7.23-linux-glibc2.12-x86_64.tar
│   │   ├── tasks
│   │   │   ├── copy_file.yml
│   │   │   ├── install_MySQL.yml
│   │   │   ├── main.yml
│   │   │   └── rep_MySQL.yml
│   │   ├── templates
│   │   │   ├── my.cnf.j2
│   │   │   ├── mysqld.j2
│   │   │   └── mysql.j2
│   │   └── vars
│   │       └── main.yml
│   └── slave
│       ├── files
│       │   └── mysql-5.7.23-linux-glibc2.12-x86_64.tar
│       ├── tasks
│       │   ├── copy_file.yml
│       │   ├── install_MySQL.yml
│       │   ├── main.yml
│       │   └── rep_MySQL.yml
│       ├── templates
│       │   ├── my.cnf.j2
│       │   ├── mysqld.j2
│       │   └── mysql.j2
│       └── vars
│           └── main.yml
└── site.yml
```

## 二. 基础环境
#### 2.1 数据库启动用户
```
work
```

#### 2.2 数据库安装目录与数据存放目录
```
basedir: /home/work/mysql
datadir: /home/work/data/mysql
```

#### 2.3 数据库root密码
```
Abcd1234_gome
```

#### 2.4 数据库主从复制帐号
```
user: rep
password: xinshouhou
```

#### 2.5 客户端远程连接数据库
```
user: wduser
password: wduser_2019_gome
```

## 三. 执行结果
```
......

TASK [master : 创建主从复制帐号] *******************************************************************************************************************************************
changed: [192.168.1.103]

TASK [master : 客户端远程连接数据库] *****************************************************************************************************************************************
changed: [192.168.1.103]

TASK [master : Get Mysql-master Status] ****************************************************************************************************************************
ok: [192.168.1.103]

......


TASK [slave : Slave_IO_Running] ************************************************************************************************************************************
ok: [192.168.1.102] => {
    "msg": "Slave_IO_Running Yes"
}
ok: [192.168.1.104] => {
    "msg": "Slave_IO_Running Yes"
}

TASK [slave : Slave_SQL_Running] ***********************************************************************************************************************************
ok: [192.168.1.102] => {
    "msg": "Slave_SQL_Running Yes"
}
ok: [192.168.1.104] => {
    "msg": "Slave_SQL_Running Yes"

```


