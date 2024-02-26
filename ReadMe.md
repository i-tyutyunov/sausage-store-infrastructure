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

### Запуск
_Перед запуском нужно выяснить IP виртуальной машины, которую создал Terraform. Полученный ip нужно передать в `ansible/inventory.yaml`_

```shell
 ansible-playbook playbook.yaml -e "@nexus_access_data.yml" --vault-password-file=vault_password
```