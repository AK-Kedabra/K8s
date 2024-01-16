## Атрибуты Services

1. apiVersion: Указывает на версию API, используемую для этого ресурса. В данном случае, v1.

2. kind: Указывает на тип ресурса. Для службы (Service) это Service.

3. metadata: Содержит метаданные ресурса, такие как имя.

4. spec: Содержит спецификации службы.

    1. selector: Определяет, какие поды должны быть связаны с этой службой.
        1. app: my-app: Это метка, которую поды должны иметь, чтобы быть связанными с этой службой.
    
    3. ports: Определяет порты для службы.
        1. protocol: Протокол передачи данных (TCP, UDP и т. д.).
        2. port: Порт службы, который будет открыт для внешнего доступа.
        3. targetPort: Порт контейнера в подах, к которому будет направлен трафик.

11. type: Тип службы, указывающий на способ предоставления доступа к подам.

    1. ClusterIP: Служба будет доступна только внутри кластера.

    2. NodePort: Открывает указанный порт на каждом узле кластера.

    3. LoadBalancer: Создает балансировщик нагрузки в облачной среде и предоставляет внешний IP-адрес.

    4. ExternalName: Служба предоставляется внешнему объекту по имени.