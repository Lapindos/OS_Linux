# Домашняя работа 05.10. Память

## Что сделано

Просмотрено, как Linux показывает физическую память и карту адресного пространства процесса.

- `/proc/iomem` — карта физической памяти: System RAM, ядро, ACPI, устройства.
- `/proc/meminfo` — сводка: `MemTotal`, `MemFree`, `MemAvailable`, кэш, swap и huge pages.
- `pgrep bash` находит PID оболочки, `ps` показывает системные потоки.
- `/proc/<pid>/maps` — участки адресного пространства: код, куча `[heap]`, библиотеки. Рядом открывается `/proc/<pid>/mem`.

## Ход работы

Карта физической памяти.

![Фрагмент /proc/iomem](screenshots/01-proc-iomem.png)

Начало `/proc/meminfo`: общий объём, свободно, доступно, кэш.

![Начало /proc/meminfo](screenshots/02-proc-meminfo.png)

Продолжение `/proc/meminfo`: slab, committed memory, huge pages.

![Продолжение /proc/meminfo](screenshots/03-proc-meminfo-hugepages.png)

Поиск bash и список процессов.

![pgrep bash и ps](screenshots/04-pgrep-and-ps.png)

Карта памяти процесса `bash`.

![/proc/PID/maps процесса bash](screenshots/05-proc-bash-maps.png)

Карта памяти `gnome-terminal`.

![/proc/PID/maps процесса gnome-terminal](screenshots/06-proc-gnome-terminal-maps.png)
