# prompt
♻️ DevOps &amp; Kubernetes

# prompts

YAML Kubernetes manifests with prompt

| NAME            | PROMPT                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | DESCRIPTION                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | EXAMPLE                                                  |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------- |
| app             | Create a Kubernetes deployment manifest for an app named "my-app". It should use the Docker image "nginx:1.19", have 2 replicas, expose port 8080, and include environment variables "ENV" set to "production" and "DEBUG" set to "false". Include a service to expose the app externally.                                                                                                                                                                                                                                                                                                       | Щоб створити app.yaml за допомогою Kubectl OpenAI plugin, важливо зазначити специфіку вашого додатка. Зазвичай це включає наступні дані: назва додатка, кількість реплік, образ, порти, які потрібно відкрити, інші ресурси, наприклад обсяг пам'яті та CPU                                                                                                                                                                                                                                                                                                               | [app.yaml](./yaml/app.yaml)                               |
| Liveness Probe  | Create a Kubernetes deployment manifest named "app-livenessProbe.yaml" for an app called "my-app". It should use the Docker image "nginx:latest", have 3 replicas, and include a livenessProbe that performs an HTTP GET request on path "/healthz" at port 8080. The liveness probe should start after 10 seconds, check every 5 seconds, and consider the container unhealthy after 3 consecutive failures.                                                                                                                                                                                    | Щоб створити app-livenessProbe.yaml з налаштуваннями liveness probe для Kubernetes, вам потрібно визначити, як Kubernetes перевірятиме, чи працює ваш додаток. Зазвичай це включає тип перевірки (наприклад, HTTP-запит або команду), інтервали перевірки і таймаути. В залежності від типу livenessProbe, потрібно чітко описати механізм перевірки і конфігураційні параметри (інтервали, кількість невдалих спроб до перезапуску контейнера тощо).                                                                                                                     | [app-livenessProbe.yaml](./yaml/app-livenessProbe.yaml)   |
| Readiness Probe | Create a Kubernetes deployment manifest named "app-readinessProbe.yaml" for an app called "my-app". It should use the Docker image "nginx:latest", have 2 replicas, and include a readinessProbe that runs the command "cat /tmp/ready". The probe should start after 10 seconds, check every 5 seconds, and mark the container ready after 1 successful execution of the command.                                                                                                                                                                                                               | Щоб створити app-readinessProbe.yaml для Kubernetes з налаштуванням readiness probe, потрібно описати, як Kubernetes перевірятиме готовність вашого додатка до прийняття трафіку. Це може включати перевірки через HTTP-запити, команди або TCP-з'єднання. Важливо зазначити параметри затримки (start time), частоти перевірок і кількість успішних спроб, необхідних для позначення контейнера як готового.                                                                                                                                                             | [app-readinessProbe.yaml](./yaml/app-readinessProbe.yaml) |
| Volume Mounts   | Create a Kubernetes deployment manifest named "app-volumeMounts.yaml" for an app called "my-app". It should use the Docker image "nginx:latest", have 2 replicas, and include a volume mount that uses a ConfigMap named "my-config" mounted at "/etc/config". The ConfigMap should contain the configuration files for the app.                                                                                                                                                                                                                                                                 | Щоб створити app-volumeMounts.yaml з налаштуваннями для підключення томів (volumes) у Kubernetes, потрібно визначити, які томи будуть підключатися до контейнера, а також їхні точки монтування. В залежності від типу даних, які ви хочете зберігати (наприклад, конфігураційні файли, секрети або дані), уточнюйте тип тому (ConfigMap, PVC, Secret) і точку монтування в контейнері.                                                                                                                                                                                   | [app-volumeMounts.yaml](./yaml/app-volumeMounts.yaml)     |
| cronjob         | Create a Kubernetes CronJob manifest named "app-cronjob.yaml" for an app called "backup-job". It should use the Docker image "alpine:latest" and run the command "tar -czf /backup/backup.tar.gz /data" every Sunday at 2:00 AM. Set the job to have a successful completion deadline of 300 seconds and keep 7 successful job history records.                                                                                                                                                                                                                                                  | Для створення app-cronjob.yaml вам потрібно описати специфіку Kubernetes CronJob, таку як частота виконання, ім'я додатка, Docker-образ, а також команда або скрипт, який повинен виконуватись за розкладом. У промпті слід вказати частоту виконання (у форматі cron), образ контейнера, який використовується, команду або скрипт, що виконується, а також будь-які додаткові налаштування, такі як дедлайни виконання і збереження історії робіт.                                                                                                                      | [app-cronjob.yaml](./yaml/app-cronjob.yaml)               |
| job             | Create a Kubernetes Job manifest named "app-job.yaml" for an app called "backup-job". It should use the Docker image "alpine:latest" and run the command "sh -c 'tar -czf /backup/backup.tar.gz /data'". The job should complete successfully within 300 seconds, and there should be no retries on failure.                                                                                                                                                                                                                                                                                     | Для створення app-job.yaml, потрібно описати однократну задачу в Kubernetes, яка запускається один раз або до завершення відповідно до вимог. Потрібно вказати Docker-образ, команду або скрипт, а також інші параметри, такі як кількість спроб (retries) або дедлайн виконання. В промпті потрібно зазначити, яку саме команду має виконати Job, Docker-образ для запуску, а також параметри, що контролюють кількість повторних спроб і дедлайн завершення.                                                                                                            | [app-job.yaml](./yaml/app-job.yaml)                       |
| multicontainer  | Create a Kubernetes Pod manifest named "app-multicontainer.yaml" for an app called "my-app". The pod should contain three containers: one for the frontend using the Docker image "nginx:latest" and exposing port 80, one for the backend using the Docker image "python:3.9-alpine" and exposing port 5000, and one for caching using the Docker image "redis:alpine". The frontend container should communicate with the backend container via internal networking, and the backend container should use Redis for caching. All containers should share a volume mounted at "/shared-config". | Для створення app-multicontainer.yaml, потрібно описати под із кількома контейнерами, які можуть взаємодіяти між собою. В такому промпті ви вказуєте кількість контейнерів, їхні Docker-образи, порти, і те, як ці контейнери повинні співпрацювати (наприклад, один контейнер може бути вебсервером, а інший — кешем або базою даних). Ці промпти описують кількість контейнерів, їхню взаємодію (наприклад, через загальні томи або мережу), порти, та інші конфігурації. Важливо зазначити, як контейнери мають взаємодіяти всередині поду.                            | [app-multicontainer.yaml](./yaml/app-multicontainer.yaml) |
| Resources       | Create a Kubernetes Pod manifest named "app-resources.yaml" for an app called "my-app". The pod should contain two containers: one using the Docker image "nginx:latest" and another using the Docker image "redis:alpine". For the nginx container, request 100m of CPU and 128Mi of memory, and limit it to 300m of CPU and 256Mi of memory. For the redis container, request 50m of CPU and 64Mi of memory, and limit it to 200m of CPU and 128Mi of memory.                                                                                                                                  | Для створення app-resources.yaml, потрібно визначити обмеження і запити на ресурси для вашого додатка в Kubernetes. Це включає виділення процесорного часу (CPU) і оперативної пам'яті (memory) для контейнерів у поді. Запити (requests) вказують мінімальну кількість ресурсів, яку контейнер повинен отримати, а ліміти (limits) встановлюють максимальну кількість ресурсів, яку він може використовувати. Ці промпти визначають необхідні ресурси для контейнерів, що дозволяє Kubernetes планувати і керувати подами відповідно до доступних ресурсів на кластерах. | [app-resources.yaml](./yaml/app-resources.yaml)           |
| Secret env      | Create a Kubernetes deployment manifest named "app-secret-env.yaml" for an app called "my-app". It should use the Docker image "nginx:latest" with 2 replicas, and include a secret named "my-secret" that contains sensitive data such as a database password. The secret should be mounted as environment variables in the container. The environment variable names should be "DB_PASSWORD", with the value coming from the key "db-password" in the secret.                                                                                                                                  | Для створення app-secret-env.yaml, ви повинні визначити, як секрети будуть використовуватися як змінні середовища в контейнері Kubernetes. Зазвичай це потрібно для зберігання конфіденційної інформації, такої як паролі, API-ключі тощо. Ці промпти визначають, як секрети будуть використовуватись як змінні середовища всередині контейнерів, що дозволяє зберігати конфіденційні дані окремо від коду та надавати їх додатку під час запуску.                                                                                                                        | [app-secret-env.yaml](./yaml/app-secret-env.yaml)         |

### Kubectl plugin to create manifests with LLMs

[GitHub](https://github.com/sozercan/kubectl-ai?tab=readme-ov-file#set-up-a-local-openai-api-compatible-endpoint)