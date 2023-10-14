University: [ITMO University](https://itmo.ru/ru/)\
Faculty: [FICT](https://fict.itmo.ru)\
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)\
Year: 2023/2024\
Group: K4111c\
Author: Sulimenko Nikita Sergeevich\
Lab: Lab2\
Date of create: 13.10.2023\
Date of finished: -

___

1) Создание [deployment]() с 2 репликами контейнера ifilyaninitmo/itdt-contained-frontend:master, установка переменных в эти реплики и создание сервиса для доступа к подам: 
REACT_APP_USERNAME, REACT_APP_COMPANY_NAME: ``kubectl apply -f lab2_deployment.yaml``
2) Получение имен созданных контейнеров: ``kubectl get pods``
3) Запуск режима проброса портов: ``kubectl port-forward <pod_name> 3001:3000``
4) Смотрим через браузер веб-интерфейс:
<img width="1225" alt="lab2" src="https://github.com/kitok07/2023_2024-introduction_to_distributed_technologies-K4111c-sulimenko_n_s/assets/147832281/702bd6eb-f2d4-40a7-8e4b-83162c7f5d99">
5) Смотрим логи контейнеров: ``kubectl logs <pod_name>``
<img width="520" alt="lab2_2" src="https://github.com/kitok07/2023_2024-introduction_to_distributed_technologies-K4111c-sulimenko_n_s/assets/147832281/9457f448-6da7-47f0-92d3-e086ce436b9b">


