# Настриваем

1. Какой по умолчанию используется порт для поключения?
2. Можно ли его изменить? если да то как?
3. Какая служба отвечает за обработку запросов на подключения по ssh?
4. Какой файл конфигурации отвечает за его настройку?
5. Попробуйте подключиться по ssh к предоставленному вам серверу
6. Отредактируйте файл настроек на сервере так, чтобы была возможность подключиться к серверу используя пользователя root
7. Измените колличество ошибок ввода пароля перед сборосом соединения, покажите эти измененения
8. Создайте пользователя ssh-user и попробуйте им подключиться к серверу
9. Ограничте ему возможность подключения к серверу
10. Как вы это сделали?
11. Что хранится в файле known_hosts?

# Домашняя работа
1. По умолчанию для подключения по SSH используется порт 22.
2. Да, можно. Сначала находим файл конфига в /etc. sudo nano /etc/ssh/sshd_config. Редактируем строку где указан порт #Port 22. Теперь перезапускаем ssh сервер для применения изменений sudo systemctl restart sshd
3. Служба sshd (SSH Daemon) отвечает за обработку запросов.
4. Основной файл конфигурации SSH-сервера — /etc/ssh/sshd_config.
5. ssh student@arzdez.ru -p 2222
6. В ранее упомянутом файле sshd_config добавляем строчку PermitRootLogin yes. Также перезагружаем службу ssh.
7. Снова достаем sshd_config и докидываем в него MaxAuthTries и количество попыток через пробел. И опять перезагружаем службу ssh.
8. sudo useradd ssh-user и passwd ssh-user
9. В sshd_config, добавляем строчку DenyUsers ssh_user. И снова перезагружаем sshd.
10. Использовал директиву DenyUsers в файле конфигурации SSH, которая блокирует доступ указанным пользователям
11. Файл ~/.ssh/known_hosts содержит список известных хостов, к которым ранее подключался пользователь, и их публичные ключи. Это необходимо для проверки подлинности сервера при повторном подключении.
