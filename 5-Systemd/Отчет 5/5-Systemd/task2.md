# Пишем юниты

1. Создайте скрипт который создаёт папку заполняет её файлами ( имена 1-4 ) и записывает в них информацию
о текущей дате, версии ядра, имени компьютера и списе всех файлов в домашнем каталоге пользователя от которого выполняется скрипт( не забудьте сдлеать проверку на существование файлов и папок)

2. Создайте юнит который будет вызывать этот скрипт при запуске. Проверьте
3. Создайте таймер который будет вызывать выполнение одноимённого systemd юнита каждые 5 минут.
4. От какого пользователя вызыаются юниты поумолчанию?
5. Создайте пользователя от имени которого будет выполняться ваш скрипт.
6. Дополните юнит информацией о пользователе от которого должен выплняться скрипт.
7. Дополните ваш скрипт так, что бы он независимо от местоположения всега выполнялся в домашней папке того кто его вызывает.

# Домашняя работа
1. ```
    #!/bin/bash
    
    set -euo pipefail
    
    DIR="/home/sb/Desktop/folder"
    
    if [ -d "$DIR" ]; then
        echo "Существует."
    else
        mkdir $DIR
        echo "Создана."
    fi
    
    CURRENT_DATE=$(date)
    KERNEL_VERSION=$(uname -r)
    HOSTNAME=$(hostname)
    HOME_DIR="$(eval echo "~$(whoami)")"
    HOME_FILES=$(ls -R "$HOME_DIR")
    
    FILE1="$DIR/1.txt"
    if [ -f "$FILE1" ]; then
        echo "Существует."
    else
        echo "Дата: $CURRENT_DATE" > "$FILE1"
        echo "Файл '$FILE1' создан и заполнен."
    fi
    
    FILE2="$DIR/2.txt"
    if [ -f "$FILE2" ]; then
        echo "Существует."
    else
        echo "Версия ядра: $KERNEL_VERSION" > "$FILE2"
        echo "Файл '$FILE2' создан и заполнен."
    fi
    
    FILE3="$DIR/3.txt"
    if [ -f "$FILE3" ]; then
        echo "Существует."
    else
        echo "Имя компьютера: $HOSTNAME" > "$FILE3"
        echo "Файл '$FILE3' создан и заполнен."
    fi
    
    FILE4="$DIR/4.txt"
    if [ -f "$FILE4" ]; then
        echo "Существует."
    else
        {
        echo "Список файлов в домашнем каталоге:"
        echo "$HOME_FILES"
        } > "$FILE4"
        echo "Файл '$FILE4' создан и заполнен."
    fi
      ```
  Запускаем
  ![image](https://github.com/user-attachments/assets/8753354b-9c9d-4cb4-b4bb-b71b7c440ff4)
  ![image](https://github.com/user-attachments/assets/8fcb176e-df55-4102-8768-7837bdb4e88d)
  Запускаем от супер пользователя
  ![image](https://github.com/user-attachments/assets/3d7f135c-04a7-4445-8d2c-0b188d099f86)
2. 
        ```
           mv script.sh /usr/local/bin/    
           sudo chmod +x /usr/local/bin/script.sh
           touch /etc/systemd/system/create_files.service
           vim /etc/systemd/system/create_files.service
           systemctl daemon-reload
           systemctl start create_files.service
           systemctl status create_files.service
        ```
3.
       ```
           touch /etc/systemd/system/create_files.timer
    
           vim /etc/systemd/system/create_files.timer
    
           systemctl daemon-reload
    
           systemctl enable create_files.timer
    
           systemctl start create_files.timer
    
           systemctl status create_files.timer
        ```
4. root
5. ```
       useradd -m -s /bin/bash scriptuser
   ```
   ```
       sudo passwd scriptuser
   ```
6. ```
       vim /etc/systemd/system/create_files.service
   ```
   ```
       systemctl daemon-reload
   ```
   ```
       systemctl restart create_files.service
   ```
   ```
       systemctl restart create_files.timer
   ```
7. ```
       HOME_DIR=$(eval echo "~scriptuser")
   ```









