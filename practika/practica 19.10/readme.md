# Практика 19.10. Сеть

## Что сделано

Проверены адрес интерфейса, маршрут, доступность сети, открытые порты и DNS.

- `ip -br a` и `ip link show` показывают адрес и MAC интерфейса `enp0s3`.
- `ip route show` и `ip route get` находят шлюз `10.0.2.2` и маршрут до `1.1.1.1`.
- `ping` проверяет `8.8.8.8`, `example.com` и шлюз. До `192.168.1.1` пакеты не доходят.
- Короткая проверка по шагам печатает `Gateway: OK`, `Internet IP: OK` и `DNS: OK`.
- `traceroute -n` показывает первый переход через шлюз.
- `ss -tlpn` выводит слушающие порты, отдельно проверяется порт `22`.
- `/etc/resolv.conf` указывает на локальный резолвер `127.0.0.53`, `dig example.com` возвращает адреса имени.

## Ход работы

Адрес и состояние интерфейса.

![ip -br a и ip link show](screenshots/01-ip-address-and-link.png)

Таблица маршрутов и маршрут до внешнего адреса.

![ip route show и ip route get](screenshots/02-ip-route.png)

Доступность `8.8.8.8`.

![ping 8.8.8.8](screenshots/03-ping-8-8-8-8.png)

Проверка DNS и трёх шагов: шлюз, внешний IP, имя.

![ping example.com и проверка шлюза, IP и DNS](screenshots/04-ping-dns-and-gateway-check.png)

Шлюз локальной сети не отвечает, интернет и DNS отвечают.

![ping шлюза, 8.8.8.8 и example.com](screenshots/05-ping-gateway-internet-dns.png)

Трассировка до `8.8.8.8`.

![traceroute -n 8.8.8.8](screenshots/06-traceroute.png)

Слушающие TCP-порты.

![ss -tlpn](screenshots/07-ss-listening-ports.png)

Проверка, слушается ли порт 22.

![ss и фильтр по порту 22](screenshots/08-ss-ssh-port.png)

Локальный DNS-резолвер.

![Содержимое /etc/resolv.conf](screenshots/09-resolv-conf.png)

Ответ DNS для `example.com`.

![dig example.com](screenshots/10-dig-example-com.png)
