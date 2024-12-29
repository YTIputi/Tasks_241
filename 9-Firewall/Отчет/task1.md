# Открываем iptables
1. Установите iptables
2. Проверьте осталась ли возможность подключения по ssh к вашему серверу
3. Почему может пропасть такая возможность?
4. Откройте нужный порт на сервере чтобы восстановить подключение
5. Это будет udp или tcp прот?
# Сохраняем
6. Сохраняются ли записанные вами правила после перезагрузки?
7. Как их сохранить?
При работе с firewall не рекомендую отключаться от текущей сессии ssh. Лучше подключаться из другой консольки.a

# Домашняя работа
1.
  ```
  sudo apt-get install iptables
  ```
2. 
  ```
  iptables -L -v
  ssh student@95.31.204.147 -p 234
  ```
  Вроде осталось
3. 
  Блокировка порта: Если порт SSH (обычно 22) закрыт в правилах iptables, соединение не будет установлено.
  Неправильные правила: Неверные настройки iptables могут привести к блокировке всех входящих соединений.
  Изменение конфигурации сети: Изменения в сетевых интерфейсах или маршрутизации также могут повлиять на доступ.
4. 
  ```
  iptables -A INPUT -p tcp --dport 234 -j ACCEPT
  ```
5.
  Для SSH используется протокол TCP. Поэтому при открытии порта необходимо указывать именно TCP.
6.
  Правила iptables не сохраняются автоматически после перезагрузки системы.
7. 
  ```
  vim /etc/systemd/system/iptables-restore.service

  [Unit]
  Description=Restore iptables firewall rules
  After=network-pre.target
  Wants=network-pre.target
  
  [Service]
  Type=oneshot
  ExecStart=/usr/sbin/iptables-restore /etc/sysconfig/iptables
  RemainAfterExit=yes
  
  [Install]
  WantedBy=multi-user.target

  systemctl daemon-reload
  sudo systemctl enable iptables-restore.service
  sudo systemctl start iptables-restore.service
  ```
