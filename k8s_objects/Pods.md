# Pod:

### Пример

    apiVersion: v1                 - Версия API
    kind: Pod                      - Тип сущьности
    metadata:                      - Метаданные
        name: my-pod               - Название пода
        namespace: default         - Пространство имен
        labels:
            name: nginx
    spec:                          - Спецификация
        containers:
            - name: nginx
              image: nginx         - Испотьзуемы Image для Pods
              ports:
                - containerPorts: 80