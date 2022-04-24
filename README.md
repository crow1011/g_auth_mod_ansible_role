# g_auth_mod_ansible_role
Ansible role for Google Authenticator PAM module

__Это решение тестового задания__

Эта роль ansible настраивает Google Authenticator PAM module для Ubuntu server 20.04

### Шаг 1
Создайте файл hosts.txt в корне проекта и заполните его по правилам ansible, либо измените inventory в ansible.cfg

### Шаг 2
Создайте виртуальное окружение и установите ansible
```bash
virtualenv venv
pip install -r requirements.txt
```
### Шаг 3
Заполните списки пользователей в `g_auth_mod/vars/main`:
 - users_for_create - пользователи, которые будут созданы
 - users_for_destroy - пользователи, которые будут удалены
 - users_for_turn_off_gauth - пользователи для которых будут сброшены настройки Google Authenticator PAM module 

Добавьте публичные ключи для создаваемых пользователей в `g_auth_mod/files/{username}.pub` 

## Шаг 4 
Запустите плейбук `pb.yaml`
```bash
ansible-playbook pb.yaml
```
____
При первом входе каждый пользователь получит qr-код для настройки Google Authenticator и коды восстановления. Для пользователя ansible проверка по коду верификации будет отключена.

