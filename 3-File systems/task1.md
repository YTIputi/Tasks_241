# ФС

1) Какие файловые системы вы знаете?
2) Как можно классифиировать файловые системы? в чём отличия??
3) Какие файловые системы используются в linux?
4) Как можно создать файловую систему на диске?
5) Как можно подключить диск в систему, что такое монтирование?
6) файловая система procfs, cifs, tpmfs,sysfs. В чём особенности каждой из них?
Вывести каталоги к которым примонтированы эти файловые системыю
7) Как можно получить информацию о системе используя лишь команду cat? 
вывести ифонмацию о процессоре и состоянии памяти системы

# Домашняя работа

1) FAT32 — старые файловые системы, поддерживаемые Windows, применяются для флешек.
NTFS — современная файловая система Windows.
ext2, ext3, ext4 — файловые системы Linux, с ext4 как наиболее популярной.
XFS — производительная и масштабируемая система Linux.
Btrfs — поддерживает современные функции, такие как снимки и сжатие.
ZFS — мощная файловая система с высокой надёжностью, поддерживает пулы хранения.
HFS+, APFS — файловые системы macOS.
ISO 9660 — используется для оптических дисков.
CIFS/SMB — сетевая файловая система.
2) По назначению:
Локальные файловые системы: ext4, NTFS, FAT32.
Сетевые файловые системы: NFS, CIFS/SMB.
Виртуальные файловые системы: procfs, sysfs, tmpfs.
По способу хранения данных:
Журналируемые: XFS, ext3, ext4 (предотвращают повреждения данных).
Не журналируемые: ext2, FAT32 (быстрее, но менее надёжные).
По поддержке функций:
Снимки, дедупликация, шифрование (например, Btrfs, ZFS).
По совместимости с ОС:
Linux: ext4, XFS, Btrfs.
Windows: NTFS, exFAT.
Кроссплатформенные: FAT32, exFAT.
3) Локальные: ext4, XFS, Btrfs, ReiserFS.
Сетевые: NFS, CIFS/SMB.
Виртуальные: procfs, sysfs, tmpfs, devtmpfs.
4) sudo mkfs.ext4 /dev/sdX1
5) Монтирование — процесс подключения файловой системы диска в дерево каталогов ОС. sudo mount /dev/sdX1 /mnt/mydisk
6) procfs создает снимок мгновенного состояния ядра и процессов, которые он контролирует для userspace. Монтируется в /proc. sysfs – псевдофайловая система, предоставляющая интерфейс к структурам данных ядра. Обычно монтируется в /sys. tmpfs – нужна для размещения пользовательских файлов непосредственно в оперативной памяти ПК. Монтируется в /tmp. cifs - сетевой протокол для доступа к файловым системам через сеть, основанный на SMB (Server Message Block)
7) Информация о процессоре: cat /proc/cpuinfo; Информация о состоянии памяти: cat /proc/meminfo






