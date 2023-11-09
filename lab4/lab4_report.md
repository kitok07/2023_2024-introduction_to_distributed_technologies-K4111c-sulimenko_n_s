University: [ITMO University](https://itmo.ru/ru/)\
Faculty: [FICT](https://fict.itmo.ru)\
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)\
Year: 2023/2024\
Group: K4111c\
Author: Sulimenko Nikita Sergeevich\
Lab: Lab4\
Date of create: 13.10.2023\
Date of finished: -

___
1) Запуск Minikube с плагином CNI Calico и в режиме Multi-Node Clusters: ``minikube start --cni=calico --nodes=2``
2) Проверка работы CNI плагина Calico и количество нод командами:
- ``kubectl get nodes``
- ``kubectl get pods -n kube-system -l k8s-app=calico-node``
<img width="564" alt="image" src="https://github.com/kitok07/2023_2024-introduction_to_distributed_technologies-K4111c-sulimenko_n_s/assets/147832281/96ad93ea-283d-442a-a7f0-d14611bcade3">

Для проверки IPAM (IP Address Management), назначим метки узлам. Присвоем метку географического расположения: location=us-east и location=us-west, для соответсвующих нод.\
``kubectl label nodes <узел_1> location=us-east``\
``kubectl label nodes <узел_2> location=us-west``

3) Создадим манифест для Calico, определяющий IP-пулы в соответствии с метками узлов: [ippool.yaml]()

4) Создадим манифест для Deployment с необходимыми переменными окружения: [deployment.yaml]()
