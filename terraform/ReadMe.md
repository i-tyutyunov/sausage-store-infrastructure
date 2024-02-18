# Создание ВМ

## Зависимости
Terraform v1.5.7

## Описание

Перед запуском обязательно, на машине с браузером, сгенерируйте токен для доступа к облаку (команда `yc iam 
create-token`) и полученный токен запишите в переменную `token` (файл `/terraform/terraform.tfvars`).

Состоит из 2х модулей:
1. tf-yc-instance - создание ВМ;
2. tf-yc-network - получение данных о сети, которые используются в модуле `tf-yc-instance`.

## Запуск

### Настройка подключения к хранилищу состояния
Создаём файл `./terraform/secret.backend.auto.tfvars` и объявляем в нём ключи от сервисного аккаунта, у которого есть 
доступ к хранилищу:
1. secret_key;
2. access_key.

### Запуск terraform init

В параметрах запуска указываем файл с ключами для подключения к хранилищу
`terraform init -backend-config=secret.backend.auto.tfvars`

### Запуск terraform plan/init

Перед запуском необходимо создать файл `./terraform/secret.provider.auto.tfvars` и задать в нём значение для 
переменной `token`. В этой переменной должен хранится токен для доступа к облаку.

`terraform init -auto-approve`