# Домашнее задание к занятию "Кластеризация" - Прощина Юлия

### Задание 1

В чём различие между SMP- и MPP-системами?

В SMP системах процессоры используют общую память. Главный минус такой архитектуры - невозможноть мастабирования. Причины этого: 
- Процессоры могут обращаться к одной ячейке памяти, что приводит к конфликтам. 
- Скорость общей памяти ограничена

В MPP системах у каждого процессора есть своя память, таким образом, систему можно масштабировать.

---

### Задание 2

В чём отличие сильно связанных и слабо связанных систем?

Сильно связанная система состоит из нескольких однородных процессоров и массива общей памяти, в слабо связанных системах нет общей памяи - вся память распределена между процессорными элементами.

---

### Задание 3

Какие преимущества отличают кластерные системы от обычных серверов?
- возможность быстрой масштабируемости
- нет ограничений на размер узлов и кластеров
- повышенная отказоустойчивость

---

### Задание 4

Приведите примеры типов современных кластерных систем.

- отказоустойчивые кластеры (Linux HA, Microsoft Windows Server, Red Hat Cluster Suite)
- кластеры с балансировкой нагрузки (сетевая балансировка, транспортная балансировка, прикладная балансировка)
- вычислительные кластеры (Azure)
- сисемы рапределенных вычислений (kafka, zookeaper, грид-системы)

---

### Задание 5

Где используют сервис Kafka, rabitMQ?

Kafka и rabitMQ используются для передачи данных в режиме реального времени (работают с потоковыми данными). 

---
