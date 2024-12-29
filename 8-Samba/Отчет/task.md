
# Шарим


1. Установите пакет samba
2. ЧТо такое побщая папка, зачем оно может быть нужно?
3. Создайте общую папку без пароля с правами только на чтение файлов
4. Создайте общую папку с паролем с правами на чтение и запись
5. Создайте общую папку с доступом для какой-то группы с полными правами
6. Создайте общую папку в которой у одной группы будет полный доступ, а у другой только доступ на чтение.
Третья группа не должна иметь к ней доступа


# Домашняя работа
1.
  ```
  apt-get install samba
  ```
2. **Общая папка**
  Общая папка — это сетевой ресурс, который позволяет пользователям обмениваться файлами и папками через локальную сеть или интернет. Она может быть полезна для:
    Совместной работы: Позволяет нескольким пользователям одновременно работать с одними и теми же файлами.
    Упрощения доступа: Упрощает доступ к документам и ресурсам, необходимым для работы.
    Экономии места: Позволяет хранить данные на одном сервере, вместо того чтобы дублировать их на каждом компьютере.
3. **без пароля с правами только на чтение файлов**
   Создаем папку
   ```
   mkdir -p /home/sb/smb/read_only
   ```
   Настраиваем права доступа
   ```
   chown -R nobody:nogroup /home/sb/smb/read_only
   chmod 755 /home/sb/smb/read_only
   ```
   Добавляем конфигурацию в файл /etc/samba/smb.conf
   ```
   [ReadOnly]
   path = /home/sb/smb/read_only
   browseable = yes
   read only = yes
   guest ok = yes
   ```
4. **с паролем с правами на чтение и запись**
      Создаем папку
   ```
   mkdir -p /home/sb/smb/read_write
   ```
   Настраиваем права доступа
   ```
   chown -R nobody:nogroup /home/sb/smb/read_write
   chmod 770 /home/sb/smb/read_write
   ```
   Добавляем пользователя Samba (если ещё не создан)
   ```
   sudo smbpasswd -a gleb 
   ```
   Добавляем конфигурацию в файл /etc/samba/smb.conf
   ```
   [ReadWrite]
   path = /home/sb/smb/read_write
   browseable = yes
   read only = no
   valid users = gleb 
   ```
5. **с доступом для какой-то группы с полными правами**
   Создаем папку
   ```
   mkdir -p /home/sm/smb/group_access
   ```
   Настраиваем права доступа
   ```
   chown :gleb_group /home/sb/smb/group_access
   chmod 770 /home/sb/smb/group_access
   ```
   Добавляем конфигурацию в файл /etc/samba/smb.conf
   ```
   [GroupAccess]
   path = /home/sb/smb/group_access
   browseable = yes
   read only = no
   valid users = @gleb_group
   ```
6. **в которой у одной группы будет полный доступ, а у другой только доступ на чтение.
Третья группа не должна иметь к ней доступа**
   Создаем папку
   ```
   mkdir -p /home/sb/smb/advanced_access
   ```
   Настраиваем права доступа
     Группа с полным доступом
     ```
     chown :fullaccessgroup /home/sb/smb/advanced_access
     chmod 770 /home/sb/smb/advanced_access
     ```
     Группа с доступом только на чтение
     ```
     chown :readonlygroup /home/sb/smb/advanced_access
     chmod 750 /home/sb/smb/advanced_access
     ``` 

   Добавляем конфигурацию в файл /etc/samba/smb.conf
   ```
   [AdvancedAccess]
   path = /home/sb/smb/advanced_access 
   browseable = yes 
   read only = no 
   valid users = @fullaccessgroup 
   write list = @readonlygroup 
   ```
**Перезапускаем**
  ```sudo systemctl restart smbd
  ```
