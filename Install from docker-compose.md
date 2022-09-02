# 1. Создаем папку elastiflow4.

   Копируем из репозитория файлы docker-compose-nginx.yml и nginx.conf в папку elastiflow4.

# 2. Создаем папку для индексов
```text
 sudo mkdir /var/lib/elastiflow_es 
```
# 3. Меняем ей доступы
```text
 sudo chown -R 1000:1000 /var/lib/elastiflow_es
```
# 4. Создаем ключ и сертификат для flow.pivzavoz.loсal cроком на 10 лет.
```text
openssl req -x509 -nodes -days 3650 -newkey rsa:2048 -keyout nginx.key -out nginx.crt -subj "/CN=flow.pivzavoz.local/O=flow.pivzavoz.local" -addext "subjectAltName = DNS:flow.pivzavoz.local"
```
# 5. Созаем файл с пользователями для доступа через nginx. (В примере пользователь "it") 
```text
 sudo sh -c "echo -n 'it:' >> .htpasswd"
```
# 6. Добавляем в файл с ползователями пароль для этого пользователей
```text
 sudo sh -c "openssl passwd -apr1 >> .htpasswd"
```
# 7. После всех манипуляций в папке долнжы быть эти файлы
```
.
├── docker-compose-nginx.yml
├── nginx.conf
├── nginx.crt
└── nginx.key
```