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
6) Импорт сертификата в minikube: ``kubectl create secret tls lab3host-tls --cert=tls.crt --key=tls.key``
7) Cоздание ingress [ingress_3.yaml](ingress_3.yaml) в minikube, где указан ранее импортированный сертификат, FQDN и имя сервиса и его приминение: ``kubectl apply -f ingress.yaml``

Если вы делаете эту работу на Windows/macOS для доступа к ingress вам необходимо использовать команду minikbe tunnel к созданному ingress. Если вы делаете эту работу на Windows/macOS для доступа к ingress вам необходимо в hosts добавить ip address и ваш FQDN.

8) Прописываем в hosts FQDN и IP адрес вашего ingress: ``echo "$(minikube ip) lab3host.com" | sudo tee -a /etc/hosts``
9) Вход в веб приложение по FQDN используя HTTPS и проверка наличия сертификата.
