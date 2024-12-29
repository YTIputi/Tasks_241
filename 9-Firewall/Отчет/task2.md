# Открываем firewald

1. Удалите iptables и установите firewalld
2. Попробуйте так-же проверить возможность подключения по ssh
3. Если её нет то откройте порт
4. Выведите список открытых портов с помощью firewall-cmd
5. Можно ли там добавить порты по названию сервиса?
6. На вашей Локальной виртуальной машине попробуйте подключиться к серверу samba из предыдущих заданий
7. Если не получилось то откройте нужные порты
9. Сделайте так чтобы изменения были постоянными

# Домашняя работа
1.
  ```
  apt-get remove iptables
  apt-get install firewalld
  ```
2.
  ```
  ssh student@95.31.204.147 -p 234
  ```
3. 
  ```
  firewall-cmd --zone=public --add-port=234/tcp --permanent
  firewall-cmd --reload
  ```
4.
  ```
  firewall-cmd --zone=public --list-ports
  ```
5.
  Можно
  ```
  firewall-cmd --zone=public --add-service=http --permanent
  firewall-cmd --reload
  ```
6. 
  ```
  smbclient //127.0.1.1 -U gleb
  ```
7. 
  ```
  firewall-cmd --zone=public --add-service=samba --permanent
  firewall-cmd --reload
  ```
8. Сделано
