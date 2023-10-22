University: [ITMO University](https://itmo.ru/ru/)\
Faculty: [FICT](https://fict.itmo.ru)\
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)\
Year: 2023/2024\
Group: K4111c\
Author: Sulimenko Nikita Sergeevich\
Lab: Lab3\
Date of create: 16.10.2023\
Date of finished: -

___
1) Cоздание и приминение configMap [configmap_3.yaml](configmap_3.yaml) с переменными: REACT_APP_USERNAME, REACT_APP_COMPANY_NAME: ``kubectl apply -f configmap_3.yaml``
2) Cоздание и приминение replicaSet [replicaset_3.yaml](replicaset_3.yaml) с 2 репликами контейнера **ifilyaninitmo/itdt-contained-frontend:master** и используя configMap (п.1) передаем переменные REACT_APP_USERNAME, REACT_APP_COMPANY_NAME: ``kubectl apply -f replicaset_3.yaml``
3) Создание service [service_3.yaml](service_3.yaml) и его примение с помощью команды ``kubectl apply -f service_3.yaml``
4) Включение Ingress: ``minikube addons enable ingress``
5) Генирация TLS сертификата: ``openssl req -x509 -newkey rsa:4096 -sha256 -days 12 -nodes -keyout tls.key -out tls.crt -subj "/CN=lab3.front.com"``
6) Импорт сертификата в minikube: ``kubectl create secret tls lab3-local-tls --cert=tls.crt --key=tls.key``
7) Cоздание ingress [ingress_3.yaml](ingress_3.yaml) в minikube, где указан ранее импортированный сертификат, FQDN и имя сервиса и его приминение: ``kubectl apply -f ingress.yaml``
8) Прописываем в hosts (C:\Windows\System32\Drivers\etc\hosts) FQDN и IP адрес localhost: ``127.0.0.1 lab3.front.local``
9) Вход в веб приложение по FQDN используя HTTPS и проверка наличия сертификата: https://lab3.front.local

<img width="905" alt="image" src="https://github.com/kitok07/2023_2024-introduction_to_distributed_technologies-K4111c-sulimenko_n_s/assets/147832281/bbba1d69-a073-48a2-9a94-fc8ccd77ef3f">

<img width="910" alt="image" src="https://github.com/kitok07/2023_2024-introduction_to_distributed_technologies-K4111c-sulimenko_n_s/assets/147832281/0051622d-98c0-43c6-b405-d0a221ad1e17">

![image](https://github.com/kitok07/2023_2024-introduction_to_distributed_technologies-K4111c-sulimenko_n_s/assets/147832281/56d3a6bf-a277-4054-992b-d0a45442d3e4)
