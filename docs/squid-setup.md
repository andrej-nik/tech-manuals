# HTTP Proxy Squid

1. Установим Squid:
```bash
sudo apt update
sudo apt install squid
```

2. Открываем файл конфигураций:
```bash
sudo nano /etc/squid/squid.conf
```

3. Настраиваем аутентификацию - в файл `/etc/squid/squid.conf` добавляем следующие строки:
```
auth_param basic program /usr/lib/squid/basic_ncsa_auth /etc/squid/passwd
auth_param basic children 5
auth_param basic realm Squid proxy-caching web server
auth_param basic credentialsttl 2 hours
auth_param basic casesensitive on
```
Эти строки разрешают доступ только для аутентифицированных пользователей.

4. Создание файла паролей.<br>
Создаем файл паролей, который будет использоваться для аутентификаций.<br>
Для этого воспользуемся утилитой **htpasswd** из пакета **apache2-utils**:
```bash
sudo apt install apache2-utils
```
Создаем файл паролей и первого пользователя:
```bash
sudo htpasswd -c /etc/squid/passwd username
```
Утилита запросит пароль для пользователя **username**.<br>
Чтобы добавить дополнительных пользователей, используем ту же команду, но без флага **-c**:
```bash
sudo htpasswd /etc/squid/passwd another_username
```

5. Перезапускаем Squid<br>
После всех настроек перезапускаем Squid:
```bash
sudo systemctl restart squid
```

