# Домашняя работа 22.09. Пользователи, группы и права доступа

## Что сделано

Созданы пользователи и общая группа, разграничен доступ к файлам в `/shared` и проверен вход под разными учётными записями.

- `groupadd` создаёт группу `project_group`, `useradd` — пользователей `user1`, `user2` и `user3`.
- `passwd` задаёт пароли, `usermod -aG` добавляет пользователей в группу.
- В `/shared` лежат `private.txt` (`chmod 600`, читает только владелец) и `public.txt` (`chmod 666`, доступен всем).
- Под `user1` оба файла читаются. Под `user2` чтение `private.txt` даёт `Permission denied`, а в `public.txt` можно дописать строку.

## Ход работы

Создание пользователей, группы и файлов в `/shared`.

![Создание пользователей и файлов в /shared](screenshots/01-useradd-passwd-shared.png)

Права: приватный файл `600`, публичный `666`.

![Права private.txt и public.txt](screenshots/02-chmod-private-public.png)

Проверка от имени владельца `user1`.

![Чтение файлов пользователем user1](screenshots/03-su-user1-read-files.png)

Проверка от имени `user2`: к приватному файлу доступа нет.

![Отказ в доступе для user2 и запись в public.txt](screenshots/04-su-user2-permission-denied.png)
