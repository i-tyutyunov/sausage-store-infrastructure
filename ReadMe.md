# Быстрый старт

## Terraform

### Организация доступа к хранилищу состояния

1. Создаём файл `terraform/secret.backend.auto.tfvars`
2. Объявляем в нём 2 переменные для доступа к хранилищу состояния terraform:
   1. access_key
   2. secret_key

### Организация доступа к облаку

1. Создём файл `terraform/secret.provider.auto.tfvars`;
2. Объявляем в файле, из п.1, переменную `token` в которую записываем токен для доступа к облаку.

### Запуск

1. `terraform init -backend-config=secret.backend.auto.tfvars`
2. `terraform apply`

## Ansible

### Организация доступа к Nuxus

1. Создаём файл `ansible/secret.yml`;
2. Объявляем в файле, из п.1, переменные для доступа к Nexus:
   _даю свои доступы для простоты проверки задания_
```yaml
nexus_login: admin
nexus_password: JN2-7ce-yZ8-bvz
```

### Запуск
_Перед запуском нужно выяснить IP виртуальной машины, которую создал Terraform. Полученный ip нужно передать в 
переменную `mv_sausage_store_ip` при запуске `ansible-playbook`_

```shell
ansible-playbook playbook.yaml -e "@secret.yml" -e "mv_sausage_store_ip=<ip>"
```