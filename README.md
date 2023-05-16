> _kubernetes-intro_
<details>
  <summary>ДЗ №1: Настройка локального окружения. Запуск первого контейнера.Работа с kubectl</summary>
### Задание 1
Разберитесь почему все pod в namespace kube-system восстановились после удаления. Укажите причину в описании PR

`core-dns`- контроллер ReplicaSet создает новый pod при его отсутствии.

`kube-proxy` - контроллер DaemonSet создает новый pod при его отсутствии 

`etcd-minikube`,`kube-controller-manager-minikube``kube-apiserver`,`kube-scheduler-minikube`- управляются Node/minikube.

### Задание 2
- создан Dockerfile для nginx
- создан манифест web-pod.yaml

### Задание 3 (Задание со *)
- создан манифест frontend-pod-healthy.yaml в котором добавлены необходимые переменные
</details>

> _kubernetes-controllers_
<details>
  <summary>ДЗ №2: Kubernetes controllers.ReplicaSet, Deployment,DaemonSet</summary>
### Задание 1
- применен манифест replicaset для frontend, отсутствовал раздел selector, манифест дополнен
### Задание 2
- изменен образ приложения в манифесте.
- приминен обновленный манифест.
- Вопрос: почему поды не пересоздались? Ответ: потому что replicaset следит только за количеством запущенных подов.
### Задание 3
- создан и применен манифест для replicaset и deployments микросервиса paymentService
### Задание 4 (Задание со *)
- созданы два манифеста blue-green и Reverse Rolling Update
### Задание 5
- создан манифест deployment для frontend с пробами
### Задача 6 (Задание со **)
- создан манифест DaemonSet для node-exporter, доплнен условием для развертывания на master нодах
</details>