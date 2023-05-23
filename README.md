# Домашнее задание к занятию "резервное копирование" - Прощина Юлия

### Задание 1
### Задание 2


![мастер](https://github.com/JulianP-P/sys-homework/blob/keepalived/img/img1.png)

### Задание 3

```
pid file = /var/run/rsyncd.pid
log file = /var/run/rsyncd.log
transfer logging = true
[data]
path = /home/backup/
uid = root
read only = yes
list = yes
comment = Data backup
auth users = backup
secrets file = /etc/rsyncd.scrt
```

```
#!/bin/bash
date
syst_dir=/home/backup/new
srv_name=debian2
srv_ip=192.168.1.1
srv_user=backup
srv_dir=data
echo "start backup ${srv_name}"
mkdir -p ${syst_dir}${srv_name}/increment/
/usr/bin/rsync -avz --progress --delete --password-file=/etc/rsyncd.scrt ${srv_user}@${srv_ip}::${srv_dir} --backup-dir=/${syst_dir}${srv_name}/increment/`date +%Y-%m-%d`/
/usr/bin/find ${syst_dir}${srv_name}/increment/ -maxdepth 1 -type d -mtime +30 -exec rm -rf {} \;
date
echo "Finish backup ${srv_name}"
```


---

