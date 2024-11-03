# INFO
1. Предварительные настройки: установка ансибл на VM - добавлен в скрипт vagrant, мапинг текущей директории 
2. ``vagrunt up``
3. Залогиниться ``vagrunt ssh ubuntu`` || ``vagrunt ssh centos``
4. Перейти в директорию ``cd ansible``
5. Установить зависимые роли и коллекции ``ansible-galaxy install -r requirements.yml``
6. Проверить/задать необходимые переменные ``vars/semaphore.yml``
7. Выполнить накат плейбука ``ansible-playbook play-semaphore.yml``
8. При успешной установки, зайти на страницу http://192.168.50.4/ (ip ubuntu) || http://192.168.50.5/  (ip centos)  - login/pass см. ``vars/semaphore.yml``

* !!! 
```
Выполнены все задания, в том числе и повышенной сложность. 
Но проверка осуществлялось только на arm архитектуре, на другой нет возможности
Данный плейбук необходимо использовать только для ознакомительных целях, так как например не предуспотренно SSL поддключение и другие важные факторы и параметры
```



# Практикум по Ansible:
## Цель: 
 закрепление материала, полученного в курсе по ansible, получение практического опыта написания и использования ролей.

## Ожидаемый результат: 
реализованная роль для установки и настройки сервиса ansible semaphore. В качестве ответа вставьте ссылку на публичный git репозиторий с ролями и плейбуками ansible.

## Задание: 

* ОС Ubuntu (версия 20.04 или выше), Centos и др.\
  **_Примечаение_**: если используется отличная от указанных ОС, в заметках указать как скачать образ для Vagrant.

* Приложение https://semaphoreui.com, реализовать запуск через docker container или через systemd.service на выбор. Файлы для systemd.service уже есть на git, ссылка в практических рекомендациях. Приложение должно автоматически запускаться после перезагрузки машины.

* Заменить БД на PostgreSQL (базово приложение использует MySQL). Роль для PostgreSQL взять из ansible-galaxy, создать базу, настроить пользователя и права (перевод приложения на PostgreSQL также описан по ссылке в Практических рекомендациях) 

### Повышенная сложность:

* Расширить роль настройки до работы со второй ОС, отличной от той которая была использована, например: чтобы роль подходила как для настройки Ubuntu, так и для Centos

* Реализовать запуск приложения именно через systemd.service

* Подготовить собственную ansible роль для PostgreSQL. Роль должна включать в себя установку и настройку PostgreSQL, создание пользователя с паролем и базу данных для приложения.

* Запустить приложение в несколько процессов(2 и больше). 
* Установить балансировщик NGINX или Haproxy. Роль для балансировщика нужно взять из набора Galaxy.

*_Задание повышенной сложности выполняется по вашему желанию_

## Практические рекомендации: 

* [systemd unit and environment file](https://github.com/semaphoreui/semaphore/tree/develop/deployment/systemd)

* [Собранный .deb пакет приложения](https://semaphoreui.com/install)

* [Релизные версии semaphore](https://github.com/semaphoreui/semaphore/releases)

* [Установка Ansible Semaphore в Rocky Linux(с использованием PostgreSQL)](https://itdraft.ru/2023/02/02/ustanovka-ansible-semaphore-v-rocky-linux/)

## Дополнительные материалы:

* [Semaphore (ansible UI) в kubernetes(youtube, RUS)](https://www.youtube.com/watch?v=9TOUdULKn2s)

* [This web UI for Ansible is so damn useful!](https://youtu.be/NyOSoLn5T5U)

* [Ansible Semaphore Installation & Setup | Web UI for Ansible](https://www.youtube.com/watch?v=UCy4Ep2x2q4)