# ДЗ №1 (Знакомство с решениями для запуска локального Kubernetes кластера, создание первого pod)

 - [ ] Разберитесь почему все pod в namespace kube-system восстановились после удаления.
 - [ ] Созать web-pod.yaml при применении которого будет запущен init контейнер, создающий страничку и контейнер с nginx , открывающий эту страничку при запросе
 - [ ] * сделать  frontend-pod-healthy.yaml запускающий без ошибок frontend


## Решение ДЗ:

 -  Поды etcd apiserver controller-manager scheduler восстанавливаются, поскольку они содержаться в локальных манифестах кубера
``` 
root@k8s-master:~# tree /etc/kubernetes/manifests/
/etc/kubernetes/manifests/
├── etcd.yaml
├── kube-apiserver.yaml
├── kube-controller-manager.yaml
└── kube-scheduler.yaml
```
Запускает их демон  kubelet
``` 
root@k8s-master:~# systemctl status kubelet
● kubelet.service - kubelet: The Kubernetes Node Agent
     Loaded: loaded (/lib/systemd/system/kubelet.service; enabled; vendor preset: enabled)
    Drop-In: /etc/systemd/system/kubelet.service.d
             └─10-kubeadm.conf
     Active: active (running)

``` 	 
Остальные поды восстанавливает тоже kubelet, но их манифесты он берет уже с apiserver

 - web-pod.yaml создан по инструкциям
 - frontend-pod-healthy.yaml нужно создать с учетом ENV переменных


# ДЗ №2 (Механика запуска и взаимодействия контейнеров в Kubernetes)

 - [ ] Создать файлы манифестов RS Deploment и Daemonset
 - [ ] * Релизовать blue-green и Reverse Rolling Update
 - [ ] ** Сделать Daemonset запускаемым на мастер ноде


## Решение ДЗ:

 -  yaml файлы созданы ))
 -  Сделал blue-green и Reverse Rolling Update так

blue-green:
```
      maxSurge: 3
      maxUnavailable: 0
```

Reverse Rolling Update :
```
      maxSurge: 0
      maxUnavailable: 1
```
 -  Сделал Daemonset запускаемым на мастер ноде так
```
      tolerations:
      - operator: Exists
```


# ДЗ №3 (Безопасность и управление доступом )

 - [ ] Сделать согласно описанию 3 таски



## Решение ДЗ:

 -  yaml файлы созданы ))


# ДЗ №4 (Хранение данных в Kubernetes: Volumes, Storages, Statefull-приложения)

 - [ ] Сделать согласно описанию 2 yaml
 - [ ] Дополнительное задание - сделать secret и использовать его в statefullset

## Решение ДЗ:

 -  yaml файлы созданы ))
 -  доп задание сделано
