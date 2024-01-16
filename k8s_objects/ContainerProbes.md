

### Пример
- Проверка готовности контейнера

        containers:
          - name: nginx
            image: nginx:1.13
           ports:
             - containerPort: 80
            readinessProbe:
              httpGet:
                path: /
                port: 80
              periodSeconds: 2
             failureThreshold: 3
             successThreshold: 1
             timeoutSeconds: 1

- Проверка работоспособности

        livenessProbe:
          httpGet:
           path: /
           port: 80
          periodSeconds: 10
          failureThreshold: 3
          successThreshold: 1
          timeoutSeconds: 1
          initialDelaySeconds: 10

            
