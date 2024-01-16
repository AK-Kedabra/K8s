# Service - Типы сервисов
## Без селектора
Можно не заполнять поле Selector, но придется создавать endpoints отдельно, создание Service для некой службы из вне
### Пример

    apiVersion: v1                                                      apiVersion: v1
        kind Service                                                        kind Service
        metadata:                                                           metadata:
            name: my-postgresql                                                 name: my-postgresql
            namespace: default                                                  namespace: default
        spec:                                                               subsets:
            ports:                                                              - addresses:
                - protocol: rcp                                                     - ip: 192.0.2.42 # К примеру база в не K8s
                  port: 5432                                                      ports:
                  targetPort: 5432                                                  - port: 5432



## ClusterIP
Используется по умолчанию, Сервису выделяется отдельный IP внутри кластера. Так как ip внутри кластера c снаружи кластера доступа нет,
Но можно предоставить с помошью proxy $ kubectl proxy --port=8080



## NodePort
Сервису выделяется IP внутри кластера по аналогии с clusterIp и на каждом узле кластера открывается порт из диапазона (30 000 - 32 767)
Который пробрасывается на предоставленный внутренний Ip кластера
 
apiVersion: v1
kind: Service
metadata:
    name: my-Service
spec:
    type: NodePort
    selector:
        app: my-app
    ports:
        - port: 80
        targetport: 80
        NodePort: 30000





## LoadBalancer
Использует внешний балансировщик (внешний IP) как правило облачный провайдер
Внешний балансировщик направляет запросы на nodePort и clusterIP, который создается автоматически
Для каждого сервиса надо запрашивать отдельный внешний IP адрес

### Пример
    $ kubectl apply -f 07_service_load_balancer.yml
        sevice/my-service-load-balancer created

    $ kubectl get services




## ExtenalName
Перенаправляет трафик на указанный ExternalName например (foo.bar.example.com)
По сути разновидность Сервиса без Селектора, в Endpoints у которого указано другое DNS имя

### Пример
    apiVersion: v1
    kind: Service
    metadata:
        name: my-serrvice
    spec:
        type: ExternalName
            ExtenalName: my.data.base.example.com