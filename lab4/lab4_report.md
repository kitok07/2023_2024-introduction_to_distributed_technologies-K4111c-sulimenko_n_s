University: [ITMO University](https://itmo.ru/ru/)\
Faculty: [FICT](https://fict.itmo.ru)\
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)\
Year: 2023/2024\
Group: K4111c\
Author: Sulimenko Nikita Sergeevich\
Lab: Lab4\
Date of create: 9.11.2023\
Date of finished: 16.11.2023

___
1) Запуск Minikube с плагином CNI Calico и в режиме Multi-Node Clusters: ``minikube start --cni=calico --nodes=2``
2) Проверка работы CNI плагина Calico и количество нод командами:
- ``kubectl get nodes``
- ``kubectl get pods -n kube-system -l k8s-app=calico-node``
<img width="564" alt="image" src="https://github.com/kitok07/2023_2024-introduction_to_distributed_technologies-K4111c-sulimenko_n_s/assets/147832281/96ad93ea-283d-442a-a7f0-d14611bcade3">

Для проверки IPAM (IP Address Management), назначим метки узлам. Присвоем метку географического расположения: location=us-east и location=us-west, для соответсвующих нод.\
``kubectl label nodes <узел_1> location=us-east``\
``kubectl label nodes <узел_2> location=us-west``

3) Создадим манифест для Calico, определяющий IP-пулы в соответствии с метками узлов: [ippool.yaml](ippool.yaml)

4) Создадим манифест для Deployment с необходимыми переменными окружения: [deployment.yaml](deployment.yaml)
5) Установим calicoctl: ``kubectl create -f calicoctl.yaml``
6) Создадим IP пулы с помощью calicoctl в поде: ``kubectl exec -i -n kube-system calicoctl -- /calicoctl create -f - < ippool.yaml --allow-version-mismatch``
7) Выводим информацию о IP пулах через calicoctl: ``kubectl exec -i -n kube-system calicoctl -- /calicoctl get ippool -o wide   --allow-version-mismatch``
<img width="831" alt="image" src="https://github.com/kitok07/2023_2024-introduction_to_distributed_technologies-K4111c-sulimenko_n_s/assets/147832281/8d090eb8-2ff8-42e5-be40-749788895ac7">

9) Открываем доступ к сервису Minikube: ``minikube service frontend-service``
10) Пробрасываем порты сервиса на локальную машину: ``kubectl port-forward service/frontend-service 9090:9090``
<img width="853" alt="image" src="https://github.com/kitok07/2023_2024-introduction_to_distributed_technologies-K4111c-sulimenko_n_s/assets/147832281/f0a483cf-b5fe-40a6-83fb-343b2e674375">

11) Получим IP одного из контейнеров и пропингуем из другого:
- ``kubectl get pods -o wide``
- ``kubectl exec -it frontend-6844569ff8-7bcm9 -- /bin/sh``
- ``ping 10.244.205.193``
<img width="791" alt="image" src="https://github.com/kitok07/2023_2024-introduction_to_distributed_technologies-K4111c-sulimenko_n_s/assets/147832281/b94631ee-d9c7-4bc6-88fe-322d65db36cb">

___

### Схема

<img width="497" alt="image" src="https://github.com/kitok07/2023_2024-introduction_to_distributed_technologies-K4111c-sulimenko_n_s/assets/147832281/1957143e-8e9c-4113-87e8-92941f7a0c9a">
