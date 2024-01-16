# Справочник по командам Kubectl

## Получить список чего либо
- $ kubectl get services - Получение списка service
- kubectl get pods - Получение списка pods
- kubectl get deployments - Получение списка deployments

## Применение Deployment с сохранением истории, флаг --record=true. По умолчанию стоит --record=false
    $ kubectl apply deployment -f .\deployment.yml --record=true 

## История ревизии 
    $ kubectl rollout history deployment my-deployment

## История изменений по номеру ревизии
    $ kubectl rollout history deployment my-deployment --revision=2

## Откат изменений
    $ kubectl rollout undo deployment my-deployment 

## Откат изменений на определенную ревизию 
    $ kubectl rollout undo deployment my-deployment --to-revision=1

## Статус Отката
    $ kubectl rollout status deployment my-deployment

## После создания Service появляется еще одна сушьность Endpoint с внешним IP Кластера
    $ kubectl get endpoint

## Контейнер внутри кластера со всеми нужными сетевыми программами 
    $ kubectl -run --rm -it --image amount/network-utils test bash
    curl по внутреннему адресу, можно по адресу кластера или названию сервиса


