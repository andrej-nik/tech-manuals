## Мониторинг системы с помощью Netdata

## Установка Netdata

1. Устанавливаем Netdata:
```bash
sudo apt update
sudo apt install -y netdata
```
2. Проверяем состояние службы:
```bash
sudo systemctl status netdata
```
Должны увидеть статус `active (running)`.

## Настройка Nginx для проксирования Netdata

1. Устанавливаем Nginx:
```bash
sudo apt update
sudo apt install nginx -y
```
2. Создаем файл `.htpasswd` для аутентификации:
```bash
sudo htpasswd -c /etc/nginx/.htpasswd <имя_пользователя>
```
Введите пароль, который будет использоваться для доступа
3. Настраиваем Nginx для проксирования запросов к Netdata.
Открываем конфигурацию Nginx:
```bash
sudo nano /etc/nginx/sites-available/default
```
4. Добавляем следующую конфигурацию:
```
server {
    listen 80;
    server_name <ваш_IP_или_домен>;

    location /netdata/ {
        proxy_pass http://127.0.0.1:19999/;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;

        # Аутентификация
        auth_basic "Protected Area";
        auth_basic_user_file /etc/nginx/.htpasswd;
    }
}
```
5. Перезапускаем nginx
```bash
sudo systemctl restart nginx
```
Теперь Netdata должен быть доступен по адресу `http://<ваш_IP_или_домен>/netdata`
