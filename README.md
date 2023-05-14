# Домашнее задание к занятию "pacemaker" - Прощина Юлия

### Задание 1

keepalived.conf с мастера
```
state MASTER
interface enp0s8
virtual_router_id 10
priority 100
advert_int 4
authentication {
auth_type PASS
auth_pass 1234
}
virtual_ipaddress {
192.168.122.250 dev enp0s8 label yoHoHo
}
}
```

keepalived.conf с slave 
```
vrrp_instance test {
state BACKUP
interface enp0s8
virtual_router_id 10
priority 90
advert_int 4
authentication {
auth_type PASS
auth_pass 1234
}
virtual_ipaddress {
192.168.122.250 dev enp0s8 label yoHoHo
}
}
```

статус на мастере
![мастер](https://github.com/JulianP-P/sys-homework/blob/keepalived/img/img1.png)

статус на slave
![slave](https://github.com/JulianP-P/sys-homework/blob/keepalived/img/img2.png)


---

