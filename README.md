# Домашнее задание к занятию "Резервное копирование" - Прощина Юлия

### Задание 1
В чём разница между:

- полным резервным копированием, - делает полное копирование всего
- дифференциальным резервным копированием, - сначала делается полное резервное копирование, затем при каждом запуске процесса резервируются только измененные данные, но точкой отсчета является состояние времени полного бэкапа
- инкрементным резервным копированием - работает как дифференцированное копирование, но в отличии от него бэкапятся данные, которые были изменены из последнего слепка, то есть отправная точка каждого нового бэкапа это бэкап n-1

### Задание 2

Установите программное обеспечении Bacula, настройте bacula-dir, bacula-sd, bacula-fd. Протестируйте работу сервисов.

Конфигурационные файлы для [bacula-dir](https://github.com/JulianP-P/sys-homework/blob/bacula/bacula-dir.conf), [bacula-sd](https://github.com/JulianP-P/sys-homework/blob/bacula/bacula-sd.conf), [bacula-fd](https://github.com/JulianP-P/sys-homework/blob/bacula/bacula-fd.conf)

Cкриншот, подтверждающий успешное прохождение резервного копирования.
![мастер](https://github.com/JulianP-P/sys-homework/blob/bacula/img/img1.png)

### Задание 3
Установите программное обеспечении Rsync. Настройте синхронизацию на двух нодах. Протестируйте работу сервиса.
Конфигурация сервера
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
Клиент Rsync
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
![мастер](https://github.com/JulianP-P/sys-homework/blob/bacula/img/img2.png)

---

