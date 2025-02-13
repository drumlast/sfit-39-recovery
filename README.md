# Домашнее задание к занятию "`Резервное копирование`"

### Задание 1

![alt text](img/1.png)

### Задание 2

![alt text](img/2.png)


```
#!/bin/bash

# Директория для резервного копирования
SOURCE=~
DESTINATION=/tmp/backup

# Создаем директорию назначения, если её нет
mkdir -p "$DESTINATION"

# Лог-файл
LOGFILE=/var/log/backup.log

# Выполняем rsync и записываем результат в лог
rsync -aHAX --checksum --exclude='.*' "$SOURCE/" "$DESTINATION/" > "$LOGFILE" 2>&1

# Проверяем успешность выполнения
if [ $? -eq 0 ]; then
  echo "$(date): Backup completed successfully." >> "$LOGFILE"
else
  echo "$(date): Backup failed." >> "$LOGFILE"
fi
```