# Атрибуты Deployment

- **apiVersion:** Указывает на версию API, используемую для этого ресурса. В данном случае, `apps/v1`.

- **kind:** Указывает на тип ресурса. Для развертывания (Deployment) это `Deployment`.

- **metadata:** Содержит метаданные ресурса, такие как имя.

- **spec:** Содержит спецификации развертывания.

  - **replicas:** Задает количество желаемых реплик (копий) подов.

  - **selector:** Определяет, какие поды должны участвовать в Deployment.

    - **matchLabels:** Указывает на метки, которые должны соответствовать меткам подов, чтобы они были учтены в Deployment.

  - **template:** Определяет шаблон для создания подов.

    - **metadata:** Содержит метаданные для пода.

      - **labels:** Указывает на метки, которые будут присвоены создаваемым подам.

    - **spec:** Содержит спецификации пода.

      - **containers:** Определяет контейнеры, которые должны быть запущены в поде.

        - **name:** Указывает на имя контейнера.

        - **image:** Указывает на образ контейнера.

        - **ports:** Определяет порты, которые контейнер будет использовать.

          - **containerPort:** Порт контейнера, который будет открыт для трафика.
