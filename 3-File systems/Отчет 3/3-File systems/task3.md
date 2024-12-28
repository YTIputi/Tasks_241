# Продолжаем

1. Выведите содержимое fstab. Что хранится в fstab?
2. Добавьте в виртуальную машину ещё один диск
3. Узнайте как ситема видит ваш диск - выведите информацию о блочных устройствах
4. С помощью полученной информации создайте на диске таблицу разделов и фаловую систему ext4
5. Примонитруте диск в каталог /mnt
6. Зайдите в каталог и создайте там файлы
7. Отмонтируйте диск и проверье остались ли файлы
8. Сделайте так чтобы диск автоматически подключался при загрузке систем ( добавьте информацию о нём с fstab)
9. Проверьте корретность записанных в fstab данных перед перезагрузкой
10. Перезагрущите систему и убедитесь что диск был подключён к системе

# Домашняя работа
1. <img width="886" alt="Снимок экрана 2024-12-13 в 16 27 58" src="https://github.com/user-attachments/assets/f8dae3d0-06d0-4b20-b19d-01286bbb39a2" />
fstab хранит список файловых систем, которые автоматически монтируются при загрузке системы, с указанием их точек монтирования, типов файловых систем, параметров монтирования и настроек проверки.
2. <img width="792" alt="Снимок экрана 2024-12-28 в 16 45 26" src="https://github.com/user-attachments/assets/6bf5bc39-6586-4446-91ba-b05aa611a6a1" />
3. ![Uploading Снимок экрана 2024-12-28 в 16.55.24.png…]()
4. Создаем раздел <img width="646" alt="Снимок экрана 2024-12-28 в 16 58 52" src="https://github.com/user-attachments/assets/9e490661-a3c3-4f5a-b1ed-8cf43f41eaca" />
Проверяем
<img width="371" alt="Снимок экрана 2024-12-28 в 16 59 59" src="https://github.com/user-attachments/assets/487d767f-ac7d-4efc-96b7-45cb3836de28" />
Создание файловой системы
<img width="513" alt="Снимок экрана 2024-12-28 в 17 00 49" src="https://github.com/user-attachments/assets/de599da3-e81c-40f8-a69e-2dce7343fe3b" />
Проверяем
<img width="605" alt="Снимок экрана 2024-12-28 в 17 02 13" src="https://github.com/user-attachments/assets/33dcb1d0-97e7-4611-a9ec-0b6239816e5c" />
5. <img width="332" alt="Снимок экрана 2024-12-28 в 17 03 52" src="https://github.com/user-attachments/assets/a5c2304c-56b9-4b79-909a-ea0a93966ed3" />
<img width="354" alt="Снимок экрана 2024-12-28 в 17 04 19" src="https://github.com/user-attachments/assets/365f2063-d09c-43fa-8b15-c41fd07eee39" />
<img width="582" alt="Снимок экрана 2024-12-28 в 17 05 05" src="https://github.com/user-attachments/assets/50f2c44f-054c-42f7-a1d9-af6a27d66ab4" />
6. <img width="426" alt="Снимок экрана 2024-12-28 в 18 56 31" src="https://github.com/user-attachments/assets/9f02d33a-5618-4a0f-b882-df11187aa9ef" />
7. <img width="579" alt="Снимок экрана 2024-12-28 в 18 58 27" src="https://github.com/user-attachments/assets/d7df3cf5-d0e8-407f-b3f7-2b9dab125655" />
<img width="346" alt="Снимок экрана 2024-12-28 в 18 58 54" src="https://github.com/user-attachments/assets/bd95026c-c474-4cc9-be64-cee9445bd431" />
8-9. Добавляем в fstab последнюю строчку 
<img width="868" alt="Снимок экрана 2024-12-28 в 19 08 30" src="https://github.com/user-attachments/assets/ba8f2642-f937-4003-a88e-37aabb666db3" />
10. 

