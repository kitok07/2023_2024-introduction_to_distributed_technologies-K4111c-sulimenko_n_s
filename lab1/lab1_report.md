University: [ITMO University](https://itmo.ru/ru/)
Faculty: [FICT](https://fict.itmo.ru)
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)
Year: 2023/2024
Group: K4111c
Author: Sulimenko Nikita Sergeevich
Lab: Lab1
Date of create: 13.10.2023
Date of finished: -

___

### Предварительная подготовка
1) Установка [minicube](https://minikube.sigs.k8s.io/docs/start/)
2) Запуск: ``minicube start``.\
Minikube запустит одноузловой кластер Kubernetes, используя автоматически выбранный драйвер.
3) Установка kubectl: ``minikube kubectl``

### Основная часть
1) Создание манифеста [vault-pod.yaml]()\
В манифесте указан образ контейнера Vault и порт, который нужно прокинуть внутрь контейнера.
2) Применение манифеста для создания пода Vault: ``minikube kubectl -- apply -f vault-pod.yaml``
3) Создание cервиса для досутпа к поду: ``minikube kubectl -- expose pod vault --type=NodePort --port=8200`` 
4) Проброс портов: ``minikube kubectl -- port-forward service/vault 8200:8200``
5) Получение кредов для входа в Vault: ``minikube kubectl -- logs vault``\
Ищем строку с **Root Token**.
6) Выполняем вход через открытый к сервису порт (п. 3-4) по адресу http://127.0.0.1:8200 и используя токен (п. 5)
<img width="592" alt="image" src="https://github.com/kitok07/2023_2024-introduction_to_distributed_technologies-K4111c-sulimenko_n_s/assets/147832281/85043c89-b55d-4c35-b4b3-1826adde2fac">

### Завершение
1) Удаление пода: ``minikube kubectl -- delete pod vault``
2) Удаление сервиса:  ``minikube kubectl -- delete service vault``
3) Останавливка работы кластера: ``minikube stop``

### Схема организации контейеров и сервисов
<img width="544" alt="image" src="https://github.com/kitok07/2023_2024-introduction_to_distributed_technologies-K4111c-sulimenko_n_s/assets/147832281/7fb9603b-22df-4112-a535-389047c59ac9">\
[Ссылка](https://drive.google.com/drive/folders/12NbINUiqkI9iRPy5nM3f-LhXHdc2Jd9T?usp=sharing) для редактирование схемы
