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
1) Cоздание configMap [configMap_3.yaml]() с переменными: REACT_APP_USERNAME, REACT_APP_COMPANY_NAME.
2) Cоздание replicaSet [replicaSet_3.yaml]() с 2 репликами контейнера **ifilyaninitmo/itdt-contained-frontend:master** и используя configMap (п.1) передаем переменные REACT_APP_USERNAME, REACT_APP_COMPANY_NAME.
3) Включение minikube addons enable ingress:
4) Генирация TLS сертификата:
5) Импорт сертификата в minikube:
6) Cоздание ingress в minikube, где указан ранее импортированный сертификат, FQDN и имя сервиса (п Х).

Если вы делаете эту работу на Windows/macOS для доступа к ingress вам необходимо использовать команду minikbe tunnel к созданному ingress. Если вы делаете эту работу на Windows/macOS для доступа к ingress вам необходимо в hosts добавить ip address и ваш FQDN.
8) Прописываем в hosts FQDN и IP адрес вашего ingress:
9) Вход в веб приложение по FQDN (п X) используя HTTPS и проверка наличия сертификата.
