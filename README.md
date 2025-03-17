# Домашнее задание к занятию «ELK» - Кощеев Иван

### Задание 1. Elasticsearch 

Установите и запустите Elasticsearch, после чего поменяйте параметр cluster_name на случайный. 

*Приведите скриншот команды 'curl -X GET 'localhost:9200/_cluster/health?pretty', сделанной на сервере с установленным Elasticsearch. Где будет виден нестандартный cluster_name*.

### Ответ:

<details>

![image1](https://github.com/SirSeoPro/10-03/blob/main/1.png)

</details>

---

### Задание 2. Kibana

Установите и запустите Kibana.

*Приведите скриншот интерфейса Kibana на странице http://<ip вашего сервера>:5601/app/dev_tools#/console, где будет выполнен запрос GET /_cluster/health?pretty*.

### Ответ:

<details>

```
wget https://mirror.yandex.ru/mirrors/elastic/8/pool/main/k/kibana/kibana-8.17.3-amd64.deb
dpkg -i kibana-8.17.3-amd64.deb
```

![image1](https://github.com/SirSeoPro/10-03/blob/main/1.png)

</details>

---

### Задание 3. Logstash

Установите и запустите Logstash и Nginx. С помощью Logstash отправьте access-лог Nginx в Elasticsearch. 

*Приведите скриншот интерфейса Kibana, на котором видны логи Nginx.*

### Ответ:

<details>


![image1](https://github.com/SirSeoPro/10-03/blob/main/1.png)

</details>

---

### Задание 4. Filebeat. 

Установите и запустите Filebeat. Переключите поставку логов Nginx с Logstash на Filebeat. 

*Приведите скриншот интерфейса Kibana, на котором видны логи Nginx, которые были отправлены через Filebeat.*

### Ответ:

<details>


![image1](https://github.com/SirSeoPro/10-03/blob/main/1.png)

</details>

