# Запуск

## Настройка перед запуском

### Настройка подключения к Nexus

Ansible скачивает артефакты приложения из Nexus.
Адрес Nexus задаётся в переменной `nexus_url` (файл `ansible/group_vars/all.yml`).

Для авторизации в Nexus нужно объявить переменные:
1. `nexus_login`
2. `nexus_password`


Эти переменные можно записать в файл `secret.yml`

_**PS:** напишу тут доступы от Nexus для упрощения процесса проверки задания.
Само собой я понимаю, что в реальном проекте хранить доступы в репозитории - **недопустимо**._
```yaml
nexus_login: admin
nexus_password: JN2-7ce-yZ8-bvz
```

С помощью переменных:
1. `nexus_backend_repository_path`
2. `nexus_frontend_repository_path`

Можно управлять расположение репозитория в Nexus.

### Указание версий

Версия бэкенда указывается в переменной: `backend_maven_version`
Версия фронтенда указывается в переменной: `frontend_version`

### Задать IP адрес ВМ к которой будет подключаться ansible

Перед тем, как запускать ansible-playbook, необходимо выяснить IP-адрес ВМ на которой будет работать приложение.
IP адрес должен быть задать в переменной `mv_sausage_store_ip`.

## Запуск
ansible-playbook playbook.yaml -e "@secret.yml" -e "mv_sausage_store_ip=178.154.207.241"