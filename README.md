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

