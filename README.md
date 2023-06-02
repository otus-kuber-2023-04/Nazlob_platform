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

> _kubernetes-networks
<details>
  <summary> ДЗ №3: Настройка сетевой связности для приложения. Добавление service, ingress. Установка MetalLB</summary>
### Задание №1
- настроен и применен web-pod.yaml
- вопрос: Почему следующая конфигурация валидна, но не имеет смысла?
~~~yaml
livenessProbe:
  exec:
    command:
      - 'sh'
      - '-c'
      - 'ps aux | grep my_web_server_process'
- Ответ: всегда возвращает 0, так как в выводе всегда есть сам grep. Можно поправить, добавив grep в исключения: | grep -v grep

### Задание №2
- создан и настроен манифест deployment web-deploy.yaml для web
- создан и настроен манифест services web-svc-cip.yaml

### Задание №3
- включен режим ipvs в minikube

### Задание №4
- установлен MetalLB
- настроен балансировщик metallb-config.yaml web-svc-lb.yaml

### Задание №5 (Задание со *)
- создан манифест сервиса coredns/dns-svc-metallb.yml

### Задание №6
- задеплоен ingress-nginx
- создан nginx-lb.yaml
- создан headless-сервис web-svc-headless.yaml
- создан ingress-proxy web-ingress.yaml

### Задание №7 (Задание с **)
- задеплоен Dashboard kube-dashboard.yaml
- создан и задеплоен манифест dashboard-ingress.yaml

### Задание №8 (Задание с **)
- манифесты в ./canary
</details>

> _kubernetes-networks
<details>
  <summary> ДЗ №4: Volumes, Storages,StatefulSet</summary>
  
### Задание №1
- применен minio-statefulset.yaml
- применен minio-headlessservice.yaml

### Задание №2
- создан и применен манифест секретов (base64 кодировка) secrets-minio.yaml
- minio-statefulset.yaml настроен на использование секретов
</details>

> _kubernetes-security
<details>
  <summary> ДЗ №5: Security</summary>
  
### Задание №1
- создан и применен манифест для sa bob с привязкой роли admin для всего кластера: 01_sa-bob-cluster-admin.yaml
- создан и применен манифест для sa dave: 02_sa-dave-na.yaml

### Задание №2
- создан и применен манифест для создания ns prometheus: 01_ns-prometheus.yaml
- создан и применен манифест для создания sa carol в ns prometheus: 02_sa-carol.yaml
- создан и применен манифест для  возможности всем Service Account в Namespace prometheus делать get , list , watch в отношении Pods всего кластера: 03_cr-bindings.yaml

### Задание №3
- создан и применен манифест для создания ns dev: 01_ns-dev.yaml
- создан и применен манифест для создания sa jane в ns dev: 02_sa-jane.yaml
- создан и применен манифест для sa jane с привязкой роли admin в рамках Namespace dev: 03_sa-jane-admin-role.yaml
- создан и применен манифест для создания sa ken в ns dev: 04_sa-ken.yaml
- создан и применен манифест для sa ken с привязкой роли view в рамках Namespace dev: 05_sa-ken-view-role.yaml

</details>

> _kubernetes-monitoring
<details>
  <summary> ДЗ №6: Monitoring</summary>
### Задание
- развернут клстер KIND
- развернут helm chart prometheus: helm install kind-prometheus prometheus-community/kube-prometheus-stack
- создан и запушен образ nginx с конфигом метрик
- создан и задеплоен манифест deployments для nginx и nginx-exporter
- создан и задеплоен манифест service для nginx и nginx-export
- создан и задеплоен манифест ServiceMonitor prometheus для получения метрик с nginx-exporter
- зашли в грфану - настроили дашборд с графиками для nginx (grafana.png)
</details>

