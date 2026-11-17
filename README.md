# lighthouse-role

Ansible-роль для установки веб-сервера Nginx и развёртывания интерфейса LightHouse для ClickHouse.

## Требования

- Целевая ОС: CentOS / Rocky Linux / RHEL.
- Наличие пакета `git` на целевом хосте (устанавливается через `pre_tasks` в playbook).

## Переменные роли

### Переменные по умолчанию (`defaults/main.yml`)

| Переменная | Значение по умолчанию | Описание |
| :--- | :--- | :--- |
| `lighthouse_vcs` | `"https://github.com"` | Ссылка на Git-репозиторий LightHouse |
| `lighthouse_location_dir` | `"/var/www/lighthouse"` | Директория размещения файлов LightHouse |
| `lighthouse_access_log_name` | `"lighthouse_access"` | Имя файла лога доступа Nginx |

### Внутренние переменные (`vars/main.yml`)

| Переменная | Описание |
| :--- | :--- |
| `nginx_user_name` | Имя системного пользователя веб-сервера Nginx |

## Пример использования

```yaml
---
- name: Install Lighthouse
  hosts: lighthouse
  pre_tasks:
    - name: Install git
      become: true
      ansible.builtin.yum:
        name: git
        state: present
  roles:
    - lighthouse-role
```

## Лицензия

MIT
