# Tech Manuals

Репозиторий содержит инструкции по настройке и эксплуатации различных серверных решений.<br>
Здесь вы найдете пошаговые руководства для установки и настройки VPN-серверов, HTTP-прокси и других полезных инструментов.

## Содержание

- [Как использовать этот репозиторий](#как-использовать-этот-репозиторий)
- [VPN-сервер на базе OpenVPN](#vpn-сервер-на-базе-openvpn)
- [HTTP-прокси сервер Squid](#http-прокси-сервер-squid)
- [SSH аутентификация на VPS сервере](#ssh-аутентификация-на-vps-сервере)

## Как использовать этот репозиторий

Этот репозиторий организован по принципу отдельных заметок для каждого типа инструмента. 
Каждая заметка находится в своей папке в директории `docs/`.

## VPN-сервер на базе OpenVPN

В этом разделе приведены инструкции по установке и настройке OpenVPN-сервера на Linux.

- Установка OpenVPN
- Генерация ключей и сертификатов
- Настройка конфигурационных файлов
- Настройка клиентских конфигураций
- Запуск сервера

[Подробнее...](docs/openvpn-setup.md)

## HTTP-прокси сервер Squid

- Установка Squid
- Настройка конфигурационных файлов
- Настройка клиентов
- Запуск сервера

[Подробнее...](docs/squid-setup.md)

## SSH аутентификация на VPS сервере

- Генерация ключа rsa
- Добавление публичного ключа на vps сервер
- Настройка клиента

[Подробнее...](docs/vps-ssh-key-auth.md)

## Мониторинг с помощью Netdata и Nginx

- Установка Netdata
- Установка Nginx
- Настройка Nginx

[Подробнее...](docs/netdata-nginx-setup.md)
