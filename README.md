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

![image2](https://github.com/SirSeoPro/10-03/blob/main/2.png)

</details>

---

### Задание 3. Logstash

Установите и запустите Logstash и Nginx. С помощью Logstash отправьте access-лог Nginx в Elasticsearch. 

*Приведите скриншот интерфейса Kibana, на котором видны логи Nginx.*

### Ответ:

<details>

Мной был установлен logstash и произведенна попытка создать 2 вида yaml файлов. К сожалению ни одна из них не привела к тому, что внутри 


</details>

---

### Задание 4. Filebeat. 

Установите и запустите Filebeat. Переключите поставку логов Nginx с Logstash на Filebeat. 

*Приведите скриншот интерфейса Kibana, на котором видны логи Nginx, которые были отправлены через Filebeat.*

### Ответ:

<details>
Создадим файл /etc/logstash/conf.d/nginx.conf

```

input {
  file {
    path => "/var/log/nginx/access.log"
    start_position => "beginning"
    sincedb_path => "/dev/null"
  }
}

filter {
  grok {
    match => { "message" => "%{COMBINEDAPACHELOG}" }
  }
  date {
    match => [ "timestamp", "dd/MMM/yyyy:HH:mm:ss Z" ]
  }
}

output {
  elasticsearch {
    hosts => ["http://localhost:9200"]
    index => "nginx-logs-%{+YYYY.MM.dd}"
  }
}

```

![image3](https://github.com/SirSeoPro/10-03/blob/main/3.png)

</details>

