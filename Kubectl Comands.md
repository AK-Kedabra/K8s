# Справочник по командам Kubectl
### kubectl get

- **Описание:** Используется для получения информации о ресурсах в кластере.
- **Пример:** `kubectl get pods`
- **Подфлаги:**
  - `-o` или `--output`: Определяет формат вывода (например, yaml, json).
  - `-n` или `--namespace`: Указывает пространство имен для запроса.

### kubectl describe

- **Описание:** Предоставляет подробную информацию о ресурсе.
- **Пример:** `kubectl describe pod <pod-name>`
- **Подфлаги:** Обычно не имеет особых подфлагов.

### kubectl create

- **Описание:** Создает ресурс из файла YAML или JSON.
- **Пример:** `kubectl create -f mypod.yaml`
- **Подфлаги:**
  - `-f` или `--filename`: Путь к файлу с описанием ресурса.

### kubectl apply

- **Описание:** Применяет изменения в конфигурации кластера, описанные в файлах YAML или JSON.
- **Пример:** `kubectl apply -f mypod.yaml`
- **Подфлаги:**
  - `-f` или `--filename`: Путь к файлу с описанием ресурса.

### kubectl delete

- **Описание:** Удаляет ресурсы.
- **Пример:** `kubectl delete pod <pod-name>`
- **Подфлаги:**
  - `--grace-period`: Определяет период ожидания перед удалением (по умолчанию 30 секунд).

### kubectl exec

- **Описание:** Запускает команду внутри контейнера пода.
- **Пример:** `kubectl exec -it <pod-name> -- /bin/bash`
- **Подфлаги:**
  - `-it` или `--stdin --tty`: Обеспечивает интерактивный режим терминала.

### kubectl logs

- **Описание:** Показывает логи контейнера внутри пода.
- **Пример:** `kubectl logs <pod-name>`
- **Подфлаги:**
  - `-f` или `--follow`: Отслеживает логи в режиме реального времени.

### kubectl scale

- **Описание:** Изменяет количество реплик ресурса.
- **Пример:** `kubectl scale deployment <deployment-name> --replicas=3`
- **Подфлаги:** Обычно включает имя ресурса и количество реплик.

### kubectl rollout

- **Описание:** Управляет процессом развертывания (rolling update).
- **Пример:** `kubectl rollout status deployment <deployment-name>`
- **Подфлаги:** Включает подкоманды, такие как `status`, `history`, `undo`, и др.

### kubectl port-forward

- **Описание:** Пробрасывает сетевые порты между локальной машиной и подом в кластере.
- **Пример:** `kubectl port-forward <pod-name> 8080:80`
- **Подфлаги:** Указывает порты для проброса.

### kubectl apply -f -

- **Описание:** Применяет конфигурацию из стандартного ввода.
- **Пример:** `cat mypod.yaml | kubectl apply -f -`
- **Подфлаг:** `-f -` указывает kubectl прочитать конфигурацию из стандартного ввода.


### Получить список чего либо
- $ kubectl get services - Получение списка service
- kubectl get pods - Получение списка pods
- kubectl get deployments - Получение списка deployments

### Применение Deployment с сохранением истории, флаг --record=true. По умолчанию стоит --record=false
    $ kubectl apply deployment -f .\deployment.yml --record=true 

### История ревизии 
    $ kubectl rollout history deployment my-deployment

### История изменений по номеру ревизии
    $ kubectl rollout history deployment my-deployment --revision=2

### Откат изменений
    $ kubectl rollout undo deployment my-deployment 

### Откат изменений на определенную ревизию 
    $ kubectl rollout undo deployment my-deployment --to-revision=1

### Статус Отката
    $ kubectl rollout status deployment my-deployment

### После создания Service появляется еще одна сушьность Endpoint с внешним IP Кластера
    $ kubectl get endpoint

### Контейнер внутри кластера со всеми нужными сетевыми программами 
    $ kubectl -run --rm -it --image amount/network-utils test bash
    curl по внутреннему адресу, можно по адресу кластера или названию сервиса


