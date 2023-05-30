# Домашнее задание к занятию "Балансировка нагрузки. HAProxy/Nginx" - Прощина Юлия

### Задание 1
Что такое балансировка нагрузки и зачем она нужна?
Балансировка нагрузки — это процесс распределения нагрузки на пул серверов
Балансировка позволяет уменьшить время ответа, повышает отказоустойчивость, а также дает возможность масштабировать систему

### Задание 2
Чем отличаются алгоритмы балансировки Round Robin и Weighted Round Robin? В каких случаях каждый из них лучше применять?
Round Robin и Weighted Round Robin распределяют запросы последовательно по пулу. Но Weighted Round Robin учитывает "вес" сервера, ему можно указать соотношение, по которому будут распределяться запросы  по серверам.

Если в пуле все сервера одинаковой мощности, то идеально подойдет Round Robin, если серера разной можности - то Weighted Round Robin.

### Задание 3
Установите и запустите Haproxy.
![мастер](https://github.com/JulianP-P/sys-homework/blob/haproxy/img/img1.png)

### Задание 4
Установите и запустите Nginx.

![nginx](https://github.com/JulianP-P/sys-homework/blob/haproxy/img/img3.png)

### Задание 5
Настройте Nginx на виртуальной машине таким образом, чтобы при запросе:
curl http://localhost:8088/ping
он возвращал в ответе строчку:
"nginx is configured correctly".
![nginxping](https://github.com/JulianP-P/sys-homework/blob/haproxy/img/img2.png)


```
server {
listen 8088;
location /ping {
return 200 'nginx is configured correctly\n';
}
}
```


---

